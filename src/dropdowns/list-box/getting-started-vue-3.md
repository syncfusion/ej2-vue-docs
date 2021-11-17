---
title: "list-box Getting started with Vue 3"
component: "ListBox"
description: "This section explains how to create a simple Syncfusion vue 3 list box component and configure it's functionalities in vue."
---

# Getting Started with Syncfusion ListBox Component in Vue 3

This section explains how to use ListBox component in Vue 3 application.

## Prerequisites

* `vue` : `3+`
* `node` : `10.15+`
* `vue-class-component` : `8.0.0-rc.1`

## Creating Vue application using Vue CLI

The easiest way to create a Vue application is to use the [`Vue CLI`](https://github.com/vuejs/vue-cli). Vue CLI versions above [`4.5.0`](https://v3.vuejs.org/guide/migration/introduction.html#vue-cli) are mandatory for creating applications using Vue 3. Use the following command to uninstall older versions of the Vue CLI.

```bash
npm uninstall vue-cli -g
```

Use the following commands to install the latest version of Vue CLI.

```bash
npm install -g @vue/cli
npm install -g @vue/cli-init
```

Create a new project using the command below.

```bash
vue create quickstart
cd quickstart
```

Initiating a new project prompts us to choose the type of project to be used for the current application. Select the option `Default (Vue 3 Preview)` from the menu.

![Reference](./images/vue3-terminal.png)

## Adding Syncfusion ListBox package in the application

Syncfusion Vue packages are maintained in the [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.
The ListBox component will be used in this example. To install it use the following command.

```bash
npm install @syncfusion/ej2-vue-dropdowns --save
```

## Adding CSS reference for Syncfusion Vue ListBox component

Import the needed css styles for the ListBox component along with dependency styles in the `<script>` section of the `src/App.vue` file as follows.

```html
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
</style>
```

## Adding Syncfusion Vue ListBox component in the application

You have completed all the necessary configurations needed  for rendering the Syncfusion Vue component. Now, you are going to add the ListBox component using following steps.

1. Import the ListBox component in the `<script>` section of the `src/App.vue` file.

    ```html
      <script>
      import { ListBoxComponent } from "@syncfusion/ej2-vue-dropdowns";
      </script>
    ```

2. Register the ListBox component which is used in this example.

    ```js
        import { ListBoxComponent } from "@syncfusion/ej2-vue-dropdowns";

        export default {
            name: "App",
            components: {
            "ejs-listbox": ListBoxComponent
            }
        }
    ```

3. Add the component definition in template section.

    ```html
    <template>
    <div class="control_wrapper">
        <ejs-listbox :dataSource='data'></ejs-listbox>
    </div>
    </template>
    ```

4. Summarizing the above steps, update the `src/App.vue` file with following code.

    ```html
    <template>
    <div class="control_wrapper" style="margin:10px auto 0; width:250px;">
        <ejs-listbox :dataSource='data'></ejs-listbox>
    </div>
    </template>

    <script>
    import { ListBoxComponent } from "@syncfusion/ej2-vue-dropdowns";

    export default {
        name: "App",
        components: {
          "ejs-listbox": ListBoxComponent
        },
        data: function() {
            return {
                data: [
                    { text: 'Hennessey Venom', id: 'list-01' },
                    { text: 'Bugatti Chiron', id: 'list-02' },
                    { text: 'Bugatti Veyron Super Sport', id: 'list-03' },
                    { text: 'SSC Ultimate Aero', id: 'list-04' },
                    { text: 'Koenigsegg CCR', id: 'list-05' },
                    { text: 'McLaren F1', id: 'list-06' },
                    { text: 'Aston Martin One- 77', id: 'list-07' },
                    { text: 'Jaguar XJ220', id: 'list-08' },
                    { text: 'McLaren P1', id: 'list-09' },
                    { text: 'Ferrari LaFerrari', id: 'list-10' },
                ]
            };
        }
    }
    </script>
    <style>
    @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
    </style>
    ```

## Running the application

Run the application using the following command.

```bash
npm run serve
```

Web server will be initiated, Open the quick start app in the browser at port [`localhost:8080`](http://localhost:8080/).

![Output](./images/vue3-listbox.PNG)