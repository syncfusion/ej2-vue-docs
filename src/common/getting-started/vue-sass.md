# Getting Started with Syncfusion Vue UI Components and Vue CLI

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your Vue applications.
To install Vue CLI, use the following command.

```bash
npm install -g @vue/cli
npm install -g @vue/cli-init
```

Start a new project using the following Vue CLI command.

```bash
vue init webpack-simple quickstart

cd quickstart
npm install

```

## Adding Syncfusion packages

All the available Syncfusion Vue packages are published in the [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.
Choose the component to be installed. In this application, the button component is installed.

To install the button component, use the following command.

```bash
npm install @syncfusion/ej2-vue-grids --save
```

## Registering Vue component

The two ways to register the Vue component are:
* Vue.use()
* Vue.component()

### Using Vue.use()

Import the component plugin from the EJ2 Vue package and register it using Vue.use() with component plugin as its argument.

Refer to the following code snippet.

```typescript
import { GridPlugin, Page } from "@syncfusion/ej2-vue-grids";

Vue.use(GridPlugin);
```

Note: By registering the component plugin in Vue, all child directives can also be globally registered.

### Using Vue.component()

Import the component and component plugin from EJ2 Vue package and register it using the Vue.component() with name of component from component plugin and the EJ2 Vue component as its arguments.

Refer to the following the code snippet.

```typescript
import { GridComponent, GridPlugin } from "@syncfusion/ej2-vue-grids";

Vue.use(GridPlugin.name, GridComponent);
```

Note: By using the Vue.component(), only the EJ2 Vue component can be registered. The child directives should be registered separately.

## Creating Vue sample

Add the EJ2 Vue button in the `<template>` section of the `App.vue` file in src directory using `<ejs-button>`. The content attribute of the button component is provided as name in the data option of the `<script>` section.

```html
<template>
  <div id="app">
    <ejs-grid :dataSource="data" :allowPaging="true" :pageSettings="pageSettings">
      <e-columns>
        <e-column field="OrderID" headerText="Order ID" textAlign="Right" width="90"></e-column>
        <e-column field="CustomerID" headerText="Customer ID" width="120"></e-column>
        <e-column field="Freight" headerText="Freight" textAlign="Right" format="C2" width="90"></e-column>
      </e-columns>
    </ejs-grid>
  </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, GridComponent } from "@syncfusion/ej2-vue-grids";
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: [
        { OrderID: 10248, CustomerID: "VINET", Freight: 32.38 },
        { OrderID: 10249, CustomerID: "TOMSP", Freight: 11.61 },
        { OrderID: 10250, CustomerID: "HANAR", Freight: 65.83 },
        { OrderID: 10251, CustomerID: "VICTE", Freight: 41.34 },
        { OrderID: 10252, CustomerID: "SUPRD", Freight: 51.3 },
        { OrderID: 10253, CustomerID: "HANAR", Freight: 58.17 },
        { OrderID: 10254, CustomerID: "CHOPS", Freight: 22.98 }
      ],
      pageSettings: { pageSize: 5 }
    };
  },
  provide: {
    grid: [Page]
  }
};
</script>
```

## Adding SCSS reference

Add the styles of Grid component to the `<style>` section of the `App.vue` file as follows.

```html
<style lang="scss">
// syncfusion styles
@import "../node_modules/@syncfusion/ej2-base/styles/material.scss";
@import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.scss";
</style>
```

## Adding includePaths option

While using scss files for style reference, you need to configure the `includePaths` in sass-loader options in the `webpack.config.js` like below:

```ts
module: {  
        rules: [  
            ....  
            ....  
            {  
                test: /\.vue$/,  
                loader: 'vue-loader',  
                options: {  
                    loaders: {  
                        // Since sass-loader (weirdly) has SCSS as its default parse mode, we map  
                        // the "scss" and "sass" values for the lang attribute to the right configs here.
                        'scss': [  
                            'vue-style-loader',  
                            'css-loader',  
                            {  
                                loader: "sass-loader",  
                                options: {  
                                    includePaths: [  
                                        path.resolve(__dirname,"./node_modules/@syncfusion")  
                                    ]  
                                }  
                            }  
                        ]  
                        ....  
                        ....  
                    }  
                }  
            }  
            ....  
            ....  
        ]  
}  
```

## Running the application

Now, run the `npm run dev` command in the console to build your application and open it in the browser.

{% tab template="common/sass", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" :allowPaging="true" :pageSettings='pageSettings'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
            <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page } from "@syncfusion/ej2-vue-grids";
import { data } from "./datasource.js";

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      pageSettings: { pageSizes: true, pageSize: 9 }
    };
  },
  provide: {
    grid: [Page]
  }
}
</script>

<style lang="scss">
// syncfusion styles
@import "../node_modules/@syncfusion/ej2-base/styles/material.scss";
@import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.scss";
</style>

```

{% endtab %}

## How To Override styles

In Syncfusion Vue components, you can override control styles by replacing sass variable values like below:

```html
<style lang="scss">

// SASS Variable override
$accent: black;
$primary: blue;

// syncfusion styles
@import "../node_modules/@syncfusion/ej2-base/styles/material.scss";
@import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.scss";

</style>
```
