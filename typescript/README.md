# SovTech Typescript Style Guide



## Table of Contents

  1. [Types](#types)


## Types

  <a name="types--primitives"></a><a name="1.1"></a>
  - [1.1](#types--primitives) **Primitives**: When you access a primitive type you work directly on its value.

    - `string`
    - `number`
    - `boolean`
    - `null`
    - `undefined`
    - `symbol`

    ```typescript
    const foo = 1;
    let bar = foo;

    bar = 9;

    console.log(foo, bar); // => 1, 9
    ```

**[⬆ back to top](#table-of-contents)**


Types and Interfaces should be defined first

Types from packages should be used where applicable
