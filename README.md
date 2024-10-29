# B4CKSP4CE Code Style Guide

[![MPL-2.0 License](https://img.shields.io/github/license/b4ck5p4c3/style-guide?style=for-the-badge)](https://www.mozilla.org/en-US/MPL/2.0/)
[![NPM Version](https://img.shields.io/npm/v/%40bksp%2Fstyle-guide?style=for-the-badge)](https://npmjs.com/package/@bksp/style-guide)
[![neostandard javascript style](https://img.shields.io/badge/code_style-neostandard-7fffff?style=for-the-badge&labelColor=ff80ff)](https://github.com/neostandard/neostandard)

## Introduction

This repository is the home of B4CKSP4CE's style guide, which includes configs for
popular linting and styling tools.

The following configs are available, and are designed to be used together.

- [ESLint](#eslint)
- [TypeScript](#typescript)
- [Commitlint](#commitlint)

Install the package using your package manager of choice:

```sh
# Using pnpm
pnpm install --save-dev @bksp/style-guide
```

## ESLint

> Note: ESLint is a peer-dependency of this package, and should be installed
> at the root of your project.

```sh
# Install ESLint and TypeScript ESLint parser required for the shared config
pnpm install --save-dev eslint typescript-eslint
```

There are two ESLint configurations available:

- `@bksp/style-guide/eslint/node` - for generic Node.js projects
- `@bksp/style-guide/eslint/next` - for Next.js projects

Re-export the desired configuration in your project's `eslint.config.mjs` file:

```js
// eslint.config.mjs
import next from '@bksp/style-guide/eslint/next'
export default next;
```

You can extend this configuration to add project-specific rules.
Read more about it in [Configuring ESLint](https://eslint.org/docs/latest/use/configure/) documentation.

## TypeScript

This style guide includes a TypeScript configuration snippet, providing basic constraints for TypeScript projects.
Notice that it isn't a full `tsconfig.json` file, but rather a set of rules to be extended in your project's `tsconfig.json`.

For now, this configuration is matching the [`@tsconfig/strictest`](https://www.npmjs.com/package/@tsconfig/strictest) package.
However, we might adjust it in the future to better fit our needs.

To use the shared TypeScript config, you need to extend it in your `tsconfig.json` file:

```json
{
  "extends": "@bksp/style-guide/typescript"
}
```

## Commitlint

Commitlint is a linting tool for commit messages.
We use it to enforce a consistent use of [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) specification.

In order to use the shared Commitlint config, you need to install the following packages:

```sh
# Install commitlint and husky for git hooks
pnpm install --save-dev @commitlint/cli husky

# Link the shared config
echo "export default { extends: ['@bksp/style-guide/commitlint'] }" > .commitlintrc.mjs

# Initialize husky
pnpm husky init

# Add a commit-msg hook
echo "pnpm dlx commitlint --edit \$1" > .husky/commit-msg
```

## Credits

This project is heavily inspired by [The Vercel Style Guide](https://github.com/vercel/style-guide).
Thanks, Vercel, for sharing this amazing piece of work!