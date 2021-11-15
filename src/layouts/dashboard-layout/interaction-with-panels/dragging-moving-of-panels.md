---
title: "Dragging and moving of panels"
component: "Dashboard Layout"
description: "This section explains how to adjust the panels within the layout in Essential JS 2 Dashboard Layout component"
---

# Drag and Drop

The Dashboard Layout component is provided with dragging functionality to drag and reorder the panels within the layout. While dragging a panel, a holder will be highlighted below the panel indicating the panel placement on panel drop. This helps the user to decide whether to place the panel in the current position or revert to previous position without disturbing the layout.

If one or more panels collide while dragging, then the colliding panels will be pushed towards the left or right or top or bottom direction where an adaptive space for the collided panel is available. The position changes of these collided panels will be updated dynamically during dragging of a panel, so the user can conclude whether to place the panel in the current position or not.

While dragging a panel in Dashboard layout the following dragging events will be triggered,
* [dragStart](https://ej2.syncfusion.com/vue/documentation/api/dashboard-layout/#dragstart) - Triggers when panel drag starts
* [drag](https://ej2.syncfusion.com/vue/documentation/api/dashboard-layout/#drag) - Triggers when panel is being dragged
* [dragStop](https://ej2.syncfusion.com/vue/documentation/api/dashboard-layout/#dragstop) - Triggers when panel drag stops

The following sample demonstrates dragging and pushing of panels. For example, while dragging the panel 0 over panel 1, these panels get collided and push the panel 1 towards the feasible direction, so that, the panel 0 gets placed in the panel 1 position.

{% tab template="dashboard-layout/setting-cell-spacing", isDefaultActive=true %}

```html
<template>
    <div class="control-section">
        <!--  DashboardLayout element declaration -->
        <ejs-dashboardlayout id='dashboard_layout'  :columns="7" :cellSpacing='cellSpacing' :dragStart="onDragStart" :drag="onDrag" :dragStop="onDragStop" >
            <e-panels>
                <e-panel :sizeX="1" :sizeY="1" :row="0" :col="0" content="<div class='content'>0</div>"></e-panel>
                <e-panel :sizeX="3" :sizeY="2" :row="0" :col="1" content="<div class='content'>1</div>"></e-panel>
                <e-panel :sizeX="1" :sizeY="3" :row="0" :col="4" content="<div class='content'>2</div>"></e-panel>
                <e-panel :sizeX="1" :sizeY="1" :row="1" :col="0" content="<div class='content'>3</div>"></e-panel>
                <e-panel :sizeX="2" :sizeY="1" :row="2" :col="0" content="<div class='content'>4</div>"></e-panel>
                <e-panel :sizeX="1" :sizeY="1" :row="2" :col="2" content="<div class='content'>5</div>"></e-panel>  
                <e-panel :sizeX="1" :sizeY="1" :row="2" :col="3" content="<div class='content'>6</div>"></e-panel>  
            </e-panels>
        </ejs-dashboardlayout>
        <!-- end of dashboardlayout element -->
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
            cellSpacing: [20, 20]
        };
    },
     methods: {
        onDragStart: function(args) {
           console.log("Drag start");
        },

        onDrag: function(args) {
          console.log("Dragging");
        },

        onDragStop: function(args) {
          console.log("Drag Stop");
        }
     }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";

/* DashboardLayout element styles  */
#dashboard_layout .e-panel .e-panel-content {
    vertical-align: middle;
    font-weight: 600;
    font-size: 20px;
    text-align: center;
    line-height: 80px;
}

#dashboard_layout .e-panel {
  transition:none !important;
}
</style>

```

{% endtab %}

# Customizing the dragging handler

Initially, the complete panel will act as the handler for dragging the panel such that the dragging action occurs on clicking anywhere over a panel. However, this dragging handler for the panels can be customized using the [`draggableHandle`](https://ej2.syncfusion.com/vue/documentation/api/dashboard-layout/#draggablehandle) property to restrict the dragging action within a particular element in the panel.

The following sample demonstrates customizing the dragging handler of the panels where the dragging action of panel occurs only with the header of the panel.

{% tab template="dashboard-layout/drag-handler", isDefaultActive=true %}

```html
<template>
  <div className="control-section" id="control_dash">
    <div className="content-wrapper">
      <!--  DashboardLayout element declaration -->
      <ejs-dashboardlayout ref="DashbordInstance" :columns="6" id='edit_dashboard' :allowResizing="false" :allowDragging="true" :draggableHandle="draggable" >
        <e-panels>
          <e-panel :row="0" :col="0" :sizeX="3" :sizeY="2" header="<div>Product usage ratio</div>" :content="pie"></e-panel>
          <e-panel :row="0" :col="3" :sizeX="3" :sizeY="2" header="<div>Mobile browsers usage</div>" :content="pie1"></e-panel>
          <e-panel :row="1" :col="0" :sizeX="3" :sizeY="2" header="<div>Spline Chart</div>" :content="spline"></e-panel>
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

var splineTemplate = Vue.component("contentTemp1", {
  template: `
    <div id="container" style='display:block;height:100%, width:100%;'>
      <!--  Chart element declaration -->
      <ejs-chart class="chart-content" ref="splineInstance" style='display:block;height:100%, width:100%;':primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'
      :chartArea='chartArea' :height='height' :width='width' :border='border'>
        <e-series-collection>
          <e-series :dataSource='seriesData' type='SplineArea' xName='x' yName='y' name='Jan' width=2 opacity=0.5 :fill="fill0"></e-series>
          <e-series :dataSource='seriesData1' type='SplineArea' xName='x' yName='y' name='Feb' width=2 opacity=0.5 :fill="fill1"></e-series>
        </e-series-collection>
      </ejs-chart>
    <!-- end of chart element -->
  </div>`,

  data: function() {
    return {
      seriesData: [
        { x: new Date(2002, 0, 1), y: 2.2 }, { x: new Date(2003, 0, 1), y: 3.4 },
        { x: new Date(2004, 0, 1), y: 2.8 }, { x: new Date(2005, 0, 1), y: 1.6 },
        { x: new Date(2006, 0, 1), y: 2.3 }, { x: new Date(2007, 0, 1), y: 2.5 },
        { x: new Date(2008, 0, 1), y: 2.9 }, { x: new Date(2009, 0, 1), y: 3.8 },
        { x: new Date(2010, 0, 1), y: 1.4 }, { x: new Date(2011, 0, 1), y: 3.1 }
      ],
      seriesData1: [
        { x: new Date(2002, 0, 1), y: 2 }, { x: new Date(2003, 0, 1), y: 1.7 },
        { x: new Date(2004, 0, 1), y: 1.8 }, { x: new Date(2005, 0, 1), y: 2.1 },
        { x: new Date(2006, 0, 1), y: 2.3 }, { x: new Date(2007, 0, 1), y: 1.6 },
        { x: new Date(2008, 0, 1), y: 1.5 }, { x: new Date(2009, 0, 1), y: 2.7 },
        { x: new Date(2010, 0, 1), y: 1.5 }, { x: new Date(2011, 0, 1), y: 2.2 }
      ],
      //Initializing Primary X Axis
      primaryXAxis: {
        valueType: 'DateTime',
        labelFormat: 'y',
        majorGridLines: { width: 0 },
        intervalType: 'Years',
        edgeLabelPlacement: 'Shift'
      },
      //Initializing Primary Y Axis
      primaryYAxis: {
        labelFormat: '{value}%',
        lineStyle: { width: 0 },
        majorTickLines: { width: 0 },
        minorTickLines: { width: 0 }
      },
      chartArea: {
        border: {
          width: 0
        }
      },
      border: {
        color: 'transparent'
      },
      width :"100%",
      fill1: 'rgb(0, 189, 174)',
      fill0: 'rgb(239, 183, 202)',
      height: "99%"
    };
  },
  provide: {
    chart: [SplineAreaSeries, Legend, DateTime]
  },
  mounted(){
    this.$refs.splineInstance.height ="100%";
    this.$refs.splineInstance.width ="100%";
  }
});

var pietemplate = Vue.component("contentTemp2", {
  template: `
    <div id="app" style='display:block;height:100%; width:100%;'>
      <ejs-accumulationchart class="chart-content" ref="accumulationInstance" style='display:block;height:100%; width:100%;' :legendSettings="legendSettings" :tooltip="tooltip">
        <e-accumulation-series-collection>
          <e-accumulation-series :dataSource='seriesData' xName='x' yName='y' innerRadius="40%" :dataLabel="dataLabel"> </e-accumulation-series>
        </e-accumulation-series-collection>
      </ejs-accumulationchart>
    </div>`,

  data() {
    return {
      seriesData:  [
            { x: 'TypeScript', y: 13, text: 'TS 13%' },
            { x: 'React', y: 12.5, text: 'Reat 12.5%' },
            { x: 'MVC', y: 12, text: 'MVC 12%' },
            { x: 'Core', y: 12.5, text: 'Core 12.5%' },
            { x: 'Vue', y: 10, text: 'Vue 10%' },
            { x: 'Angular', y: 40, text: 'Angular 40%' }
      ],
      legendSettings: { visible: false },
      dataLabel: { visible: true, position: 'Inside', name: 'value'},
      tooltip: {
        enable: true, header: '<b>${point.x}</b>', format: 'Composition: <b>${point.y}</b>'
      },
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

var pietemplate1 = Vue.component("contentTemp3", {
  template: `
    <div id="app1" style='display:block;height:100%; width:100%;'>
      <ejs-accumulationchart class="chart-content" ref="accumulationInstance" style='display:block;height:100%; width:100%;' :legendSettings="legendSettings" :tooltip="tooltip">
        <e-accumulation-series-collection>
          <e-accumulation-series  :dataSource='seriesData' xName='x' yName='y' innerRadius="40%" :dataLabel="dataLabel"> </e-accumulation-series>
        </e-accumulation-series-collection>
      </ejs-accumulationchart>
    </div>`,

  data() {
    return {
      seriesData:  [
          { 'x': 'Chrome', y: 37, text: '37%' },
          { 'x': 'UC Browser', y: 17, text: '17%' },
          { 'x': 'iPhone', y: 19, text: '19%' },
          { 'x': 'Others', y: 4, text: '4%' },
          { 'x': 'Opera', y: 11, text: '11%' },
          { 'x': 'Android', y: 12, text: '12%' }
    ],
      legendSettings: { visible: false },
      dataLabel: { visible: true, position: 'Inside', name: 'value'},
      tooltip: {
        enable: true, header: '<b>${point.x}</b>', format: 'Composition: <b>${point.y}</b>'
      },
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
      spacing: [10,10],
      header:'Add a Content',
      target:'.control-section',
      draggable:'.e-panel-header',
      showCloseIcon: true,
      spline: function () {
        return { template : splineTemplate }
      },
      pie: function () {
        return { template : pietemplate }
      },
      pie1: function () {
        return { template: pietemplate1}
      }
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

By default, the dragging of panels is enabled in Dashboard Layout. It can also be disabled with the help of [allowDragging](https://ej2.syncfusion.com/vue/documentation/api/dashboard-layout/#allowdragging) API. Setting [allowDragging](https://ej2.syncfusion.com/vue/documentation/api/dashboard-layout/#allowdragging) to false disables the dragging functionality in Dashboard Layout.

The following sample demonstrates Dashboard Layout with dragging support disabled.

{% tab template="dashboard-layout/disable-dragging", isDefaultActive=true %}

```html
<template>
    <div class="control-section">
        <!--  DashboardLayout element declaration -->
        <ejs-dashboardlayout id='dashboard_layout'  :columns="5" :cellSpacing='cellSpacing' :allowDragging ='allowDragging' >
            <e-panels>
                <e-panel :sizeX="1" :sizeY="1" :row="0" :col="0" content="<div class='content'>0</div>"></e-panel>
                <e-panel :sizeX="3" :sizeY="2" :row="0" :col="1" content="<div class='content'>1</div>"></e-panel>
                <e-panel :sizeX="1" :sizeY="3" :row="0" :col="4" content="<div class='content'>2</div>"></e-panel>
                <e-panel :sizeX="1" :sizeY="1" :row="1" :col="0" content="<div class='content'>3</div>"></e-panel>
                <e-panel :sizeX="2" :sizeY="1" :row="2" :col="0" content="<div class='content'>4</div>"></e-panel>
                <e-panel :sizeX="1" :sizeY="1" :row="2" :col="2" content="<div class='content'>5</div>"></e-panel>  
                <e-panel :sizeX="1" :sizeY="1" :row="2" :col="3" content="<div class='content'>6</div>"></e-panel>  
            </e-panels>
        </ejs-dashboardlayout>
        <!-- end of dashboardlayout element -->
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
            cellSpacing: [20, 20],
            allowDragging: false
        };
    },
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";

/* DashboardLayout element styles  */
#dashboard_layout .e-panel .e-panel-content {
    vertical-align: middle;
    font-weight: 600;
    font-size: 20px;
    text-align: center;
    line-height: 80px;
}

#dashboard_layout .e-panel {
  transition:none !important;
}
</style>

```

{% endtab %}

> You can refer to our [Vue Dashboard Layout](https://www.syncfusion.com/vue-ui-components/vue-dashboard-layout) feature tour page for its groundbreaking feature representations. You can also explore our [Vue Dashboard Layout example](https://ej2.syncfusion.com/vue/demos/#/material/dashboard-layout/default.html) to knows how to present and manipulate data.