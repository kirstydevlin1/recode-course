# Setting up a linter

Firstly ensure you have read [Installing ESLint](../getting-setup/installing-eslint.md).

You should do the below steps for every project **inside the project root**. Once you've done this for the first time, double check with a tutor that it's working.

*The following applies on OS X, Linux and Windows*

## JavaScript without React

Add an `.eslintrc` file to the project root with the following contents:

```json
{
  "extends": "mcr-codes"
}
```

In the Terminal:

```bash
npm install --save-dev eslint-config-mcr-codes eslint eslint-plugin-import babel-eslint eslint-plugin-babel
```

## JavaScript with React

If you are using React in your project, you should do the same as above, with the following differences:

Your `.eslintrc` file should instead look like this:

```json
{
  "extends": "mcr-codes/react"
}
```

You will also need to install the `eslint-plugin-react` peer dependency:


In the Terminal:

```bash
npm install --save-dev eslint-plugin-react
```
