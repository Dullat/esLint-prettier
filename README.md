# Setting up Prettier and ESLint

## Prettier

### Installation

To integrate Prettier into your project, use the following command:

```
npm install --save-dev --save-exact prettier
```

### Usage

Format your files using Prettier with:

```
npx prettier --write index.html
```

### Automate

Change the formatter in VS Code to Prettier and enable format on save.

## ESLint

### Installation

Install ESLint extension and the package via npm:

```
npm install eslint --save-dev
```

### Configuration

Create ESLint config:

```
npm init @eslint/config
```

Automate preferences by changing `Preferences: Open Workspace Settings (JSON)`:

```json
{
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "eslint.validate": ["javascript"]
}
```

Refer to the [ESLint guide](https://eslint.org/docs/latest/use/getting-started) for detailed instructions.

## Prettier with ESLint

### Installation

Integrate Prettier with ESLint:

```
npm install --save-dev eslint-config-prettier eslint-plugin-prettier
```

Extend your ESLint configuration:

```json
{
  "extends": ["some-other-config-you-use", "prettier"]
}
```

For more detailed instructions, check the [Prettier ESLint configuration guide](https://github.com/prettier/eslint-config-prettier?tab=readme-ov-file#cli-helper-tool).

### Configuration

To configure ESLint to use single quotes and integrate it with Prettier, follow these steps:

1. **Configure Prettier:**

   Create a `.prettierrc` file in your project's root directory if you don't already have one. Inside the `.prettierrc` file, specify the `"singleQuote"` option set to `true` to enforce single quotes:

   ```json
   {
     "singleQuote": true
   }
   ```

2. **Integrate Prettier with ESLint:**

   Modify your `.eslintrc.json` file to extend the Prettier configuration and turn off ESLint rules that conflict with Prettier:

   ```json
   {
     "env": {
       "browser": true,
       "commonjs": true,
       "es2021": true
     },
     "extends": ["airbnb-base", "prettier"],
     "plugins": ["prettier"], //using (eslint-plugin-prettier)
     "parserOptions": {
       "ecmaVersion": "latest"
     },
     "rules": {}
   }
   ```

This configuration extends ESLint's recommended rules and integrates Prettier via the `eslint-plugin-prettier` plugin. It also turns off ESLint rules that conflict with Prettier's formatting.

Now you can format your files using ESLint with Prettier by running:

```
npx eslint --fix .
```

This command will lint and fix any issues in your project's JavaScript, HTML, and CSS files according to the configured rules.
