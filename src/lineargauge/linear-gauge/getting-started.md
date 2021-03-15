---
title: "Getting Started"
component: "LinearGauge"
description: "Getting started in linear gauge component"
---

# Getting Started

This section explains you the steps required to create a simple linear gauge and demonstrate the basic usage of the linear gauge control.

## Dependencies

The list of dependencies required to use the linear gauge component in your application is given below:

```javascript
|-- @syncfusion/ej2-vue-lineargauge
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-vue-base
    |-- @syncfusion/ej2-svg-base
    |-- @syncfusion/ej2-lineargauge
```

## Get Started with Vue CLI

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your Vue applications.
To install Vue CLI use the following command.

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

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.
You can choose the component that you want to install. For this application, we are going to use linear gauge component.

To install linear gauge component, use the following command

```bash
npm install @syncfusion/ej2-vue-lineargauge –save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.
* Vue.use()
* Vue.component()

### Using Vue.use()

Import the Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { LinearGaugePlugin } from '@syncfuion/ej2-vue-lineargauge';

Vue.use(LinearGaugePlugin);
```

> By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the Component and Component Plugin from EJ2 Vue Package,
register the same using the Vue.component() with name of Component from ComponentPlugin
and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { LinearGaugeComponent, LinearGaugePlugin } from '@syncfusion/ej2-vue-lineargauge';

Vue.component(LinearGaugePlugin.name, LinearGaugerComponent);
```

Note: By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Creating Vue Sample

Add the EJ2 Vue linear gauge using `<ejs-lineargauge>` to the `<template>` section of the `App.vue` file in src directory,
the content attribute of the linear gauge component is provided as name in data option in the `<script>` section.

```html
<template>
    <div>
    <div class="col-md-8 control-section">
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge ></ejs-lineargauge>
  </div>
  </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from '@syncfusion/ej2-vue-lineargauge';

Vue.use(LinearGaugePlugin);
export default { }
</script>
```

## Running the Application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

```cmd
npm run dev
```

The below example shows a basic linear gauge component.
{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```html
<template>
    <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge ></ejs-lineargauge>
  </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from '@syncfusion/ej2-vue-lineargauge';

Vue.use(LinearGaugePlugin);
export default { }
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}

## Module Injection

LinearGauge component is segregated into individual feature-wise modules. In order to use a particular feature, you need to inject its feature module using `provide: {}`. For this application,  we are going to use tooltip and annotation feature of the linear gauge. Please find relevant feature module name and description as follows.

* Annotation -  Inject this module to use the annotation features.
* GaugeTooltip - Inject this module to use the tooltip features.

Now import the above mentioned modules from linear gauge package and inject it into the LinearGauge component using `provide: {}` .

```typescript
import { LinearGaugePlugin, Annotations, GaugeTooltip } from "@syncfusion/ej2-vue-lineargauge";
provide: {
    lineargauge: [Annotations, GaugeTooltip]
},

```

## Add Gauge Title

You can add a title using [`title`](../api/linear-gauge/linearGaugeModel/#title-string) property to the linear gauge to provide quick information to the user.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```html
<template>
     <div>
    <div class="content-wrapper">
    <ejs-lineargauge style='display:block' :title ='title' ></ejs-lineargauge>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";

Vue.use(LinearGaugePlugin);
export default {
    data: function () {
        return {
                title: 'linear gauge',
        }
    }
};
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}

## Axis Range

You can set the range to the axis using [`minimum`](../api/linear-gauge/axis/#minimum-number) and [`maximum`](../api/linear-gauge/axis/#maximum-number) properties. The following code example shows how to set the range to the axis in linear gauge control.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <ejs-lineargauge >
    <e-axes>
    <e-axis minimum = 0 maximum = 200 ></e-axis>
    </e-axes>
    </ejs-lineargauge>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";

Vue.use(LinearGaugePlugin);
export default { };

</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}

### To Customize the axis labels

To denote the axis values with temperature units, we can add °C as suffix to each label. This can be achieved by setting the {value}°C to the format property of labelStyle in the axis. Here, {value} acts as a placeholder for each axis label.

You can change the pointer value from the default value of the gauge by settings the [`value`](../api/linear-gauge/pointer/#value-number)  property in pointers option in axis.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```html
<template>
     <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge>
    <e-axes>
    <e-axis minimum = 0 maximum = 200  :ranges='ranges'></e-axis>
    <e-pointers>
           <e-pointer value=140 ></e-pointer>
    </e-pointers>
    </e-axes>
    </ejs-lineargauge>
   </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";

Vue.use(LinearGaugePlugin);
export default {
    data: function () {
        return {
            labelStyle: {
            format: '{value}°C'
        },
            ranges: [{
            start: 0,
            end: 80,
            startWidth:15,
            endWidth:15
        }, {
            start: 80,
            end: 120,
            startWidth:15,
            endWidth:15
        }, {
            start: 120,
            end: 140,
            startWidth:15,
            endWidth:15
        }, {
            start: 140,
            end: 200,
            startWidth:15,
            endWidth:15
        }]
        }
    }
});
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}

## Set Pointer Value

You can change the pointer value using [`value`](../api/linear-gauge/pointer/#value-number) property in [`pointers`](../api/linear-gauge/pointer). The following code example shows how to set the pointer value in linear gauge control.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge>
    <e-axes>
      <e-axis minimum=0 maximum=200>
        <e-pointers>
           <e-pointer value=40 color='green'></e-pointer>
    </e-pointers>
    </e-axis>
    </e-axes>
    </ejs-lineargauge>
   </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";

Vue.use(LinearGaugePlugin);
export default { };
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}