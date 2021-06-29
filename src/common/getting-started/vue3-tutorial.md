# Getting Started with Syncfusion UI Components in Vue CLI 3

You can make use of [`Vue CLI 3`](https://github.com/SyncfusionExamples/EJ2-Vue-3-template) to setup your Vue applications.
To install Vue CLI 3, use the following command.

```bash
npm install -g @vue/cli
npm install -g @vue/cli-init
```

Start a new project using the following Vue CLI 3 command.

```bash
vue init webpack-simple quickstart

cd quickstart
npm install

```

## Adding Syncfusion packages

Syncfusion packages are distributed in npm as @syncfusion scoped packages. You can get all the vue syncfusion package from npm [link](https://www.npmjs.com/search?q=%40syncfusion%2Fej2-vue-).

Add @syncfusion/ej2-vue-dropdowns package to the application.

To install the dropdownslist component, use the following command.

```bash
npm install @syncfusion/ej2-vue-dropdowns –save
```

## Creating Vue 3 sample

Add the Syncfusion Vue DropDownList using `<ejs-dropdownlist>` to the `<template>` section of the `App.vue` file in src directory, the content attribute of the DropDownList component is provided as name in data option in the `<script>` section.

```html
<template>
  <ejs-dropdownlist
    id="dropdownlist"
    :itemTemplate="itemTemplate"
    :dataSource="sportsData"
    :fields="fields"
    placeholder="Select a game"
  ></ejs-dropdownlist>
</template>

<script>
import { DropDownListComponent } from "@syncfusion/ej2-vue-dropdowns";

import { createApp } from "vue";

const app = createApp({
  // Displays "Hello, World" initially, changes based on input
  template: '<hello></hello>'
}); 

// Register the `hello` component
var itemVue = app.component('itemTemplate', {
  data: () => ({}),
  template:`<span><span class='name'>{{data.Game}}</span><span class ='city'>{{data.Id}}</span></span>`
});  
 
export default {
  name: "App",
  components: {
    'ejs-dropdownlist' : DropDownListComponent,
  },
  data() {
    return {
      sportsData: [
        { Id: "game1", Game: "Badminton" },
        { Id: "game2", Game: "Football" },
        { Id: "game3", Game: "Tennis" },
      ],
      fields: { text: "Game", value: "Id" },
      itemTemplate:  function() {
        return { template: itemVue };
      }
    };
  },
};
</script>
```

## Adding CSS reference

Add the styles of the dropdownlist component to the `<style>` section of the `App.vue` file as follows.

```html
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";

button {
  margin: 25px 5px 20px 20px;
}
</style>
```
## Running the application

Now, run the `npm run dev` command in the console to build your application and open it in the browser.
