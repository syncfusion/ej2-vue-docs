---
title: "Getting Stared with Vue Bullet Chart | Syncfusion"
component: "Bullet Chart"
description: "Learn here all about Getting Started with Syncfusion Bullet Chart in Vue application using Vue CLI."
---

# Getting Started with Syncfusion Bullet Chart component in Vue 3

This section explains how to use Bullet Chart component in Vue 3 application.

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

## Adding Syncfusion Bullet Chart package in the application

Syncfusion Vue packages are maintained in the [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry. The Bullet Chart component will be used in this example. To install it in the **quickstart** folder use the following command.

```bash
npm install @syncfusion/ej2-vue-charts --save
```

## Adding Syncfusion Bullet Chart component in the application

You have completed all the necessary configurations needed for rendering the Syncfusion Vue component. Now, you are going to add the Bullet Chart component using following steps.

1. Import the Bullet Chart component in the `<script>` section of the `src/App.vue` file.

    ```html
    <script>
    import { BulletChartComponent, BulletTooltip, BulletRangeCollectionDirective, BulletRangeDirective } from "@syncfusion/ej2-vue-charts";
    </script>
    ```

2. Register the Bullet Chart component along with the required child directives which are used in this example. Find the list of child directives and tag names that can be used in the Bullet Chart component in the following table.

    | Directive Name   | Tag Name    |
    |------------------|-------------|
    | `BulletRangeCollectionDirective` | `e-bullet-range-collection` |
    | `BulletRangeDirective`  | `e-bullet-range`  |

    ```js
    import { BulletChartComponent, BulletTooltip, BulletRangeCollectionDirective, BulletRangeDirective } from "@syncfusion/ej2-vue-charts";

    //Component registration.
    export default {
      components: {
        "ejs-bulletchart": BulletChartComponent,
        "e-bullet-range-collection": BulletRangeCollectionDirective,
        "e-bullet-range": BulletRangeDirective
      }
    };
    ```

3. Add the Bullet Chart component definition in template section.

    ```html
    <template>
      <ejs-bulletchart :dataSource="data" :valueField="valueField" :tooltip="tooltip" :targetField="targetField" :height="height"
        :title="title" :minimum="minimum" :maximum="maximum" :interval="interval">
        <e-bullet-range-collection>
          <e-bullet-range end="100" color="red"></e-bullet-range>
          <e-bullet-range end="200" color="blue"></e-bullet-range>
          <e-bullet-range end="300" color="green"></e-bullet-range>
        </e-bullet-range-collection>
      </ejs-bulletchart>
    </template>
    ```

    Above is the Bullet Chart component definition with [`dataSource`](https://ej2.syncfusion.com/vue/documentation/api/bullet-chart/#datasource), [`valueField`](https://ej2.syncfusion.com/vue/documentation/api/bullet-chart/#valuefield), [`tooltip`](https://ej2.syncfusion.com/vue/documentation/api/bullet-chart/#tooltip), [`targetField`](https://ej2.syncfusion.com/vue/documentation/api/bullet-chart/#targetfield), [`height`](https://ej2.syncfusion.com/vue/documentation/api/bullet-chart/#height), [`minimum`](https://ej2.syncfusion.com/vue/documentation/api/bullet-chart/#minimum), [`maximum`](https://ej2.syncfusion.com/vue/documentation/api/bullet-chart/#maximum), [`interval`](https://ej2.syncfusion.com/vue/documentation/api/bullet-chart/#interval) and [`ranges`](https://ej2.syncfusion.com/vue/documentation/api/bullet-chart/#ranges) properties.

4. Declare the bound properties in the `script` section.

    ```js
    export default {
      components: {
        "ejs-bulletchart": BulletChartComponent,
        "e-bullet-range-collection": BulletRangeCollectionDirective,
        "e-bullet-range": BulletRangeDirective
      },
      data() {
        return {
          data: [
            { value: 100, target: 80 },
            { value: 200, target: 180 },
            { value: 300, target: 280 },
            { value: 400, target: 180 },
            { value: 500, target: 230 }
          ],
          minimum: 0,
          maximum: 300,
          interval: 50,
          tooltip: { enable: true },
          title: 'Revenue',
          height: '300px',
          targetField: 'target',
          valueField: 'value'
        };
      },
      provide: {
        bulletChart: [BulletTooltip]
      }
    };
    ```

5. Summarizing the above steps, update the `src/App.vue` file with following code.

    ```html
    <template>
      <ejs-bulletchart :dataSource="data" :valueField="valueField" :tooltip="tooltip" :targetField="targetField" :height="height"
        :title="title" :minimum="minimum" :maximum="maximum" :interval="interval">
        <e-bullet-range-collection>
          <e-bullet-range end="100" color="red"></e-bullet-range>
          <e-bullet-range end="200" color="blue"></e-bullet-range>
          <e-bullet-range end="300" color="green"></e-bullet-range>
        </e-bullet-range-collection>
      </ejs-bulletchart>
    </template>

    <script>

    import { BulletChartComponent, BulletTooltip, BulletRangeCollectionDirective, BulletRangeDirective } from "@syncfusion/ej2-vue-charts";

    export default {
      components: {
        "ejs-bulletchart": BulletChartComponent,
        "e-bullet-range-collection": BulletRangeCollectionDirective,
        "e-bullet-range": BulletRangeDirective
      },
      data() {
        return {
          data: [
            { value: 100, target: 80 },
            { value: 200, target: 180 },
            { value: 300, target: 280 },
            { value: 400, target: 180 },
            { value: 500, target: 230 }
          ],
          minimum: 0,
          maximum: 300,
          interval: 50,
          tooltip: { enable: true },
          title: 'Revenue',
          height: '300px',
          targetField: 'target',
          valueField: 'value'
        };
      },
      provide: {
        bulletChart: [BulletTooltip]
      }
    };
    </script>
    ```

6. Run the application using the following command.

    ```bash
    npm run serve
    ```

The web server will be initiated and open the **quickstart** app in the browser at port [`localhost:8080`](http://localhost:8080/).

![Output](./images/vue3-bullet-chart-demo.png)

Refer the following sample, [vue3-bullet-chart-getting-started](https://github.com/SyncfusionExamples/vue3-bullet-chart-getting-started).