# Getting Started

This section explains you the steps required to create a TreeMap and demonstrate its basic usage.

## Dependencies

The following list of minimum dependencies are required to use the treemap:

```javascript
|-- @syncfusion/ej2-treemap
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-pdf-export
    |-- @syncfusion/ej2-file-utils
    |-- @syncfusion/ej2-compression
    |-- @syncfusion/ej2-svg-base
```

## Installation and configuration

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your Vue applications. To install Vue CLI use the following command.

```bash
npm install -g @vue/cli

npm install -g @vue/cli-init
```

Start a new project using below Vue CLI command.

```bash
vue init webpack-simple quickstart

cd quickstart

npm install

```

## Adding Syncfusion packages

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry. You can choose the component that you want to install. For this application, we are going to use TreeMap component.

To install TreeMap component, use the following command

```bash
npm install @syncfusion/ej2-vue-treemap –save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.

* Vue.use()
* Vue.component()

### Using Vue.use()

Import the Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { TreeMapPlugin } from '@syncfuion/ej2-vue-treemap';

Vue.use(TreeMapPlugin);
```

> By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the Component and Component Plugin from EJ2 Vue Package, register the same using the Vue.component() with name of Component from ComponentPlugin and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { TreeMapComponent, TreeMapPlugin } from '@syncfusion/ej2-vue-treemap';

Vue.component(TreeMapPlugin.name, TreeMapComponent);
```

Note: By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Initialize TreeMap component

Add the EJ2 Vue TreeMap using `<ejs-treemap>` to the `<template>` section of the `App.vue` file in src directory, the content attribute of the TreeMap component is provided as name in data option in the `<script>` section.

```html
<template>
    <div id="app">
    <ejs-treemap></ejs-treemap>
  </div>
</template>
<script>
import Vue from 'vue';
import { TreeMapPlugin } from '@syncfusion/ej2-vue-treemap';

Vue.use(TreeMapPlugin);
export default Vue.extend ({});
</script>
```

## Run the application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

The following example shows a basic TreeMap.

```html
<template>
<ejs-treemap id="treemap"></ejs-treemap>
</template>

<script>
import Vue from 'vue';
import { TreeMapPlugin } from '@syncfusion/ej2-vue-treemap';

Vue.use(TreeMapPlugin);

export default Vue.extend ({});
</script>
```

Since any data source has not been bound to the tree map, no shape will be rendered. Only an empty SVG element is appended to the tree map container.

## Module Injection

The tree map control is segregated into individual feature-wise modules. To use a particular feature, inject its feature module using the `provide` option on component creation. Find the modules available in tree map and their descriptions as follows.

* TreeMapHighlight - Inject this provider to use highlight feature.
* TreeMapSelection - Inject this provider to use selection feature.
* TreeMapLegend - Inject this provider to use legend feature.
* TreeMapTooltip - Inject this provider to use tooltip series.

In the current application, the above basic tree map is modified to visualize international airport count in South America.

In this demo, the tree map is just rendered with labels. For this, you need not to import any modules.

## Render tree map

This section explains how to render the tree map with data source.

{% tab template="treemap/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
        <ejs-treemap id="treemap" :height='height' :dataSource='dataSource' :weightValuePath='weightValuePath' :leafItemSettings='leafItemSettings'></ejs-treemap>
    </div>
</template>
<script>
import Vue from 'vue';
import { TreeMapPlugin } from "@syncfusion/ej2-vue-treemap";
Vue.use(TreeMapPlugin);

export default {
  data: function() {
    return {
    height:'350px',
     dataSource: [
        { Title: 'State wise International Airport count in South America', State: "Brazil", Count: 25 },
        { Title: 'State wise International Airport count in South America', State: "Colombia", Count: 12 },
        { Title: 'State wise International Airport count in South America', State: "Argentina", Count: 9 },
        { Title: 'State wise International Airport count in South America', State: "Ecuador", Count: 7 },
        { Title: 'State wise International Airport count in South America', State: "Chile", Count: 6 },
        { Title: 'State wise International Airport count in South America', State: "Peru", Count: 3 },
        { Title: 'State wise International Airport count in South America', State: "Venezuela", Count: 3 },
        { Title: 'State wise International Airport count in South America', State: "Bolivia", Count: 2 },
        { Title: 'State wise International Airport count in South America', State: "Paraguay", Count: 2 },
        { Title: 'State wise International Airport count in South America', State: "Uruguay", Count: 2 },
        { Title: 'State wise International Airport count in South America', State: "Falkland Islands",Count: 1 },
        { Title: 'State wise International Airport count in South America', State: "French Guiana", Count:1 },
        { Title: 'State wise International Airport count in South America', State: "Guyana", Count: 1 },
        { Title: 'State wise International Airport count in South America', State: "Suriname", Count: 1 },
    ],
    weightValuePath: 'Count',
    leafItemSettings: {
        labelPath: 'State',
    }
    }
  }
}
</script>
```

{% endtab %}

Here, the tree map is created with data source and set with the [`weightValuePath`] as count. You can customize the leaf level tree map items using the [`leafItemSettings`]. The properties such as [`fill`], [`border`], and [`labelPosition`] can be changed using the [`leafItemSettings`].

## Apply color mapping

The color mapping feature supports customization of item colors based on the underlying value of item received from bound data source. Specify the field name from the values that have to be compared for the item in the [`equalColorValuePath`] or [`rangeColorValuePath`] property.

