---
title: "Getting Stared with Vue Range Navigator | Syncfusion"
component: "Range Navigator"
description: "Learn here all about Getting Started with Syncfusion Range Navigator in Vue application using Vue CLI."
---

# Getting Started with Syncfusion Range Navigator component in Vue 3

This section explains how to use Range Navigator component in Vue 3 application.

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

```

Initiating a new project prompts us to choose the type of project to be used for the current application. Select the option `Default (Vue 3 Preview)` from the menu.

![Vue 3 Terminal](./images/vue3-terminal.png)

## Adding Syncfusion Range Navigator package in the application

Syncfusion Vue packages are maintained in the [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry. The Range Navigator component will be used in this example. To install it in the **quickstart** folder use the following command.

```bash
npm install @syncfusion/ej2-vue-charts --save
```

## Adding Syncfusion Range Navigator component in the application

You have completed all the necessary configurations needed for rendering the Syncfusion Vue component. Now, you are going to add the Range Navigator component using following steps.

**1.** Import the Range Navigator component in the `<script>` section of the `src/App.vue` file.

```html
<script>
import { RangeNavigatorComponent, StepLineSeries, DateTime, RangenavigatorSeriesCollectionDirective,
RangenavigatorSeriesDirective } from "@syncfusion/ej2-vue-charts";
</script>
```

**2.** Register the Range Navigator component along with the required child directives which are used in this example. Find the list of child directives and the tag names that can be used in the Range Navigator component in the following table.
  
| Directive Name                            | Tag Name                             |
|-------------------------------------------|--------------------------------------|
| `RangenavigatorSeriesCollectionDirective` | `e-rangenavigator-series-collection` |
| `RangenavigatorSeriesDirective`           | `e-rangenavigator-series`            |

```js
import { RangeNavigatorComponent, StepLineSeries, DateTime, RangenavigatorSeriesCollectionDirective,
RangenavigatorSeriesDirective } from "@syncfusion/ej2-vue-charts";
//Component registeration.
export default {
    name: "App",
    components: {
    "ejs-rangenavigator": RangeNavigatorComponent,
    "e-rangenavigator-series-collection": RangenavigatorSeriesCollectionDirective,
    "e-rangenavigator-series":  RangenavigatorSeriesDirective
  },
};

```

In the above code snippet, you have registered Range Navigator and the directives for series. Series directives are used to visualize the data with different chart types like `Line`, `StepLine` etc.

**3.** Add the component definition in template section.

```html
<template>
      <ejs-rangenavigator :valueType='valueType' :value='value' :labelFormat='labelFormat'>
          <e-rangenavigator-series-collection>
              <e-rangenavigator-series :dataSource='data' type='StepLine' xName='Date' yName='Close' width=2>
              </e-rangenavigator-series>
          </e-rangenavigator-series-collection>
      </ejs-rangenavigator>
</template>

```

Above is the Range Navigator component with `dataSource` bound to series directives.

**4.** Define the collection `data` which is bound for the `dataSource`, `valueType`, `value` and `labelFormat` properties in the `script` section.

```js
  data() {
    return {
     valueType: 'DateTime',
     value: [new Date("2008-01-01"), new Date("2010-01-01")],
     labelFormat: 'MMM-yy',
     data:[
        { Date: new Date("2005-01-01"), Close: 21 },
        { Date: new Date("2006-01-01"), Close: 24 },
        { Date: new Date("2007-01-01"), Close: 36 },
        { Date: new Date("2008-01-01"), Close: 38 },
        { Date: new Date("2009-01-01"), Close: 54 },
        { Date: new Date("2010-01-01"), Close: 57 },
        { Date: new Date("2011-01-01"), Close: 62 },
      ],
    };
  },

```

**5.** Summarizing the above steps, update the `src/App.vue` file with following code.

```html
<template>
      <ejs-rangenavigator :valueType='valueType' :value='value' :labelFormat='labelFormat'>
          <e-rangenavigator-series-collection>
              <e-rangenavigator-series :dataSource='data' type='StepLine' xName='Date' yName='Close' width=2>
              </e-rangenavigator-series>
          </e-rangenavigator-series-collection>
      </ejs-rangenavigator>
</template>

<script>
import { RangeNavigatorComponent, StepLineSeries, DateTime, RangenavigatorSeriesCollectionDirective,
RangenavigatorSeriesDirective } from "@syncfusion/ej2-vue-charts";

export default {
    name: "App",
    components: {
    "ejs-rangenavigator": RangeNavigatorComponent,
    "e-rangenavigator-series-collection": RangenavigatorSeriesCollectionDirective,
    "e-rangenavigator-series":  RangenavigatorSeriesDirective
  },
  data() {
    return {
     valueType: 'DateTime',
     value: [new Date("2008-01-01"), new Date("2010-01-01")],
     labelFormat: 'MMM-yy',
     data:[
        { Date: new Date("2005-01-01"), Close: 21 },
        { Date: new Date("2006-01-01"), Close: 24 },
        { Date: new Date("2007-01-01"), Close: 36 },
        { Date: new Date("2008-01-01"), Close: 38 },
        { Date: new Date("2009-01-01"), Close: 54 },
        { Date: new Date("2010-01-01"), Close: 57 },
        { Date: new Date("2011-01-01"), Close: 62 },
      ],
    };
  },
  provide: {
    rangeNavigator: [ DateTime, StepLineSeries ],
  },
};
</script>

```

**6.** Run the application using the following command.

```bash
npm run serve
```

The web server will be initiated and open the **quickstart** app in the browser at port [`localhost:8080`](http://localhost:8080/).

![Output](./images/vue3-RN-demo.png)

Refer the following sample, [vue3-range-navigator-getting-started](https://github.com/SyncfusionExamples/vue3-range-navigator-getting-started).
