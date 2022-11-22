# Issue Repro: Astro with Vercel API Routes

[![Open in StackBlitz](https://developer.stackblitz.com/img/open_in_stackblitz.svg)](https://stackblitz.com/github/joe-bell/issue-repro-astro-vercel)
[![Open with CodeSandbox](https://assets.codesandbox.io/github/button-edit-lime.svg)](https://codesandbox.io/s/github/joe-bell/issue-repro-astro-vercel)

## Commands

This repo supports `nvm`.

All commands are run from the root of the project, from a terminal:

| Command             | Action                                       |
| :------------------ | :------------------------------------------- |
| `pnpm install`      | Installs dependencies                        |
| `pnpm vercel dev`   | Starts local dev server at `localhost:3000`  |
| `pnpm vercel build` | Build your production site to `./dist/`      |
| `pnpm preview`      | Preview your build locally, before deploying |

## Issues

There are a few things to highlight:

1. These issues only occur locally, not on Vercel.
1. `vercel`'s TypeScript version is hard-coded and doesn't support my project's newer version.
1. `@vercel/og` fails for non-`.tsx` files (and can't seem to find built-in assets)

When running `pnpm vercel dev` the following error is displayed:

```sh
> @example/minimal@0.0.1 dev /Users/joe/www/issue-repro-astro-vercel
> astro dev "--port" "3000"

  🚀  astro  v1.6.10 started in 22ms

  ┃ Local    http://127.0.0.1:3000/
  ┃ Network  use --host to expose

> Ready! Available at http://localhost:3000
Failed to instantiate edge runtime.
Invalid URL: ../vendor/noto-sans-v27-latin-regular.ttf
Error: Failed to complete request to /api/og: Error: socket hang up
node_modules/.pnpm/astro@1.6.10_@types+node@18.11.9/node_modules/astro/tsconfigs/strictest.json:18:5 - error TS5023: Unknown compiler option 'exactOptionalPropertyTypes'.

18     "exactOptionalPropertyTypes": true,
       ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Found 1 error.
```