{% tab template="treemap/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
        <ejs-treemap id="treemap" :height='height' :dataSource='dataSource' :weightValuePath='weightValuePath' :equalColorValuePath='equalColorValuePath' :leafItemSettings='leafItemSettings'></ejs-treemap>
    </div>
</template>
<script>
import Vue from 'vue';
import { TreeMapPlugin } from "@syncfusion/ej2-vue-treemap";
Vue.use(TreeMapPlugin);

export default {
  data: function() {
    return {
     height: '350px',
        dataSource: [
            { Title: 'State wise International Airport count in South America', State: "Brazil", Count: 25 },
            { Title: 'State wise International Airport count in South America', State: "Colombia", Count: 12 },
            { Title: 'State wise International Airport count in South America', State: "Argentina", Count: 9 },
            { Title: 'State wise International Airport count in South America', State: "Ecuador", Count: 7 },
            { Title: 'State wise International Airport count in South America', State: "Chile", Count: 6 },
            { Title: 'State wise International Airport count in South America', State: "Peru", Count: 3 },
            { Title: 'State wise International Airport count in South America', State: "Venezuela", Count: 3 },
            { Title: 'State wise International Airport count in South America', State: "Bolivia", Count: 2 },
            { Title: 'State wise International Airport count in South America', State: "Paraguay", Count: 2 },
            { Title: 'State wise International Airport count in South America', State: "Uruguay", Count: 2 },
            { Title: 'State wise International Airport count in South America', State: "Falkland Islands", Count: 1 },
            { Title: 'State wise International Airport count in South America', State: "French Guiana", Count: 1 },
            { Title: 'State wise International Airport count in South America', State: "Guyana", Count: 1 },
            { Title: 'State wise International Airport count in South America', State: "Suriname", Count: 1 },
        ],
        weightValuePath: 'Count',
        equalColorValuePath: 'Count',
        leafItemSettings: {
            labelPath: 'State',
            colorMapping: [
                {
                    value: 25,
                    color: '#634D6F'
                },
                {
                    value: 12,
                    color: '#B34D6D'
                },
                {
                    value: 9,
                    color: '#557C5C'
                },
                {
                    value: 7,
                    color: '#44537F'
                },
                {
                    value: 6,
                    color: '#637392'
                },
                {
                    value: 3,
                    color: '#7C754D'
                },
                {
                    value: 2,
                    color: '#2E7A64'
                },
                {
                    value: 1,
                    color: '#95659A'
                },
            ]
        }
    }
  }
}
</script>
```

{% endtab %}

## Enable legend

You can show legend for the tree map by setting the [`visible`] property to true in [`legendSettings`] object and injecting the `TreeMapLegend` module using the `provide` option.

{% tab template="treemap/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
        <ejs-treemap id="treemap" :dataSource='dataSource' :legendSettings='legendSettings' :weightValuePath='weightValuePath' :equalColorValuePath='equalColorValuePath' :leafItemSettings='leafItemSettings'></ejs-treemap>
    </div>
</template>
<script>
import Vue from 'vue';
import { TreeMapPlugin, TreeMapLegend } from "@syncfusion/ej2-vue-treemap";
Vue.use(TreeMapPlugin);

export default {
  data: function() {
    return {
     dataSource: [
            { Title: 'State wise International Airport count in South America', State: "Brazil", Count: 25 },
            { Title: 'State wise International Airport count in South America', State: "Colombia", Count: 12 },
            { Title: 'State wise International Airport count in South America', State: "Argentina", Count: 9 },
            { Title: 'State wise International Airport count in South America', State: "Ecuador", Count: 7 },
            { Title: 'State wise International Airport count in South America', State: "Chile", Count: 6 },
            { Title: 'State wise International Airport count in South America', State: "Peru", Count: 3 },
            { Title: 'State wise International Airport count in South America', State: "Venezuela", Count: 3 },
            { Title: 'State wise International Airport count in South America', State: "Bolivia", Count: 2 },
            { Title: 'State wise International Airport count in South America', State: "Paraguay", Count: 2 },
            { Title: 'State wise International Airport count in South America', State: "Uruguay", Count: 2 },
            { Title: 'State wise International Airport count in South America', State: "Falkland Islands", Count: 1 },
            { Title: 'State wise International Airport count in South America', State: "French Guiana", Count: 1 },
            { Title: 'State wise International Airport count in South America', State: "Guyana", Count: 1 },
            { Title: 'State wise International Airport count in South America', State: "Suriname", Count: 1 },
        ],
        legendSettings: {
            visible: true,
            position: 'Top',
            shape: 'Rectangle'
        },
        weightValuePath: 'Count',
        equalColorValuePath: 'Count',
        leafItemSettings: {
            labelPath: 'State',
            colorMapping: [
                {
                    value: 25,
                    color: '#634D6F'
                },
                {
                    value: 12,
                    color: '#B34D6D'
                },
                {
                    value: 9,
                    color: '#557C5C'
                },
                {
                    value: 7,
                    color: '#44537F'
                },
                {
                    value: 6,
                    color: '#637392'
                },
                {
                    value: 3,
                    color: '#7C754D'
                },
                {
                    value: 2,
                    color: '#2E7A64'
                },
                {
                    value: 1,
                    color: '#95659A'
                },
            ]
        }
    }
  },
provide:{
     treemap:[TreeMapLegend]
}
}
</script>
```

{% endtab %}
