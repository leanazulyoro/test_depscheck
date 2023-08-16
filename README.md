Repository to reproduce an issue with dependency-check and TSX files

1. `npm install`
2. `npm run deps:check`

It will fail with `Fail! Modules in package.json not used in code: lodash` even when lodash is imported in `TestFile2.ts`

3. change the extension of `TestFile.tsx` to `TestFile.ts` and it works fine. So the issue might be in the `@fatso83/detective-tsx` package, that uses the `typescript-detective`'s `tsx` version.

As far as I can see the issue happens when using an ImportExpression (`import('...')`) that imports a tsx file. In that case the imports that are in the file that got imported by that expression are not recognised