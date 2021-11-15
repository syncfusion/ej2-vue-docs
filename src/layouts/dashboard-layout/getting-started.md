---
title: "Getting Started"
component: "DashboardLayout"
description: "This section explains how to create a `DashboardLayout` component in the Vue application with its basic features."
---

# Getting Started

The following section explains the required steps to build the simple `DashboardLayout` component with its basic usage in step-by-step procedure.

## Dependencies

The following list of dependencies is required to use the DashboardLayout component in your application.

```javascript
|-- @syncfusion/ej2-vue-layouts
    |-- @syncfusion/ej2-vue-base
        |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-layouts

```

## Installation and configuration

* You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your vue applications. To install Vue CLI use the following command.

```bash
npm install -g @vue/cli
npm install -g @vue/cli-init
```

* Start a new project using the below Vue CLI command.

```bash
vue init webpack-simple quickstart

cd quickstart

npm install

```

## Adding Syncfusion packages

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.
You can choose the component that you want to install. For this application, we are going to use the DashboardLayout component.

To install `DashboardLayout` component, use the following command

```bash
npm install @syncfusion/ej2-vue-layouts -–save
```

## Registering Vue component

Two ways are available for registering the Vue Component. They are as follows.

* Vue.use()

* Vue.component()

### Using Vue.use()

Import the Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { DashboardLayoutPlugin } from '@syncfuion/ej2-vue-layouts';

Vue.use(DashboardLayoutPlugin);
```

> By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the `DashboardLayout` Component from EJ2 Vue Package, register the same using the Vue.component() with name of Component from ComponentPlugin and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { DashboardLayoutComponent, DashboardLayoutPlugin } from '@syncfuion/ej2-vue-layouts';

Vue.component(DashboardLayoutPlugin.name, DashboardLayoutComponent);
```

>> **Note**: By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Add DashboardLayout to the application

You can render the `DashboardLayout` component in the following two ways.

* Defined the panels property as the attribute in the HTML div element directly into the `<template>`.
* Using the `panels` property in `<e-panels>`.

### Setting the `panels` property using HTML attributes

Add the HTML div element into the `<template>` section of the `App.vue` file in src directory, the content attribute of the Splitter component is provided as name in data option in the `<script>` section.

```html
<template>
    <div>
        <div class="control-section">
            <!--  DashboardLayout element declaration -->
            <ejs-dashboardlayout id='defaultLayout' :cellSpacing="spacing" :columns="6">
                <div id="one" class="e-panel" data-row="0" data-col="0" data-sizeX="1" data-sizeY="1">
                    <div class="e-panel-container">
                        <div class="text-align">
                            <div>0</div>
                        </div>
                    </div>
                </div>
                <div id="two" class="e-panel" data-row="1" data-col="0" data-sizeX="1" data-sizeY="2">
                    <div class="e-panel-container">
                        <div class="text-align">
                            <div>1</div>
                        </div>
                    </div>
                </div>
                <div id="three" class="e-panel" data-row="0" data-col="1" data-sizeX="2" data-sizeY="2">
                    <div class="e-panel-container">
                        <div class="text-align">
                            <div>2</div>
                        </div>
                    </div>
                </div>
                <div id="four" class="e-panel" data-row="2" data-col="1" data-sizeX="1" data-sizeY="1">
                    <div class="e-panel-container">
                        <div class="text-align">
                            <div>3</div>
                        </div>
                    </div>
                </div>
                <div id="five" class="e-panel" data-row="2" data-col="2" data-sizeX="2" data-sizeY="1">
                    <div class="e-panel-container">
                        <div class="text-align">
                            <div>4</div>
                        </div>
                    </div>
                </div>
                <div id="six" class="e-panel" data-row="0" data-col="3" data-sizeX="1" data-sizeY="1">
                    <div class="e-panel-container">
                        <div class="text-align">
                            <div>5</div>
                        </div>
                    </div>
                </div>
                <div id="seven" class="e-panel" data-row="1" data-col="3" data-sizeX="1" data-sizeY="1">
                    <div class="e-panel-container">
                        <div class="text-align">
                            <div>6</div>
                        </div>
                    </div>
                </div>
                <div id="eight" class="e-panel" data-row="0" data-col="4" data-sizeX="1" data-sizeY="3">
                    <div class="e-panel-container">
                        <div class="text-align">
                            <div>7</div>
                        </div>
                    </div>
                </div>
            </ejs-dashboardlayout>
            <!-- end of dashboardlayout element -->
        </div>
    </div>
</template>

<script>
import Vue from "vue";
// Import syncfusion dashboardlayout component from layouts package
import { DashboardLayoutPlugin } from "@syncfusion/ej2-vue-layouts";

Vue.use(DashboardLayoutPlugin);

export default {
    data: function() {
        return {
          count: 8,
          spacing: [10,10]
        };
    }
}
</script>
```

## Adding style sheet to the application

