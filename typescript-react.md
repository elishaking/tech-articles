## Summary

For react projects created with [create-react-app](https://create-react-app.dev/docs/getting-started/), it is very easy to migrate to [Typescript](https://www.typescriptlang.org/). This will guarantee type checking and proper linting of the codebase.

## Steps

### 1. Install necessary dependencies

```shell
yarn add typescript @types/node @types/react-dom @types/jest @types/react-router-dom @types/react-redux @types/jwt-decode
```

### 2. Change file extensions

- Change component files from `.js` or `.jsx` to `.tsx`
- Change other javascript files from `.js` to `.ts`
- Fix import statements
- Fix any other issues that may arise

Since react works with es6 syntax, switching to typescript should raise minimal to no issues

### 3. Start project

```shell
yarn start
```

Starting the project will automatically create a `tsconfig.json` file with all the necessary settings

### 4. Add Type to variables and functions

Append the **type** for each variable, parameter and **return type** for each function or method.
For example, change the following javascript function:

```javascript
function add(a, b) {
  return a + b;
}
```

to the following typescript function:

```typescript
function add(a: number, b: number): number {
  return a + b;
}
```

Both parameters have a type of `number` and the function also has a return type of `number`

### 5. Define Classes/Interfaces for Complex Data

This includes data from API's and redux state
