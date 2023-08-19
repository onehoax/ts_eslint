# TypeScript with ESLint (Flat Config) and Prettier

## This repo follows the following articles:

-   [Linting in TypeScript using ESLint and Prettier](https://blog.logrocket.com/linting-typescript-eslint-prettier/)
-   [Introduction to Flat Config](https://eslint.org/blog/2022/08/new-config-system-part-2/)
-   [Migration to Flat Config](https://eslint.org/docs/latest/use/configure/migration-guide)

## ESLint

### Install ESLint for TypeScript

```
npm i -D eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin
```

-   **`esling:`** ESLint core library
-   **`@typescript-eslint/parser`:** A parser that allows ESLint to understand TypeScript code
-   **`@typescript-eslint/eslint-plugin`:** Plugin with a set of recommended TypeScript rules

### Install ESLint predefined configs

In flat config files, predefined configs are imported from separate modules
into flat config files. The recommended and all rules configs are located
in the `@eslint/js` package. You must import this package to use these
configs:

```
npm i -D @eslint/js
```

### Using eslintrc Configs in Flat Config

You may find that there’s a shareable config you rely on that hasn’t yet
been updated to flat config format. In that case, you can use the
`FlatCompat` utility to translate the eslintrc format into flat config
format. Install the `@eslint/eslintrc` package:

```
npm i -D @eslint/eslintrc
```

### Configuration

`npx eslint --init` or `npm init @eslint/config` don't work for flat config
yet, therefore you will have to manually create the config file. To use
flat config with ESLint v8, place a `eslint.config.js` file in the.
root of your project.

-   Follow [this article](https://eslint.org/blog/2022/08/new-config-system-part-2/) for an intro to the new flat config
-   Follow [this article](https://eslint.org/docs/latest/use/configure/migration-guide) for an guide on how to migrate to the new flat config

## Prettier

### Install Prettier

```
npm i -D prettier
```

## Avoiding conflicts when working with ESLint and Prettier

The best solution here is to use a plugin `eslint-config-prettier` to
disable all ESLint rules that are irrelevant to code formatting, as
Prettier is already good at it:

```
npm i -D eslint-config-prettier
```

With that installed, and add `prettier` at the end of your extends list on your
`eslint.config.js` file to disable any other previous rules from other plugins.

## My config files showcasing the above

-   [eslint.config.js](./eslint.config.js)
-   [package.json](./package.json)