To render the DashboardLayout component, need to import Layouts and its dependent component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";
</style>
```

>Note: If you want to refer the combined component styles, please make use of our [`CRG`](https://crg.syncfusion.com/) (Custom Resource Generator) in your application.

## Run the application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

{% tab template="dashboard-layout/getting-started", isDefaultActive=true %}

```html
<template>
    <div>
        <div class="control-section">
            <!--  DashboardLayout element declaration -->
            <ejs-dashboardlayout id='defaultLayout' :cellSpacing="spacing" :columns="6">
                <div id="one" class="e-panel" data-row="0" data-col="0" data-sizeX="1" data-sizeY="1">
                    <div class="e-panel-container">
                        <div class="text-align">
                            <div>0</div>
                        </div>
                    </div>
                </div>
                <div id="two" class="e-panel" data-row="1" data-col="0" data-sizeX="1" data-sizeY="2">
                    <div class="e-panel-container">
                        <div class="text-align">
                            <div>1</div>
                        </div>
                    </div>
                </div>
                <div id="three" class="e-panel" data-row="0" data-col="1" data-sizeX="2" data-sizeY="2">
                    <div class="e-panel-container">
                        <div class="text-align">
                            <div>2</div>
                        </div>
                    </div>
                </div>
                <div id="four" class="e-panel" data-row="2" data-col="1" data-sizeX="1" data-sizeY="1">
                    <div class="e-panel-container">
                        <div class="text-align">
                            <div>3</div>
                        </div>
                    </div>
                </div>
                <div id="five" class="e-panel" data-row="2" data-col="2" data-sizeX="2" data-sizeY="1">
                    <div class="e-panel-container">
                        <div class="text-align">
                            <div>4</div>
                        </div>
                    </div>
                </div>
                <div id="six" class="e-panel" data-row="0" data-col="3" data-sizeX="1" data-sizeY="1">
                    <div class="e-panel-container">
                        <div class="text-align">
                            <div>5</div>
                        </div>
                    </div>
                </div>
                <div id="seven" class="e-panel" data-row="1" data-col="3" data-sizeX="1" data-sizeY="1">
                    <div class="e-panel-container">
                        <div class="text-align">
                            <div>6</div>
                        </div>
                    </div>
                </div>
                <div id="eight" class="e-panel" data-row="0" data-col="4" data-sizeX="1" data-sizeY="3">
                    <div class="e-panel-container">
                        <div class="text-align">
                            <div>7</div>
                        </div>
                    </div>
                </div>
            </ejs-dashboardlayout>
            <!-- end of dashboardlayout element -->
        </div>
    </div>
</template>

<script>
import Vue from "vue";
// Import syncfusion dashboardlayout component from layouts package
import { DashboardLayoutPlugin } from "@syncfusion/ej2-vue-layouts";

Vue.use(DashboardLayoutPlugin);

export default {
    data: function() {
        return {
            count: 8,
            spacing: [10,10]
        };
    }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";

/* DashboardLayout element styles  */
#defaultLayout .e-panel .e-panel-container {
    vertical-align: middle;
    font-weight: 600;
    font-size: 20px;
    text-align: center;
}

.text-align {
    line-height: 80px;
}

#defaultLayout .e-panel {
  transition:none !important;
}
</style>

```

{% endtab %}

### Setting the `panels` property using helper

You can render the DashboardLayout component by using the **panels** property through `<e-panels>`.

{% tab template="dashboard-layout/getting-started-panel", isDefaultActive=true %}

```html
<template>
    <div>
        <div class="control-section">
            <!--  DashboardLayout element declaration -->
            <ejs-dashboardlayout id="defaultLayout" :cellSpacing="spacing" :columns="6">
                <e-panels>
                    <e-panel :row="0" :col="0" :sizeX="1" :sizeY="1" content="<div class='panel-content'>0</div>"></e-panel>
                    <e-panel :row="0" :col="1" :sizeX="3" :sizeY="2" content="<div class='panel-content'>1</div>"></e-panel>
                    <e-panel :row="0" :col="4" :sizeX="1" :sizeY="3" content="<div class='panel-content'>2</div>"></e-panel>
                    <e-panel :row="1" :col="0" :sizeX="1" :sizeY="1" content="<div class='panel-content'>3</div>"></e-panel>
                    <e-panel :row="2" :col="0" :sizeX="2" :sizeY="1" content="<div class='panel-content'>4</div>"></e-panel>
                    <e-panel :row="2" :col="2" :sizeX="1" :sizeY="1" content="<div class='panel-content'>5</div>"></e-panel>
                    <e-panel :row="2" :col="3" :sizeX="1" :sizeY="1" content="<div class='panel-content'>6</div>"></e-panel>
                </e-panels>
            </ejs-dashboardlayout>
            <!-- end of dashboardlayout element -->
        </div>
    </div>
</template>

<script>
import Vue from "vue";
// Import syncfusion dashboardlayout component from layouts package
import { DashboardLayoutPlugin } from "@syncfusion/ej2-vue-layouts";

Vue.use(DashboardLayoutPlugin);

export default {
    data: function() {
        return {
            spacing: [10,10]
        };
    }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";

/* DashboardLayout element styles  */
#defaultLayout .e-panel .e-panel-container {
    vertical-align: middle;
    font-weight: 600;
    font-size: 20px;
    text-align: center;
}

.panel-content {
    line-height: 80px;
}

#defaultLayout .e-panel {
  transition:none !important;
}
</style>
```

{% endtab %}

> You can refer to our [Vue Dashboard Layout](https://www.syncfusion.com/vue-ui-components/vue-dashboard-layout) feature tour page for its groundbreaking feature representations. You can also explore our [Vue Dashboard Layout example](https://ej2.syncfusion.com/vue/demos/#/material/dashboard-layout/default.html) to knows how to present and manipulate data.