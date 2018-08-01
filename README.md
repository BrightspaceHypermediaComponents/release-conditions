# d2l-release-conditions
[![Published on webcomponents.org](https://img.shields.io/badge/webcomponents.org-published-blue.svg)](https://www.webcomponents.org/element/BrightspaceUI/release-conditions)
[![Bower version][bower-image]][bower-url]
[![Build status][ci-image]][ci-url]

View and edit a condition set

## Installation

`d2l-release-conditions` can be installed from [Bower][bower-url]:
```shell
bower install d2l-release-conditions
```

## Usage

Include the [webcomponents.js](http://webcomponents.org/polyfills/) "lite" polyfill (for browsers who don't natively support web components), then import `d2l-release-conditions.html`:

```html
<head>
	<script src="bower_components/webcomponentsjs/webcomponents-lite.js"></script>
	<link rel="import" href="bower_components/d2l-release-conditions/d2l-release-conditions.html">
</head>
```

<!---
```
<custom-element-demo>
  <template>
    <script src="../webcomponentsjs/webcomponents-lite.js"></script>
    <link rel="import" href="../d2l-typography/d2l-typography.html">
    <link rel="import" href="d2l-release-conditions.html">
    <custom-style include="d2l-typography">
      <style is="custom-style" include="d2l-typography"></style>
    </custom-style>
    <style>
      html {
        font-size: 20px;
        font-family: 'Lato', 'Lucida Sans Unicode', 'Lucida Grande', sans-serif;
      }
    </style>
    <next-code-block></next-code-block>
  </template>
</custom-element-demo>
```
-->
```html
<d2l-release-conditions>My element</d2l-release-conditions>
```

## Developing, Testing and Contributing

After cloning the repo, run `npm install` to install dependencies.

If you don't have it already, install the [Polymer CLI](https://www.polymer-project.org/3.0/docs/tools/polymer-cli) globally:

```shell
npm install -g polymer-cli
```

To start a [local web server](https://www.polymer-project.org/3.0/docs/tools/polymer-cli-commands#serve) that hosts the demo page and tests:

```shell
polymer serve
```

To lint ([eslint](http://eslint.org/) and [Polymer lint](https://www.polymer-project.org/3.0/docs/tools/polymer-cli-commands#lint)):

```shell
npm run lint
```

To run unit tests locally using [Polymer test](https://www.polymer-project.org/3.0/docs/tools/polymer-cli-commands#tests):

```shell
npm run test:polymer:local
```

To lint AND run local unit tests:

```shell
npm test
```

### How to Test Changes Locally Within the LMS
1. Develop within this repo as usual
2. Once the changes are done that you want to try, run the command `bower link` in the root of this repo locally
3. In your local checkout of the [Brightspace Integration][bsi-link] project, run the command `bower link d2l-release-conditions`, which should create a symlink to your local copy of the repo
4. Build Brightspace Integration by running `npm run build`
5. Run Brightspace Integration by running `npm run serve`
6. Go to {instance}/config/Infrastructure directory
7. Edit `D2L.LP.Web.UI.Html.Bsi.config.json`
8. Change the `daylight-polymer-<version>` property to the localhost server (note the trailing /)
9. Restart IIS

## How to Propagate Changes to the LMS
1. Merge your PR into the master branch of this repo
2. Create a new release, versioning appropriately
	See [here](https://help.github.com/articles/creating-releases/) about making a release, see [here](https://semver.org/) about appropriate versioning
3. In the [Brightspace Integration][bsi-link] project, create a new PR to adjust the version of `d2l-release-conditions` in bower.json
	* Unlock bower.json by running `bower-locker unlock`
	* Make adjustments
	* Lock bower.json by running `bower-locker lock`
4. Merge the PR
5. Publish a new release of BSI
6. Create a PR in LP to update `daylight-polymer-<version>` to the new version of BSI you just published


[bower-url]: http://bower.io/search/?q=d2l-release-conditions
[bower-image]: https://badge.fury.io/bo/d2l-release-conditions.svg
[ci-url]: https://travis-ci.org/BrightspaceUI/release-conditions
[ci-image]: https://travis-ci.org/BrightspaceUI/release-conditions.svg?branch=master
[bsi-link]: https://github.com/Brightspace/brightspace-integration
