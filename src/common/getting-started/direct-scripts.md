<!-- markdownlint-disable MD024 -->
# Getting Started with Syncfusion Vue UI Components using direct scripts in a quickstart application

This article provides a step-by-step introduction to configure Syncfusion Vue UI components (Essential JS 2) and build a simple HTML web application.

## Getting started by using CDN link for script and style references

### Prerequisites

* [Visual Studio Code](https://code.visualstudio.com/)

### Configure Syncfusion JavaScript (ES5) control in the application

1. Create an app folder `quickstart` for the Syncfusion  controls and open it in the Visual Studio Code.
2. The below hosted CDN links contains all Syncfusion Vue (ES) components resources in a single file.

    > Scripts: `https://cdn.syncfusion.com/ej2/ej2-vue-es5/dist/ej2-vue.min.js`
    >
    > Styles: `https://cdn.syncfusion.com/ej2/material.css`
3. Create an HTML file `~/quickstart/index.html` and add the below  Syncfusion and [Vue] (https://vuejs.org/v2/guide/installation.html#CDN) CDN link references. Now,  the `Button` element and register the `Syncfusion Vue Button` component in the index.html by using the following code.

{% tab template="common/getting-started-es5", sourceFiles="index.html", skipVue="true" %}

```html
  <!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">

<head>
    <title>Syncfusion Vue (ES5) UI Components</title>
    <!-- Essentail JS2 for Vue  (All components Styles) -->
    <link href="https://cdn.syncfusion.com/ej2/material.css" rel="stylesheet" type="text/css" />
    <!-- Vue library file-->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.5.16/dist/vue.min.js" type="text/javascript"></script>
    <!-- Essential JS 2 for Vue  global script -->
    <script src="https://cdn.syncfusion.com/ej2/ej2-vue-es5/dist/ej2-vue.min.js" type="text/javascript"></script>

</head>

<body>
    <h2>Syncfusion Vue Button Components</h2>
    <div id="app">
        <ejs-button is-primary="true">Button</ejs-button>
    </div>
    <script>
        new Vue({
            el: '#app',
        });
    </script>

</body>

</html>
```

{% endtab %}

Note : While using Syncfusion Vue components  in DOM templates, camelCased property (isPrimary)  names need to specify  in the  kebab-cased (is-primary) equivalents.

4. Finally, run the `~/quickstart/index.html` file in the web browser and it will render the Syncfusion Vue  Button component.