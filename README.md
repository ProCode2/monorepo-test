# Working with a monorepo

# Installing tools

```bash
yarn global add lerna
```

## Initialise lerna

```bash
lerna init
```

## Re-Generate Package.json to get the full one

```bash
npm init
```

## Add this to your `lerna.json`

```json
{
  "npmClient": "yarn",
  "useWorkspaces": true,
  "version": "independent",
  "packages": ["packages/*"]
}
```

## Add Workspaces to yarn

Include this in your root `package.json`

```json
{
  // .....

  "workspaces": ["packages/*"]

  // ...
}
```

## add different packages in the packages directory

to create a package from scratch

```bash
lerna cretae <package_name>
```

## Install dependencies across all packages

```bash
lerna add <package_name>  # uses yarn under the hood
```

## Install dependencies for a single package

```bash
lerna add <package_name> --scope=<one_of_your_package>
```

## Interdependency of the packages

Tell lerna, one of the packages(`package A`) that you created is a dependency for another package(`package B`) inside the packages directory

```bash

lerna add `Package A` --scope`Package B`
```

After this you should be able to import `package A` inside `package B` like this:

```javascript
const packageA = require("packageA");
```

## Add dependencies to the root project

```bash
yarn add -W <package_name>
```
