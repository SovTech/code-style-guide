# SovTech Code Style Guide

Based off the AirBnB javascript style guide

_A mostly reasonable approach to JavaScript_

Guides:

- [Typescript](typescript/)
- [React](react/)
- [CSS-in-JavaScript](css-in-javascript/)

### Linting setup

Install the relevant packages listed below and copy the `.eslintrc.json`, `.editorconfig` and `.prettierrc` files

#### Create React App projects

CRA comes with eslint and some relevant packages already installed

```
yarn add -D @typescript-eslint/eslint-plugin @typescript-eslint/parser eslint-config-airbnb eslint-config-prettier eslint-config-react eslint-plugin-prettier 
```

#### Other Typescript projects

```
yarn add -D eslint @typescript-eslint/eslint-plugin @typescript-eslint/parser eslint-config-airbnb eslint-config-prettier eslint-plugin-prettier 
```

Remove the references to React in the `.eslintrc.json` file
