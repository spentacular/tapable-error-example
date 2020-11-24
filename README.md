Example of `tapable` hositing error:

```
yarn run build
```

The `@types/webpack` is hoisted from `html-webpack-plugin`. This doesn't always have to be in a top-level dependency either, anything that wraps some type of webpack config in a CLI and depends on any package that hoists `@types/webpack` will face this issue. For example, in one of our projects using the [design-systems-cli](https://github.com/intuit/design-systems-cli) it's hoisted from a very nested dependency on it:

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
