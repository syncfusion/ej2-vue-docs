---
title: "Getting Started with Vue Linear Gauge component | Syncfusion"

component: "Linear Gauge"

description: "Learn here about getting started with Syncfusion Vue Linear Gauge component, its elements, and more."
---

# Getting Started with Vue Linear Gauge

This section explains you the steps required to create a simple Linear Gauge and demonstrate the basic usage of the Linear Gauge control.

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

[`Vue CLI`](https://github.com/vuejs/vue-cli) can be used to setup the Vue applications. To install Vue CLI use the following command.

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

To install Linear Gauge component, use the following command

```bash
npm install @syncfusion/ej2-vue-lineargauge –save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.
* Vue.use()
* Vue.component()

### Using Vue.use()

Import the Linear Gauge Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { LinearGaugePlugin } from '@syncfuion/ej2-vue-lineargauge';

Vue.use(LinearGaugePlugin);
```

> Note: By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the Linear Gauge Component and Plugin from EJ2 Vue Package, register the same using the Vue.component() with Linear Gauge component from LinearGaugePlugin and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { LinearGaugeComponent, LinearGaugePlugin } from '@syncfusion/ej2-vue-lineargauge';

Vue.component(LinearGaugePlugin.name, LinearGaugerComponent);
```

>Note: By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Creating Vue Sample

Add the EJ2 Vue Linear Gauge to the **template** section of the **App.vue** file in src directory using **ejs-lineargauge** tag. The content attribute of the Linear Gauge component is provided as name in the data option of the **script** section.

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

Now run the `npm run dev` command in the console to build the application and open the same in the browser.

```cmd
npm run dev
```

The below example shows a basic Linear Gauge component.

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

LinearGauge component is segregated into the individual feature-wise modules. In order to use a particular feature, inject its feature module using the `provide: {}`. Please find the feature module name and description as follows.

* Annotation -  Inject this module to use the annotation features.
* GaugeTooltip - Inject this module to use the tooltip features.

Now import the above mentioned modules from linear gauge package and inject it into the LinearGauge component using `provide: {}` .

```typescript
import { LinearGaugePlugin, Annotations, GaugeTooltip } from "@syncfusion/ej2-vue-lineargauge";
provide: {
    lineargauge: [Annotations, GaugeTooltip]
},

```

## Adding the Linear Gauge Title

The title can be added to the Linear Gauge component using the [`title`](../api/linear-gauge/linearGaugeModel#title-string) property in the Linear Gauge.

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

The range of the axis can be set using the [`minimum`](../api/linear-gauge/axis#minimum-number) and [`maximum`](../api/linear-gauge/axis#maximum-number) properties in the Linear Gauge.

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

### Customizing the axis labels

To denote the axis labels with temperature units, add the °C as suffix to each label. This can be achieved by setting the **{value}°C** to the [`format`](../api/linear-gauge/labelModel/#format-string) property in the [`labelStyle`](../api/linear-gauge/axis#labelstyle-labelmodel) object of the axis. Here, **{value}** acts as a placeholder for each axis label.

To change the pointer value from the default value of the gauge, set the [`value`](../api/linear-gauge/pointer/#value-number) property in [`pointers`](../api/linear-gauge/pointerModel/) object of the axis.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```html
<template>
    <div>
        <div class="content-wrapper">
            <div align='center'>
                <ejs-lineargauge>
                    <e-axes>
                        <e-axis minimum = 0 maximum = 200  :ranges='ranges'>
                            <e-pointers>
                                <e-pointer value=140 ></e-pointer>
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

The pointer value is changed in the below sample using the [`value`](../api/linear-gauge/pointer/#value-number) property in [`pointers`](../api/linear-gauge/pointer) object of the axis.

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