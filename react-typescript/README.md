
# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.\
You will also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However, we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

## Additional Setup

### Prettier Setup

```bash
npm install --save-exact prettier
```

Create a `.prettierrc` file and install the Prettier extension for your editor.

### Lint-Staged Setup

```bash
npm install --save-dev lint-staged
```

### Husky Setup

```bash
npm install --save-dev husky
npm pkg set scripts.prepare="husky install"
npx husky-init
npx husky add .husky/pre-commit "npx lint-staged"
npx husky install
```

### Update `package.json` with the following

```json
"lint-staged": {
  "{src,src/**/*}.{tsx,ts,html,css}": "prettier --write",
  "{src,src/**/*}.{tsx,ts}": "eslint"
}
```

### Pre-commit Hook

In `.husky/pre-commit` file, write:

```bash
npx lint-staged
```

### ESLint Setup with TypeScript

```bash
npm install --save-dev eslint @eslint/js @types/eslint__js typescript @typescript-eslint/eslint-plugin @typescript-eslint/parser eslint-plugin-react
```

### ESLint Configuration (`eslint.config.mjs`)

```javascript
import globals from "globals";
import pluginJs from "@eslint/js";
import tseslintPlugin from "@typescript-eslint/eslint-plugin";
import tsParser from "@typescript-eslint/parser";
import pluginReact from "eslint-plugin-react";

export default [
  {
    files: ["**/*.{js,mjs,cjs,ts,jsx,tsx}"],
    languageOptions: {
      parser: tsParser,
      parserOptions: {
        ecmaVersion: 2021,
        sourceType: "module",
        ecmaFeatures: {
          jsx: true,
          tsx: true,
        },
      },
      globals: {
        ...globals.browser,
      },
    },
    plugins: {
      "@typescript-eslint": tseslintPlugin,
      react: pluginReact,
    },
    rules: {
      // JavaScript rules
      "eqeqeq": "off",
      "no-unused-vars": "error",
      "max-len": ["warn", { code: 200 }],
      "prefer-const": ["error", { ignoreReadBeforeAssign: true }],
      "no-use-before-define": "off",

      // TypeScript rules
      "@typescript-eslint/no-use-before-define": ["error"],

      // React-specific rules
      "react/jsx-filename-extension": ["warn", { extensions: [".tsx"] }],
      "react/react-in-jsx-scope": "off",
    },
  },
];
```

### Prettier Configuration (`.prettierrc`)

```json
{
  "printWidth": 80,
  "tabWidth": 2,
  "singleQuote": true,
  "semi": true,
  "trailingComma": "all",
  "bracketSpacing": true,
  "jsxBracketSameLine": false,
  "arrowParens": "always",
  "endOfLine": "lf",
  "htmlWhitespaceSensitivity": "css",
  "quoteProps": "as-needed",
  "insertPragma": false,
  "requirePragma": false,
  "useTabs": false
}
```

### Reference Video (prettier-eslint-husky-setup)

You can watch a reference video [here](https://youtu.be/tmTajqVgkwI?si=MayOkpsB6ckyNtla).
