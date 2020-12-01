# Deployment

## CDN

The CDN links are provided individually for all the scripts and style sheets of Syncfusion Vue UI components.

The CDN link is provided to following files in the package

1. UMD Files
2. CSS Files

_The latest minified versions of all UMD, Global and CSS files are available on CDN:_

* **`https://cdn.syncfusion.com/ej2/PACKAGENAME/dist/PACKAGENAME.umd.min.js`**
* **`https://cdn.syncfusion.com/ej2/PACKAGENAME/styles/THEMENAME.css`**

For example

* [https://cdn.syncfusion.com/ej2/ej2-vue-inputs/dist/ej2-vue-inputs.umd.min.js](https://cdn.syncfusion.com/ej2/ej2-vue-inputs/dist/ej2-vue-inputs.umd.min.js)
* [https://cdn.syncfusion.com/ej2/ej2-vue-inputs/styles/material.css](https://cdn.syncfusion.com/ej2/ej2-vue-inputs/styles/material.css)

_Versioned files are also available on CDN._

* **`https://cdn.syncfusion.com/ej2/VERSION/PACKAGENAME/dist/PACKAGENAME.umd.min.js`**
* **`https://cdn.syncfusion.com/ej2/VERSION/PACKAGENAME/styles/THEMENAME.css`**

For example

* [https://cdn.syncfusion.com/ej2/1.0.18/ej2-vue-inputs/dist/ej2-vue-inputs.umd.min.js](https://cdn.syncfusion.com/ej2/1.0.18/ej2-vue-inputs/dist/ej2-vue-inputs.umd.min.js)
* [https://cdn.syncfusion.com/ej2/1.0.18/ej2-vue-inputs/styles/material.css](https://cdn.syncfusion.com/ej2/1.0.18/ej2-vue-inputs/styles/material.css)

## Packages

Syncfusion Vue packages is published and available in public
[npm](https://www.npmjs.com/search?q=ej2-vue&page=1&ranking=optimal) registry.

### Anatomy of NPM Packages

Syncfusion Vue UI components are shipped as npm packages. Following table explains the purpose of each file available in the package.

|    Files                                                                  |    Purpose                                                                                                                                                                                                                                                                                   |
|---------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `dist/es6`                                                               |    This folder contains the ES6 formatted JS file of   the package.                                                                                                   |
|    `dist/<packagename>.umd.min.js`   `dist/<packagename>.umd.js`              |        For applications using AMD or Common JS based   module loader can be utilize these files.                                                                                                                                                                                             |
|    `src/`                                                                   |    This folder contains the script files in AMD   format. You can connect these AMD files as a package in System JS or Require   JS.                                                                                                                                                         |
|    `styles/<theme name>.css`   `styles/<theme name>.scss`                     |    This folder contains the CSS and SCSS files of the   package.                                                                                                                                                                                                                             ||