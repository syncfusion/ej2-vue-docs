---
title: "Moving of panels programatically"
component: "Dashboard Layout"
description: "This section explains how to move the panels programatically within the layout in Essential JS 2 Dashboard Layout component"
---

# Moving of panels programatically

Other than drag and drop, it is possible to move the panels in Dashboard Layout programatically. This can be achieved using [movePanel](https://ej2.syncfusion.com/vue/documentation/api/dashboard-layout/#movepanel) method. The method is invoked as follows,

```js
movePanel(id, row, col)

```

Where,
* id - ID of the panel which needs to be moved.
* row - New row position for moving the panel.
* col - New column position for moving the panel.

Each time a panel's position is changed(Programatically or through UI interaction), the Dashboard Layout's [change](https://ej2.syncfusion.com/vue/documentation/api/dashboard-layout/#change) event will be triggered.

The following sample demonstrates moving a panel programatically to a new position in the Dashboard Layout's [created](https://ej2.syncfusion.com/vue/documentation/api/dashboard-layout/#created) event.

{% tab template="dashboard-layout/moving", isDefaultActive=true %}

```html
<template>
    <div class="control-section">
        <!--  DashboardLayout element declaration -->
        <ejs-dashboardlayout id='dashboard_layout'  ref="dashboard"  :columns="5" :cellSpacing='cellSpacing' :created="onCreated" :change="onChange" >
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
        onCreated: function(args) {
           // movePanel("id", row, col)
            this.$refs.dashboard.$el.ej2_instances[0].movePanel("layout_0",1,0);
        },
        //Dashboard Layout's change event function
        onChange: function(args) {
          console.log("Change event Triggered");
        },
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

> You can refer to our [Vue Dashboard Layout](https://www.syncfusion.com/vue-ui-components/vue-dashboard-layout) feature tour page for its groundbreaking feature representations. You can also explore our [Vue Dashboard Layout example](https://ej2.syncfusion.com/vue/demos/#/material/dashboard-layout/default.html) to knows how to present and manipulate data.