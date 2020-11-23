Example of `tapable` hositing error when building. We're leveraging the [design-systems-cli](https://github.com/intuit/design-systems-cli), but the errors would happen in any similar scenarios due to hoisting. To see the error:

```
yarn run build
```

The `@types/webpack` is hoisted all the way from `html-webpack-plugin` which is leveraged by playroom (but tons of packages depend on `html-webpack-plugin`).

```
❯ yarn why @types/webpack
yarn why v1.22.5
[1/4] 🤔  Why do we have the module "@types/webpack"...?
[2/4] 🚚  Initialising dependency graph...
[3/4] 🔍  Finding dependency...
[4/4] 🚡  Calculating file sizes...
=> Found "@types/webpack@4.41.25"
info Reasons this module exists
   - "@design-systems#cli#@design-systems#core#@design-systems#playroom#playroom#html-webpack-plugin" depends on it
   - Hoisted from "@design-systems#cli#@design-systems#core#@design-systems#playroom#playroom#html-webpack-plugin#@types#webpack"
```
