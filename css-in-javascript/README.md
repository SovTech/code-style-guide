# SovTech CSS-in-JavaScript Style Guide

This guide **is not** based off the AirBnB CSS-in-JS style guide.

SovTech's approach to CSS-in-JS uses [Styled Components](https://styled-components.com) and [Styled System](https://styled-system.com)

## Table of Contents

1. [Why CSS-in-JS](#why-css-in-js)
1. [Why Styled Components](#why-styled-components)
1. [Why Styled System](#why-styled-system)
1. [Theme](#theme)
1. [Naming](#component-naming)
1. [Style Location](#style-location)
1. [Spacing](#spacing)
1. [Inline](#inline)

## Why CSS-in-JS?

Because CSS-in-JS is awesome :raised_hands:

## Why Styled Components?

There are a lof of CSS-in-JS frameworks out there. Styled Components are as close to industry standard as you are gonna get in this category.

The component structure works well with React paradigms, it has nice theming and it's performance is acceptable.

## Why Styled System?

There are some aspects of using Styled Components that get a bit tedious. Styled System helps solve this problem and increases developer velocity.

## Theme

- Theme should be located in it's own package.

> Why? This means a single theme can be shared across multiple clients. Even if there is only a single client this pattern will allow for greater extensibility in future if required.

- Always use the Styled Components ThemeProvider along with Styled System

> Why? It is useful to have a set of shared variables for styling your components. Using an abstraction layer makes this more convenient. Additionally, this can help prevent your components from being tightly coupled to any particular underlying implementation, which gives you more freedom.

```typescript
const theme: Theme = {
  fontSizes: ['0.618em', '1rem', '1.618em', '2.618em', '4.236em'], // Golden ratio
  space: [0, 5, 10, 15, 30, 60, 120],
  fontFamily: 'Helvetica Neue, sans-serif',
  colors: {
    accent: '#5AC1F2',
    htmlBackground: '5AC1F2',
    primary: '#5AC1F2',
    secondary: '#5AC1F2',
    textColor: '#5AC1F2',
    textColorInverse: '#CACACA',
    transparent: '#00000000',
    transparentBlack: '#00000004',
    transparentWhite: '#FFFFFF04'
  },
  baseRadius: '5px',
  baseBoxShadow: 'box-shadow: 0 4px 6px rgba(50,50,93,.11), 0 1px 3px rgba(0,0,0,.08)',
  baseTransition: 'all 0.2s cubic-bezier(0.25, 0.46, 0.45, 0.94)'
};
```

- Colour names **should not be abstract**.

> Color names should be practical and based on where and how they will be used in the application.

```typescript
// bad
colors: {
  blood: '#FFF',
  fire: '#FFF',
  treeSap: '#FFF'
};

// good
colors: {
  text: '#FFF',
  cardBackground: '#FFF',
  header: '#FFF'
};
```

- Only use colors from the theme. It is very unlikely that you will use a colour in a single place.

```typescript
// bad
export const StyledButton = styled.button<ButtonProps>`
  color: '#00EE77';
`;

// good
export const StyledButton = styled.button<ButtonProps>`
  color: ${({ theme }: { theme: Theme }) => theme.colors.primary};
`;
```

- Only use fonts from the theme.

```typescript
// bad
export const StyledButton = styled.button<ButtonProps>`
  font: arial;
`;

// good
export const StyledButton = styled.button<ButtonProps>`
  color: ${({ theme }: { theme: Theme }) => theme.fontFamily};
`;
```

- Use [breakpoints from Styled System](https://styled-system.com/theme-specification/#breakpoints)

- Only use [media queries defined in the theme](https://styled-system.com/theme-specification/#media-queries) - these should be based off the breakpoints

```typescript
breakpoints: ['40em', '52em', '64em'];
```

## Component Naming

- Styled Component names should start with "Styled" eg: StyledButton

## Style Location

- Define Styled Components related to a component in a `styles.ts` file.

> If the components are going to be reused they should have their own `Component/xxx` folder.
> If styles are only going to be used in one component they should live in that component's `styles.ts` file.

## Spacing

- Leave a blank line between adjacent blocks at the same indentation level.

> Why? The whitespace improves readability and reduces the likelihood of merge conflicts.

```typescript
// bad
export const StyledButton = styled.button<ButtonProps>`
  display: 'inline-block',
    '::before': {
    content: "''";
  }
`;

// good
export const StyledButton = styled.button<ButtonProps>`
  display: 'inline-block',
  
    '::before': {
    content: "''";
  }
`;
```

## Inline

- Use inline styles with caution
- Passing props to a component using Styled System is preferred

> Why? Inline styles can lead to many variations of the same component. Other than margins for aligning components you shouldn't have one-off variations of the same component. If you are going to use the variation more than once it would be better to extend the component and use that to prevent unwanted variations/changes.
