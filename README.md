# TypeScript with ESLint and Prettier

## Install ESLint for TypeScript

```
npm i -D eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin
```

-   **`esling:`** ESLint core library
-   **`@typescript-eslint/parser`:** A parser that allows ESLint to understand TypeScript code
-   **`@typescript-eslint/eslint-plugin`:** Plugin with a set of recommended TypeScript rules

## Useful ESLint Commands

-   **Create an ESLint config file `.eslintrc.json`:**
    ```
    npx eslint --init
    ```
-   **Create a Node script for ESLint:**
    ```
    {
        // ...
        "scripts": {
            "lint": "eslint --ignore-path .eslintignore --ext .js,.ts src/"
        },
        // ...
    }
    ```
-   **Run ESLint through Node:**
    ```
    npm run lint -- --fix
    ```

## Install Prettier

```
npm i -D prettier
```

-   **Add a `"prettier"` key to your package.json file:**
    ```
    {
        // ...
        "prettier": {
            "tabWidth": 4
        },
        // ...
    }
    ```

## Useful Prettier Commands

-   **Run Prettier and overwrite the file with formatting:**

    ```
    npx prettier --write src/index.ts
    ```

-   **Create a Node script for Prettier:**
    ```
    {
        // ...
        "scripts": {
            "format": "prettier --ignore-path .gitignore --write \"**/*.+(js|ts|json)\""
        },
        // ...
    }
    ```
-   **Run Prettier through Node:**
    ```
    npm run format
    ```

## Avoiding conflicts when working with ESLint and Prettier

The best solution here is to use a plugin `eslint-config-prettier` to disable all ESLint rules
that are irrelevant to code formatting, as Prettier is already good at it:

```
npm i -D eslint-config-prettier
```

With that installed, let’s go to the `.eslintrc.json` file and add `prettier` at the end of your
extends list to disable any other previous rules from other plugins:

```
{
    // ...
    "extends": ["eslint:recommended", "plugin:@typescript-eslint/recommended", "prettier"],
    // ...
}
```
