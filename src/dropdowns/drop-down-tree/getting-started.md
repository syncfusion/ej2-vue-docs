---
title: "Drop-down litreest Getting started"
component: "DropDown Tree"
description: "This section explains how to create a simple Syncfusion vue drop-down tree component and configure it's functionalities in vue."
---

# Getting Started

This section explains you about how to create a simple **Dropdown Tree** component and configure its available
functionalities in Vue.

## Get Started with Vue CLI

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your vue applications.
To install Vue CLI use the following command.

```bash
npm install -g @vue/cli
```

Start a new project using below Vue CLI command.

```bash
vue init webpack-simple quickstart

cd quickstart
npm install

```

## Adding Syncfusion packages

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.
You can choose the component that you want to install. For this application, we are going to use Dropdown Tree component.

To install Dropdown Tree component, use the following command

```bash
npm install @syncfusion/ej2-vue-dropdowns --save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.
* Vue.use()
* Vue.component()

### Using Vue.use()

Import the Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { DropDownTreePlugin } from '@syncfusion/ej2-vue-dropdowns';

Vue.use(DropDownTreePlugin);
```

Note : By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the Component and Component Plugin from EJ2 Vue Package,
register the same using the Vue.component() with name of Component from ComponentPlugin
and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { DropDownTreeComponent, DropDownTreePlugin } from '@syncfusion/ej2-vue-dropdowns';

Vue.component(DropDownTreePlugin.name, DropDownTreeComponent);
```

Note: By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Creating Vue Sample

Add the EJ2 Vue Dropdown Tree using `<ejs-dropdowntree>` to the `<template>` section of the `App.vue` file in src directory,the content attribute of the Dropdown Tree component is provided as name in data option in the `<script>` section.

```html
<template>
    <div class="control_wrapper">
        <ejs-dropdowntree id='dropdowntree'></ejs-dropdowntree>
    </div>
</template>
<script>
import Vue from 'vue';
import { DropDownTreePlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(DropDownTreePlugin);

export default Vue.extend({
  data: function() {
    return {

    };
  }
});

</script>
```

## Adding CSS Reference

Add Dropdown Tree component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
</style>
```

## Binding data source

The Dropdown Tree component can load the data either from local data sources or remote data services. This can be done using the `dataSource` property that is a member of the `fields` property. The dataSource property supports array of JavaScript objects and DataManager. Here, an array of JSON values is passed to the Dropdown Tree component.

```html

<template>
    <div class="control_wrapper">
        <ejs-dropdowntree id='dropdowntree' :fields='fields'></ejs-dropdowntree>
    </div>
</template>
<script>
import Vue from 'vue';
import { DropDownTreePlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(DropDownTreePlugin);

var data =  [
    {
        nodeId: '01', nodeText: 'Music',
        nodeChild: [
            { nodeId: '01-01', nodeText: 'Gouttes.mp3' }
        ]
    },
    {
        nodeId: '02', nodeText: 'Videos', expanded: true,
        nodeChild: [
            { nodeId: '02-01', nodeText: 'Naturals.mp4' },
            { nodeId: '02-02', nodeText: 'Wild.mpeg' },
        ]
    },
    {
        nodeId: '03', nodeText: 'Documents',
        nodeChild: [
            { nodeId: '03-01', nodeText: 'Environment Pollution.docx' },
            { nodeId: '03-02', nodeText: 'Global Water, Sanitation, & Hygiene.docx' },
            { nodeId: '03-03', nodeText: 'Global Warming.ppt' },
            { nodeId: '03-04', nodeText: 'Social Network.pdf' },
            { nodeId: '03-05', nodeText: 'Youth Empowerment.pdf' },
        ]
    }];

export default Vue.extend({
  data: function() {
    return {
      fields: { dataSource: data, value: 'nodeId', text: 'nodeText', child: 'nodeChild' }
    };
  }
});

</script>

```

## Run the application

After completing the configuration required to render a basic Dropdown Tree, run the following command to
display the output in your default browser.

```cmd
npm run dev
```

{% tab template="drop-down-tree/getting-started/getting-started", isDefaultActive=true %}

```html

<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-dropdowntree id='dropdowntree' :fields='fields'></ejs-dropdowntree>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import { DropDownTreePlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(DropDownTreePlugin);

var data =  [
    {
        nodeId: '01', nodeText: 'Music',
        nodeChild: [
            { nodeId: '01-01', nodeText: 'Gouttes.mp3' }
        ]
    },
    {
        nodeId: '02', nodeText: 'Videos', expanded: true,
        nodeChild: [
            { nodeId: '02-01', nodeText: 'Naturals.mp4' },
            { nodeId: '02-02', nodeText: 'Wild.mpeg' },
        ]
    },
    {
        nodeId: '03', nodeText: 'Documents',
        nodeChild: [
            { nodeId: '03-01', nodeText: 'Environment Pollution.docx' },
            { nodeId: '03-02', nodeText: 'Global Water, Sanitation, & Hygiene.docx' },
            { nodeId: '03-03', nodeText: 'Global Warming.ppt' },
            { nodeId: '03-04', nodeText: 'Social Network.pdf' },
            { nodeId: '03-05', nodeText: 'Youth Empowerment.pdf' },
        ]
    }];

export default {
  data (){
    return {
      fields: { dataSource: data, value: 'nodeId', text: 'nodeText', child: 'nodeChild' }
    }
  }
}

</script>

<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
</style>

```

{% endtab %}
