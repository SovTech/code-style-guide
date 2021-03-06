# SovTech Code Style Guide

Based off the AirBnB javascript style guide: _A mostly reasonable approach to JavaScript_

## How to use this?

1. Read through the [Guides](#style-guides) and familiarise yourself with the content there.

2. Perform the [Setups](#linter-and-formatter-setup) steps on your project

## Style Guides

### [Javascript](javascript/)

### [Typescript](typescript/)

### [React](react/)

### [CSS-in-JavaScript](css-in-javascript/)

### [Commit messages](commit-messages/)

### [PR Descriptions](pr-descriptions/)

### [Tests](tests/)

## Linter and formatter setup

Install the relevant packages listed below and copy the `.eslintrc.json`, `.editorconfig` and `.prettierrc` files to your project root.

If you have a mono-repo setup you will need to copy these files to the package roots as well.

### Create React App projects

CRA comes with eslint and some relevant packages already installed

```
yarn add -D @typescript-eslint/eslint-plugin @typescript-eslint/parser eslint-config-airbnb eslint-config-prettier eslint-config-react eslint-plugin-prettier
```

### Other Typescript projects

```
yarn add -D eslint @typescript-eslint/eslint-plugin @typescript-eslint/parser eslint-config-airbnb eslint-config-prettier eslint-plugin-prettier
```

Remove the references to React in the `.eslintrc.json` file

## Something wrong?

Please send feedback via slack!

## Further reading

[Google JS Style Guide](https://google.github.io/styleguide/jsguide.html)

[Idomatic JS](https://github.com/rwaldron/idiomatic.js)

[React Typescript Cheatsheet](https://github.com/typescript-cheatsheets/react-typescript-cheatsheet)
