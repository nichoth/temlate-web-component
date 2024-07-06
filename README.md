# template web component
![tests](https://github.com/nichoth/template-web-component/actions/workflows/nodejs.yml/badge.svg)
[![types](https://img.shields.io/npm/types/@nichoth/catch-links?style=flat-square)](README.md)
[![module](https://img.shields.io/badge/module-ESM%2FCJS-blue?style=flat-square)](README.md)
[![semantic versioning](https://img.shields.io/badge/semver-2.0.0-blue?logo=semver&style=flat-square)](https://semver.org/)
[![license](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE)

A template for vanilla web components.

## use
1. Use the template button in github. Or clone this then
`rm -rf .git && git init`. Then `npm i && npm init`.

2. Edit the source code in `src/index.ts`.

3. Delete either `.github/workflows/gh-pages-docs.yml` or `.github/workflows/gh-pages.yml`, depending on whether you want to deploy an example or docs to github pages.

4. __Edit things__
    * Edit this readme
    * edit the `build-example` command in `package.json` so that it has the right
    namespace for github pages

## featuring

* compile the source to both ESM and CJS format, and put compiled files in `dist`.
* ignore `dist` and `*.js` in git, but don't ignore them in npm. That way we
  don't commit any compiled code to git, but it is available to consumers.
* use npm's `prepublishOnly` hook to compile the code before publishing to npm.
* use [exports](./package.json#L41) field in `package.json` to make sure the right format is used
  by consumers.
* `preversion` npm hook -- lint
* `postversion` npm hook -- `git push --follow-tags && npm publish`
* eslint -- `npm run lint`
* tests run in a browser environment via `tape-run` -- see [`npm test`](./package.json#L12).
  Includes `tap` testing tools -- [tapzero](https://github.com/bicycle-codes/tapzero)
  and [tap-spec](https://www.npmjs.com/package/tap-spec)
* CI via github actions

## the component

See *[Web Component lifecycle methods](https://gomakethings.com/the-web-component-lifecycle-methods/)*.

### [attributeChangedCallback](https://gomakethings.com/how-to-detect-when-attributes-change-on-a-web-component/#the-attributechangedcallback-method)

> runs whenever an attribute on the Web Component is added, removed, or changes in value.

> For performance reasons, the attributeChangedCallback() method only watches and reacts to attributes you tell it to. To do that, you create a `static` `observedAttributes` property, with an array of attributes to watch as its value.

> You can use any attributes you’d like, including non-standard ones.


### [disconnectedCallback](https://gomakethings.com/the-web-component-lifecycle-methods/#the-connectedcallback-and-disconnectedcallback-methods)

