---
title: "Resizing panels"
component: "Dashboard Layout"
description: "This section explains how to enable resizing and the dynamic resizing of panels within the layout in Essential JS 2 DashboardLayout component"
---

# Resizing panels

The Dashboard Layout component is also provided with the panel resizing functionality which can be enabled or disabled using the [`allowResizing`](https://ej2.syncfusion.com/vue/documentation/api/dashboard-layout/#allowresizing) property. This functionality allows you to resize the panels dynamically through UI interactions using the resizing handlers which controls the panel resizing in various directions.

Initially, the panels can be resized only in south-east direction. However, panels can also be resized in east, west, north, south and south-west directions by defining the required directions with the [`resizableHandles`](https://ej2.syncfusion.com/vue/documentation/api/dashboard-layout/#resizablehandles) property.

On resizing a panel in Dashboard layout the following events will be triggered,
* [resizeStart](https://ej2.syncfusion.com/vue/documentation/api/dashboard-layout/#resizestart) - Triggers when panel resize starts
* [resize](https://ej2.syncfusion.com/vue/documentation/api/dashboard-layout/#resize) - Triggers when panel is being resized
* [resizeStop](https://ej2.syncfusion.com/vue/documentation/api/dashboard-layout/#resizestop) - Triggers when panel resize stops

The following sample demonstrates how to enable and disable the resizing of panels in the Dashboard Layout component in different directions.

{% tab template="dashboard-layout/resizing", isDefaultActive=true %}

```html
<template>
  <div class="control-section">
    <!--  DashboardLayout element declaration -->
    <ejs-dashboardlayout id='dashboard_default' ref="dashboard" :cellSpacing='cellSpacing' :allowResizing='true' :resizableHandles='resizableHandles' :columns="6" :resizeStart="onResizeStart" :resize="onResize" :resizeStop="onResizeStop">
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
      cellSpacing: [10, 10],
      resizableHandles: ['e-south-east','e-east','e-west','e-north','e-south'],
    };
  },
  methods: {
      //Dashboard Layout's resizestart event function
      onResizeStart: function(args) {
        console.log("Resize Start");
      },
     //Dashboard Layout's resize event function
      onResize: function(args) {
        console.log("Resizing");
      },
      //Dashboard Layout's resizestop event function
      onResizeStop: function(args) {
        console.log("Resize Stop")
      }
  }
}
</script>

<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";

/* DashboardLayout element styles  */
#dashboard_default .e-panel .e-panel-container .content {
  vertical-align: middle;
  font-weight: 600;
  font-size: 20px;
  text-align: center;
  line-height: 80px;
}

#dashboard_default .e-panel {
  transition:none !important;
}
</style>

```

{% endtab %}

# Resizing panels programatically

The Dashboard Layout panels can also be resized programatically by using [resizePanel](https://ej2.syncfusion.com/vue/documentation/api/dashboard-layout/#resizepanel) method. The method is invoked as follows,

```js
resizePanel(id, sizeX, sizeY)

```

Where,
* id - ID of the panel which needs to be resized.
* sizeX - New panel width in cells count for resizing the panel.
* sizeY - New panel height in cells count for resizing the panel.

The following sample demonstrates resizing panels programatically in the Dashboard Layout's [created](https://ej2.syncfusion.com/vue/documentation/api/dashboard-layout/#created) event.

{% tab template="dashboard-layout/resize-panel", isDefaultActive=true %}

```html
<template>
  <div class="control-section">
    <!--  DashboardLayout element declaration -->
    <ejs-dashboardlayout id='dashboard_default' ref="dashboard" :cellSpacing='cellSpacing' :columns="5" :created="onCreated" >
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
      cellSpacing: [10, 10]
    };
  },
  methods: {
      //Dashboard Layout's create event function
      onCreated: function(args) {
        // resizePanel("id", sizeX, sizeY)
        this.$refs.dashboard.$el.ej2_instances[0].resizePanel("layout_4", 1, 1);
        this.$refs.dashboard.$el.ej2_instances[0].resizePanel("layout_5", 2, 1);
      },
  }
}
</script>

<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";

/* DashboardLayout element styles  */
#dashboard_default .e-panel .e-panel-container .content {
  vertical-align: middle;
  font-weight: 600;
  font-size: 20px;
  text-align: center;
  line-height: 80px;
}

#dashboard_default .e-panel {
  transition:none !important;
}
</style>

```

{% endtab %}

> You can refer to our [Vue Dashboard Layout](https://www.syncfusion.com/vue-ui-components/vue-dashboard-layout) feature tour page for its groundbreaking feature representations. You can also explore our [Vue Dashboard Layout example](https://ej2.syncfusion.com/vue/demos/#/material/dashboard-layout/default.html) to knows how to present and manipulate data.