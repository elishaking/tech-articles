## Summary

For react projects created with [create-react-app](https://create-react-app.dev/docs/getting-started/), it is very easy to migrate to [Typescript](https://www.typescriptlang.org/). This will guarantee type checking and proper linting of the codebase.

## Steps

### 1. Install necessary dependencies

```shell
# yarn
yarn add -D typescript @types/node @types/react-dom @types/jest @types/react-router-dom

# npm
npm install --save-dev typescript @types/node @types/react-dom @types/jest @types/react-router-dom
```

**Note:** most react/npm packages will require an `@types/<package-name>` dependency to work with typescript. So add them accordingly

### 2. Change file extensions

- Change component files from `.js` or `.jsx` to `.tsx`
- Change other javascript files from `.js` to `.ts`
- Fix import statements
- Fix any other issues that may arise

Since react works with es6 syntax, switching to typescript should raise minimal to no issues

### 3. Start project

```shell
# yarn
yarn start

# npm
npm start
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

Both parameters in the function have a type of `number` and the function also has a return type of `number`

### 5. Define Classes/Interfaces for Complex Data

This includes data from API's and redux state

Thanks 👍 for making it to the end 👨‍💻 and I really hope you found the content useful.

Leave a comment below or tweet me @ElishaChibueze if you have any questions or suggestions
