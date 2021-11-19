# Getting Started with Syncfusion File Manager Component in Vue 3

This section explains how to use File Manager component in Vue 3 application.

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

## Adding Syncfusion File Manager package in the application

Syncfusion Vue packages are maintained in the [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.
The File Manager component will be used in this example. To install it use the following command.

```bash
npm install @syncfusion/ej2-vue-filemanager --save
```

## Adding CSS reference for Syncfusion Vue File Manager component

Import the needed css styles for the  File Manager component along with dependency styles in the `<script>` section of the `src/App.vue` file as follows.

```js
<script>
  import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  import "../node_modules/@syncfusion/ej2-icons/styles/material.css";
  import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
  import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
  import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
  import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
  import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
  import "../node_modules/@syncfusion/ej2-layouts/styles/material.css";
  import "../node_modules/@syncfusion/ej2-grids/styles/material.css";
  import "../node_modules/@syncfusion/ej2-vue-filemanager/styles/material.css";
</script>
```

## Adding Syncfusion Vue File Manager component in the application

You have completed all the necessary configurations needed  for rendering the Syncfusion Vue component. Now, you are going to add the File Manager component using following steps.

1. Import the File Manager component in the `<script>` section of the `src/App.vue` file.

     ```html
     <script>
       import { FileManagerComponent } from "@syncfusion/ej2-vue-filemanager";
      </script>
     ```

2. Register the File Manager component as like in the below code snippet.

    ```js
        import { FileManagerComponent } from "@syncfusion/ej2-vue-filemanager";
    //Component registeration
    export default {
        name: "App",
        components: {
          "ejs-filemanager": FileManagerComponent
        }
    }
    ```

3. Add the component definition in template section.

    ```html
        <ejs-filemanager id="file-manager" :ajaxSettings="ajaxSettings"></ejs-filemanager>
    ```

    >Note: By default, LargeIcons view will be initialized in the File Manager. If Grid view is required then the DetailsView module needs to be injected using `provide`.

4. Summarizing the above steps, update the `src/App.vue` file with following code.

  ```html
    <template>
    <ejs-filemanager id="file-manager" :ajaxSettings="ajaxSettings"></ejs-filemanager>
  </template>

  <script>
  import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  import "../node_modules/@syncfusion/ej2-icons/styles/material.css";
  import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
  import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
  import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
  import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
  import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
  import "../node_modules/@syncfusion/ej2-layouts/styles/material.css";
  import "../node_modules/@syncfusion/ej2-grids/styles/material.css";
  import "../node_modules/@syncfusion/ej2-vue-filemanager/styles/material.css";

  import { FileManagerComponent, DetailsView, NavigationPane, Toolbar } from "@syncfusion/ej2-vue-filemanager";

  export default {
      name: "App",
      components: {
        "ejs-filemanager": FileManagerComponent
      },
      provide: {
          filemanager: [DetailsView, NavigationPane, Toolbar]
      },
      data() {
      return {
        ajaxSettings:
          {
            url: "https://ej2-aspcore-service.azurewebsites.net/api/FileManager/FileOperations",
            getImageUrl: "https://ej2-aspcore-service.azurewebsites.net/api/FileManager/GetImage",
            uploadUrl: "https://ej2-aspcore-service.azurewebsites.net/api/FileManager/Upload",
            downloadUrl: "https://ej2-aspcore-service.azurewebsites.net/api/FileManager/Download"
          },
      };
    }
  }
  </script>

  ```

## Running the application

Run the application using the following command.

```bash
npm run serve
```

Web server will be initiated, Open the quick start app in the browser at port [`localhost:8080`](http://localhost:8080/).

![Output](./images/vue3-filemanager-demo.PNG)
