---
title: "Dashboard Layout Template"
component: "Dashboard Layout"
description: "Explains how to customize the dashboard layout using a template that helps to design own user interface in the dashboard layout control."
---

# Template

You can customize the default appearance of the dashboard layout using the `content` property.

The two ways to configure template support in dashboard layout using `content` property are:

* Custom vue template (.vue file)
* Vue.component()

## Custom vue template

The `content` property is used to customize the default appearance of each panel in the dashboard layout. The content of the dashboard layout is displayed as per the template layout provided.

* Define the content in a pietemplate.vue file and create an object `data` in the **data option** of the pietemplate.vue file.

Refer to the following code snippet of pietemplate.vue file.

```html
// pietemplate.vue

<template>
    <div id="app" style='display:block;height:100%; width:100%;'>
        <!--  chart element declaration -->
         <ejs-accumulationchart class="chart-content" ref="accumulationInstance" style='display:block;height:100%; width:100%;' :legendSettings="legendSettings" :tooltip="tooltip">
            <e-accumulation-series-collection>
                <e-accumulation-series :palettes='palettes' :dataSource='seriesData' xName='x' yName='y' innerRadius="40%" :dataLabel="dataLabel"> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries, AccumulationDataLabel, AccumulationTooltip } from "@syncfusion/ej2-vue-charts";
Vue.use(AccumulationChartPlugin);
export default {
  data() {
    return {
      seriesData:  [
        { 'x': 'Jan', y: 12.5, text: 'January' },
        { 'x': 'Feb', y: 25, text: 'February' },
        { 'x': 'Mar', y: 50, text: 'March' },
     ],
     legendSettings: { visible: false },
     dataLabel: { visible: true, position: 'Inside', name: 'value'},
     tooltip: {
        enable: true, header: '<b>${point.x}</b>', format: 'Composition: <b>${point.y}</b>'
     },
     palettes: ['#00bdae', '#357cd2', '#e56691'],
    };
  },
  provide: {
     accumulationchart: [PieSeries, AccumulationDataLabel, AccumulationTooltip]
  },
    mounted(){
    this.$refs.accumulationInstance.height ="100%";
    this.$refs.accumulationInstance.width ="100%";
  }
};
</script>

<style>
  .chart-content{
    height: 100%;
    width:100%;
  }
  #container{
    width: 100%;
    height: 100%;
  }
</style>
```

* Import the `pietemplate.vue` file in the corresponding app.vue file and create a template function, which returns an object

```typescript

import pieTemplate from './pietemplate.vue'

pie: function () {
    return { template : pieTemplate }
},
```

Refer to the following code snippet of App.vue file.

```html
// App.vue

<template>
    <div id="app">
     <!--  dashboard layout element declaration -->
      <ejs-dashboardlayout ref="DashbordInstance" :columns="2" id='edit_dashboard' >
         <e-panels>
                 <!--  template declaration for content property -->
                <e-panel :row="0" :col="1" :sizeX="1" :sizeY="1" header="<div>Pie Chart</div>" :content="pie"></e-panel>
            </e-panels>
    </ejs-dashboardlayout>
    </div>
</template>
<script>
import Vue from 'vue';
// Import syncfusion dashboardlayout component from layouts package
import { DashboardLayoutPlugin } from "@syncfusion/ej2-vue-layouts";
import pieTemplate from "./pietemplate.vue";
import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

Vue.use(DashboardLayoutPlugin);

export default {
       data () {
        return {
             pie: function () {
                return { template : pieTemplate }
            },
        };
     },
}
</script>
```

## Vue component

The pietemplate is initialized with `Vue.component()` where template is provided in the template option.

