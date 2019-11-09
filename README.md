# eslint-config-benjie

Benjie's ESLint config, by Benjie, for Benjie. Highly opinionated. Opinions
you might not agree with. Opinions that may be focussed more on Benjie's
productivity than on "best practices" or guidance.

Install with:

```bash
yarn add --dev eslint-config-benjie
npx install-peerdeps --dev eslint-config-benjie
```

Use it with GraphQL with an `.eslintrc.js` like this:

```js
const { readFileSync } = require("fs");
const schemaString = readFileSync("./data/schema.graphql", "utf8");

module.exports = {
  extends: ["benjie"],

  rules: {
    "graphql/template-strings": [
      "error",
      {
        env: "literal",
        schemaString
      }
    ],
    "graphql/named-operations": [
      "error",
      {
        schemaString
      }
    ],
    "graphql/required-fields": [
      "error",
      {
        env: "literal",
        schemaString,
        requiredFields: ["nodeId", "id"]
      }
    ]
  }
};
```

- Assumes you use TypeScript, GraphQL, React, and Jest
- Assumes you're comfortable with ES2018+ syntax and bitwise operations
- Assumes you're writing your code in modules (`import` / `export`)
- Uses `prettier` for formatting within ESLint
- Targets browser _and_ Node
- Uses \_underscorePrefixes for placeholder arguments
- Allows `return (a = 3)` but not `return a = 3`
- Disables `no-debugger` because autofix removes it
- Assumes you might be dealing with data from other sources, so `camelcase` is not enforced (but you should still use camelcase almost everywhere!)
- No `react/prop-types` - use TypeScript instead!
- Allows nested ternaries, because Prettier rocks
