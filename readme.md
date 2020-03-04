# lerna-nohoist-issue

## The issue

Lerna removes dependencies listed as devDependencies in the root package.json
if they are also specified in `nohoist`.

## To reproduce

1. Clone the repo

```
git clone https://github.com/tomyam1/lerna-nohoist-issue.git
```

2. Install lerna locally (and other root dependecies)

```
npm install
```

The `@sindresorhus/tsconfig` will be under root `node_modules`

3. Bootstrap

```
npx lerna bootstrap --hoist
```

The `@sindresorhus/tsconfig` package will be removed from `node_modules`

It should not have been removed because it's a root dependency.

If we remove the `escape-string-regexp` dependency from package-a and package-b
this doesn't happen.