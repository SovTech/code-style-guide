# SovTech CSS-in-JavaScript Style Guide

This guide **is not** based off the AirBnB CSS-in-JS style guide. 

SovTech's approach to CSS-in-JS uses [Styled Components](https://styled-components.com) and [Styled System](https://styled-system.com)

## Table of Contents

1. [Naming](#naming)
1. [Style Location](#style-location)
1. [Nesting](#nesting)
1. [Inline](#inline)
1. [Themes](#themes)

## Naming

- Use [breakpoints from Styled System](https://styled-system.com/theme-specification/#breakpoints)

These should be added to the theme

```typescript
breakpoints: ['40em', '52em', '64em'];
```

## Style Location

- Define styles in their own `styles.ts` file.
- If the components are going to be reused they should be in their own `Component/xxx` folder. If styles are only going to be used in one component they should live in that component's `styles.ts` file.

## Nesting

- Leave a blank line between adjacent blocks at the same indentation level.

  > Why? The whitespace improves readability and reduces the likelihood of merge conflicts.

  ```typescript
  // bad
  {
    bigBang: {
      display: 'inline-block',
      '::before': {
        content: "''"
      }
    },
    universe: {
      border: 'none'
    }
  }

  // good
  {
    bigBang: {
      display: 'inline-block',

      '::before': {
        content: "''"
      }
    },

    universe: {
      border: 'none'
    }
  }
  ```

## Inline

- Use inline styles with caution
- Passing props to a component using Styled System is preferred

## Themes

- Always use the Styled Components ThemeProvider along with Styled System

> Why? It is useful to have a set of shared variables for styling your components. Using an abstraction layer makes this more convenient. Additionally, this can help prevent your components from being tightly coupled to any particular underlying implementation, which gives you more freedom.

- Define colors only in themes.

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

- Define fonts only in themes.

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

- Define fonts as sets of related styles.

  ```typescript
  // bad
  export default withStyles(() => ({
    towerOfPisa: {
      fontFamily: 'Italiana, "Times New Roman", serif',
      fontSize: '2em',
      fontStyle: 'italic',
      lineHeight: 1.5
    }
  }))(MyComponent);

  // good
  export default withStyles(({ font }) => ({
    towerOfPisa: {
      ...font.italian
    }
  }))(MyComponent);
  ```

- Only use [media queries defined in the theme](https://styled-system.com/theme-specification/#media-queries) - these should be based off the breakpoints
