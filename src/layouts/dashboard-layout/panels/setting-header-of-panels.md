---
title: "Header and Content of Panels"
component: "Dashboard Layout"
description: "This section explains how to add header for the panels in Essential JS 2 DashboardLayout component"
---

# Header and content of panels

The dashboard layout component is mostly used to represent the data used for monitoring or managing a process. These data or any HTML template can be placed as the content of a panel using the `content` property. Also, word or phrase that summarize the panel’s content can be added as the header on the top of each panel using the `header` property of the panel.

The following sample demonstrates how to add content for each panel using the header and content properties of the panels.

{% tab template="dashboard-layout/header", isDefaultActive=true %}

```html
<template>
    <div class="col-lg-8 control-section">
        <!--  DashboardLayout element declaration -->
        <ejs-dashboardlayout id="defaultLayout" :cellSpacing="spacing" :columns="7">
            <e-panels>
                <e-panel id="panel0" :row="0" :col="0" :sizeX="1" :sizeY="1" header="<div>Panel 0</div>" content='<div class="content">Panel Content<div>'></e-panel>
                <e-panel id="panel1" :row="0" :col="1" :sizeX="3" :sizeY="2" header="<div>Panel 1</div>" content='<div class="content">Panel Content<div>'></e-panel>
                <e-panel id="panel2" :row="0" :col="4" :sizeX="1" :sizeY="3" header="<div>Panel 2</div>" content='<div class="content">Panel Content<div>'></e-panel>
                <e-panel id="panel3" :row="1" :col="0" :sizeX="1" :sizeY="1" header="<div>Panel 3</div>" content='<div class="content">Panel Content<div>'></e-panel>
                <e-panel id="panel4" :row="2" :col="0" :sizeX="2" :sizeY="1" header="<div>Panel 4</div>" content='<div class="content">Panel Content<div>'></e-panel>
                <e-panel id="panel5" :row="2" :col="2" :sizeX="1" :sizeY="1" header="<div>Panel 5</div>" content='<div class="content">Panel Content<div>'></e-panel>
                <e-panel id="panel6" :row="2" :col="3" :sizeX="1" :sizeY="1" header="<div>Panel 6</div>" content='<div class="content">Panel Content<div>'></e-panel>
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
        spacing: [10,10]
    };
  }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";

/* DashboardLayout element styles  */
#defaultLayout .e-panel .e-panel-container .e-panel-header {
    vertical-align: middle;
    font-weight: 600;
    font-size: 20px;
    text-align:center;
    padding:10px
}

.e-panel-content {
    text-align:center;
    padding:20px;
    line-height:40px;
}

#defaultLayout .e-panel {
  transition:none !important;
}
</style>

```

{% endtab %}

# Placing components as content of panels

In a dashboard, components like the chart, grids, maps, gauge, and more etc. can be used to present a complex data. Such components can be placed as the panel content by assigning the corresponding component element as the `content` of the panel.

The following sample demonstrates how to add EJ2 Chart components as the `content` for each panel in the dashboard layout component.

{% tab template="dashboard-layout/content", isDefaultActive=true %}

```html
<template>
  <div className="control-section" id="control_dash">
    <div className="content-wrapper">
      <!--  DashboardLayout element declaration -->
      <ejs-dashboardlayout ref="DashbordInstance" :columns="6" id='edit_dashboard' :allowResizing="false" :allowDragging="true" >
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