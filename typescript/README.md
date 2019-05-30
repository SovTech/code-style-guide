# SovTech Typescript Style Guide



## Table of Contents

  1. [Types](#types)
  1. [TS Ignore comments](#ignore-comments)


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

Prefer Product[] over Array<Product>

## Ignore comments

// @ts-ignore comments must always have the reason why they were added in the code

  ```typescript
  // bad
  // @ts-ignore
   handleChange={this.handleChange}
   
  // good
  // @ts-ignore - ignored because custom input isn't typed
   handleChange={this.handleChange}
  ```

**[⬆ back to top](#table-of-contents)**