```typescript

var pietemplate = Vue.component("contentTemp1", {
    template: `
        <div id="app" style='display:block;height:100%; width:100%;'>
            <ejs-accumulationchart class="chart-content" ref="accumulationInstance" style='display:block;height:100%; width:100%;' :legendSettings="legendSettings" :tooltip="tooltip">
                <e-accumulation-series-collection>
                    <e-accumulation-series :palettes='palettes' :dataSource='seriesData' xName='x' yName='y' innerRadius="40%" :dataLabel="dataLabel"> </e-accumulation-series>
                </e-accumulation-series-collection>
            </ejs-accumulationchart>
        </div>`,

    data() {
        return {
            seriesData:  [
                { 'x': 'Jan', y: 12.5, text: 'January' },
                { 'x': 'Feb', y: 25, text: 'February' },
                { 'x': 'Mar', y: 50, text: 'March' },
            ],
            legendSettings: { visible: false },
            dataLabel: { visible: true, position: 'Inside', name: 'value'},
            tooltip: {
                enable: true, header: '<b>${point.x}</b>', format: 'Composition: <b>${point.y}</b>'
            },
            palettes: ['#00bdae', '#357cd2', '#e56691'],
        };
    },
    provide: {
        accumulationchart: [PieSeries, AccumulationDataLabel, AccumulationTooltip]
    },
    mounted(){
        this.$refs.accumulationInstance.height ="100%";
        this.$refs.accumulationInstance.width ="100%";
    }
});
```

* Create a template function which returns an object

```typescript

export default {
    data: function() {
        return {
            pie: function () {
                return { template : pietemplate }
            },
        };
    }
}
```

The following sample demonstrates how to add EJ2 Chart components as the `content` for  panel in the dashboard layout component.

{% tab template="dashboard-layout/template", isDefaultActive=true %}

```html
<template>
  <div className="control-section" id="control_dash">
    <div className="content-wrapper">
      <!--  DashboardLayout element declaration -->
      <ejs-dashboardlayout ref="DashbordInstance" :columns="2" id='edit_dashboard' >
        <e-panels>
          <e-panel :row="0" :col="0" :sizeX="1" :sizeY="1" header="<div>Pie Chart</div>" :content="pie"></e-panel>
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
// Import syncfusion chart component from charts package
import { AccumulationChartPlugin, PieSeries, AccumulationDataLabel, AccumulationTooltip, ChartPlugin, SplineAreaSeries, Legend, DateTime } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);
Vue.use(AccumulationChartPlugin);
Vue.use(DashboardLayoutPlugin);

var pietemplate = Vue.component("contentTemp2", {
  template: `
   <div id="app" style='display:block;height:100%; width:100%;'>
         <ejs-accumulationchart class="chart-content" ref="accumulationInstance" style='display:block;height:100%; width:100%;' :legendSettings="legendSettings" :tooltip="tooltip">
            <e-accumulation-series-collection>
                <e-accumulation-series :palettes='palettes' :dataSource='seriesData' xName='x' yName='y' innerRadius="40%" :dataLabel="dataLabel"> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>`,

  data() {
    return {
        seriesData:  [
          { 'x': 'Jan', y: 12.5, text: 'January' },
          { 'x': 'Feb', y: 25, text: 'February' },
          { 'x': 'Mar', y: 50, text: 'March' },
      ],
      legendSettings: { visible: false },
      dataLabel: { visible: true, position: 'Inside', name: 'value'},
      tooltip: {
          enable: true, header: '<b>${point.x}</b>', format: 'Composition: <b>${point.y}</b>'
      },
      palettes: ['#00bdae', '#357cd2', '#e56691'],
      };
  },
  provide: {
    accumulationchart: [PieSeries, AccumulationDataLabel, AccumulationTooltip]
  },
  mounted(){
    this.$refs.accumulationInstance.height ="100%";
    this.$refs.accumulationInstance.width ="100%";
  }
});

export default {
  data: function() {
    return {
      header:'Add a Content',
      target:'.control-section',
      pie: function () {
        return { template : pietemplate }
      },
    };
  }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";

/* DashboardLayout element styles  */
#dashboard_default .e-panel .e-panel-content {
    vertical-align: middle;
    font-weight: 600;
    font-size: 20px;
    text-align: center;
    line-height: 100px;
}

.chart-content{
    height: 100%;
    width:100%;
}

#container{
    width: 100%;
    height: 100%;
}

#dashboard_default .e-panel {
  transition:none !important;
}
</style>
```

{% endtab %}

> You can refer to our [Vue Dashboard Layout](https://www.syncfusion.com/vue-ui-components/vue-dashboard-layout) feature tour page for its groundbreaking feature representations. You can also explore our [Vue Dashboard Layout example](https://ej2.syncfusion.com/vue/demos/#/material/dashboard-layout/default.html) to knows how to present and manipulate data.