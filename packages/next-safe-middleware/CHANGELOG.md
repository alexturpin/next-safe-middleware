# @next-safe/middleware

## 0.8.0

### Minor Changes

- [#38](https://github.com/nibtime/next-safe-middleware/pull/38) [`be1c950`](https://github.com/nibtime/next-safe-middleware/commit/be1c950e438ac52c463bbb3d70ab15d4014c1827) Thanks [@nibtime](https://github.com/nibtime)! - Internal redesign for Next.js 12.2 (`req.page` deprecated) ([#37](https://github.com/nibtime/next-safe-middleware/issues/37))

* [#38](https://github.com/nibtime/next-safe-middleware/pull/38) [`be1c950`](https://github.com/nibtime/next-safe-middleware/commit/be1c950e438ac52c463bbb3d70ab15d4014c1827) Thanks [@nibtime](https://github.com/nibtime)! - provide new middleware abstractions for Next.js 12.2 stable middleware

  - `matchChain` function that allows to disable chain execution for certain requests with a matcher (predicate on `NextRequest`)
  - `continued` function that allows to continue a middleware response to a middleware chain
  - `isPageRequest` matcher that matches only requests to Next.js pages

### Patch Changes

- [#38](https://github.com/nibtime/next-safe-middleware/pull/38) [`be1c950`](https://github.com/nibtime/next-safe-middleware/commit/be1c950e438ac52c463bbb3d70ab15d4014c1827) Thanks [@nibtime](https://github.com/nibtime)! - fix: `enhanceAppWithNonce` as separate function.Must spread `nonce` into `pageProps`, else fails with Next 12.2

* [#38](https://github.com/nibtime/next-safe-middleware/pull/38) [`be1c950`](https://github.com/nibtime/next-safe-middleware/commit/be1c950e438ac52c463bbb3d70ab15d4014c1827) Thanks [@nibtime](https://github.com/nibtime)! - fix: guard critical section with lockfile when writing out hashes for CSP to file at build time

## 0.7.0

### Minor Changes

- [#36](https://github.com/nibtime/next-safe-middleware/pull/36) [`2c8c5cd`](https://github.com/nibtime/next-safe-middleware/commit/2c8c5cd6f7b6b744b4bc6af35371a38a8eccef5a) Thanks [@nibtime](https://github.com/nibtime)! - new `csp` middleware with extensive Typing for IntelliSense CSP configuration

  - typing has been borrowed from the [SvelteKit CSP Integration](https://kit.svelte.dev/docs/configuration#csp), which is excellent
  - handles annoying single quotes in the background, no need to think about them in code

* [#36](https://github.com/nibtime/next-safe-middleware/pull/36) [`2c8c5cd`](https://github.com/nibtime/next-safe-middleware/commit/2c8c5cd6f7b6b744b4bc6af35371a38a8eccef5a) Thanks [@nibtime](https://github.com/nibtime)! - versatile `getCspInitialProps` for `_document.js`

  - flag to opt into styles trustification for CSP
  - flag to opt out from script trustification for CSP
  - option to pass external raw css text to hash for CSP. For instance needed for [Mantine](https://mantine.dev/), to pass `extractCritical(initialProps.html).css` (emotion)
  - option to enhance `<App>` (`_app.js`) with nonce from SSR (needed for React Providers that can consume a nonce)

- [#36](https://github.com/nibtime/next-safe-middleware/pull/36) [`2c8c5cd`](https://github.com/nibtime/next-safe-middleware/commit/2c8c5cd6f7b6b744b4bc6af35371a38a8eccef5a) Thanks [@nibtime](https://github.com/nibtime)! - helper to set up [CSP violation reprting to Sentry](https://docs.sentry.io/product/security-policy-reporting/) with a one-liner

### Patch Changes

- [#36](https://github.com/nibtime/next-safe-middleware/pull/36) [`2c8c5cd`](https://github.com/nibtime/next-safe-middleware/commit/2c8c5cd6f7b6b744b4bc6af35371a38a8eccef5a) Thanks [@nibtime](https://github.com/nibtime)! - use base64 encoding for nonce instead of Hex

* [#32](https://github.com/nibtime/next-safe-middleware/pull/32) [`c9d42e5`](https://github.com/nibtime/next-safe-middleware/commit/c9d42e5e9da2caaadb464cde6aba21e2ec0c50d8) Thanks [@boennemann](https://github.com/boennemann)! - fix: use open-ended peerDependency ranges

## 0.6.0

### Minor Changes

- [#24](https://github.com/nibtime/next-safe-middleware/pull/24) [`af9b7ad`](https://github.com/nibtime/next-safe-middleware/commit/af9b7ad621f4ddbcfe584abbc1d66df99258ad8c) Thanks [@nibtime](https://github.com/nibtime)! - support exhaustive inline style hashing and noncing in `document` and `strictInlineStyles` middleware

### Patch Changes

- [#26](https://github.com/nibtime/next-safe-middleware/pull/26) [`8340307`](https://github.com/nibtime/next-safe-middleware/commit/83403072598b8d4fc02d268a238339830534dae3) Thanks [@nibtime](https://github.com/nibtime)! - update `getPreNextScripts` for the new `<Script strategy="worker>"` with [partytown](https://partytown.builder.io/#web-workers) introduced in [Next 12.1.1](https://github.com/vercel/next.js/releases/tag/v12.1.1).

  - follow https://nextjs.org/docs/basic-features/script#off-loading-scripts-to-a-web-worker-experimental to set it up.

## 0.5.2

### Patch Changes

- [#20](https://github.com/nibtime/next-safe-middleware/pull/20) [`0e5fe59`](https://github.com/nibtime/next-safe-middleware/commit/0e5fe590612624fa4727817f2fd3b77b4d07a87e) Thanks [@nibtime](https://github.com/nibtime)! - add hash of empty string to style hashes. CSS-in-js frameworks like stitches seem to need it to not break during hydration

## 0.5.1

### Patch Changes

- [#18](https://github.com/nibtime/next-safe-middleware/pull/18) [`b40cc05`](https://github.com/nibtime/next-safe-middleware/commit/b40cc0550ae8d67a97795c992155791628dd15be) Thanks [@nibtime](https://github.com/nibtime)! - use correct call order in `render()` of custom `Document` components. That should prevent things from breaking in ISR mode.

* [#18](https://github.com/nibtime/next-safe-middleware/pull/18) [`b40cc05`](https://github.com/nibtime/next-safe-middleware/commit/b40cc0550ae8d67a97795c992155791628dd15be) Thanks [@nibtime](https://github.com/nibtime)! - fetch script/style hashes for `/404` route if a request has no route/page. This makes strict CSP work with a custom `pages/404.js`.

## 0.5.0

### Minor Changes

- [#15](https://github.com/nibtime/next-safe-middleware/pull/15) [`e7b4193`](https://github.com/nibtime/next-safe-middleware/commit/e7b4193e3935d945f2103ecd75f2826aaaad82cc) Thanks [@nibtime](https://github.com/nibtime)! - better bundling config + bundling of external utils. Saves around ~100% size for `_middleware` - important for edge where limit is 1MB

* [#15](https://github.com/nibtime/next-safe-middleware/pull/15) [`e7b4193`](https://github.com/nibtime/next-safe-middleware/commit/e7b4193e3935d945f2103ecd75f2826aaaad82cc) Thanks [@nibtime](https://github.com/nibtime)! - provide an API handler for easy creation of a report procesing endpoint by Next/Vercel cloud function

- [#17](https://github.com/nibtime/next-safe-middleware/pull/17) [`b084027`](https://github.com/nibtime/next-safe-middleware/commit/b0840272b32fbec265e5bee26607160b55cb9dc4) Thanks [@nibtime](https://github.com/nibtime)! - provide `strictInlineStyles` middleware. Extend `dist/document` to write out hashes of inline styles (Hash-based) or attach nonce to inline styles (Nonce-based).

* [#17](https://github.com/nibtime/next-safe-middleware/pull/17) [`b084027`](https://github.com/nibtime/next-safe-middleware/commit/b0840272b32fbec265e5bee26607160b55cb9dc4) Thanks [@nibtime](https://github.com/nibtime)! - add `tellsupported` config option (a function) to `strictDynamic`. Allows for strong customization of fallback behavior by parsed user agent.

## 0.4.0

### Minor Changes

- [#13](https://github.com/nibtime/next-safe-middleware/pull/13) [`67469d7`](https://github.com/nibtime/next-safe-middleware/commit/67469d732b7d9bff6fe507cf94852525a10c991e) Thanks [@nibtime](https://github.com/nibtime)! - provide a uniform middleware builder and configuration interface

* [`6b8bbc1`](https://github.com/nibtime/next-safe-middleware/commit/6b8bbc19e37685695952cc32928f2f3b51ca9f0e) Thanks [@nibtime](https://github.com/nibtime)! - add configuration options to `strictDynamic` (allowUnsafeEval, reportOnly)

## 0.3.1

### Patch Changes

- [#11](https://github.com/nibtime/next-safe-middleware/pull/11) [`7f44414`](https://github.com/nibtime/next-safe-middleware/commit/7f44414f0bb09d13d1a89fa97be186bd59fd615d) Thanks [@nibtime](https://github.com/nibtime)! - add a undefined guard to browser support check of `strictDynamic`. This led to undesired behavior when user agent is empty/unknown.

## 0.3.0

### Minor Changes

- [#8](https://github.com/nibtime/next-safe-middleware/pull/8) [`84944a4`](https://github.com/nibtime/next-safe-middleware/commit/84944a42dbd3ee8ce139fea01e62cc86ea123c8b) Thanks [@nibtime](https://github.com/nibtime)! - add reporting middleware to configure reporting according to Reporting API spec

* [#10](https://github.com/nibtime/next-safe-middleware/pull/10) [`2b8a0bb`](https://github.com/nibtime/next-safe-middleware/commit/2b8a0bbd6e0e102e5f31db0c53d449573503c80b) Thanks [@nibtime](https://github.com/nibtime)! - `strictDynamic` middleware for easier strict-CSP configuration. With baked-in fallback logic for browser non-support.

## 0.2.0

### Minor Changes

- [#3](https://github.com/nibtime/next-safe-middleware/pull/3) [`a1137ab`](https://github.com/nibtime/next-safe-middleware/commit/a1137aba24c534d43770442f3a5ee06f43bdb1de) Thanks [@nibtime](https://github.com/nibtime)! - bundle package with swc and rollup as cjs and esm

## 0.1.0

**This version has been unpublished from NPM because it uses a broken build config that makes the package unusable**

### Minor Changes

- [#1](https://github.com/nibtime/next-safe-middleware/pull/1) [`06456a8`](https://github.com/nibtime/next-safe-middleware/commit/06456a83764a825a677e41c1e37ae2861d561ada) Thanks [@nibtime](https://github.com/nibtime)! - initial release of @next-safe/middleware and its companion app for e2e testing
