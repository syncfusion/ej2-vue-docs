---
title: Responsive Dashboard"
component: "Dashboard Layout"
description: "This section explains about responsiveness and adaptivity of Essential JS 2 Dashboard Layout component"
---

# Responsive and adaptive layout

The control is provided with built-in responsive support, where panels within the layout get adjusted based on their parent element's dimensions to accommodate any resolution which relieves the burden of building responsive dashboards.

The dashboard layout is designed to automatically adapt with lower resolutions by transforming the entire layout into a stacked one, so that, the panels will be displayed in a vertical column. By default, whenever the screen resolution meets 600 px or lower resolutions this layout transformation occurs. This transformation can be modified for any user defined resolution by defining the for the [`mediaQuery`](../api/dashboard-layout/#mediaquery) property of the component.

The following sample demonstrates the usage of the [`mediaQuery`](../api/dashboard-layout/#mediaquery) property to turn out the layout into a stacked one in user defined resolution. Here, whenever, the window size reaches 700 px or lesser, the layout becomes a stacked layout.

{% tab template="dashboard-layout/responsive-adaptive", isDefaultActive=true %}

```html
<template>
    <div className="control-section">
        <!--  DashboardLayout element declaration -->
        <ejs-dashboardlayout id='dashboard_layout' ref="dashboard" :cellSpacing='cellSpacing' :mediaQuery='mediaQuery' :columns="6">
            <e-panels>
                <e-panel :sizeX="1" :sizeY="1" :row="0" :col="0" content="<div>0</div>"></e-panel>
                <e-panel :sizeX="2" :sizeY="2" :row="0" :col="1" content="<div>1</div>"></e-panel>
                <e-panel :sizeX="1" :sizeY="3" :row="0" :col="4" content="<div>2</div>"></e-panel>
                <e-panel :sizeX="1" :sizeY="1" :row="1" :col="0" content="<div>3</div>"></e-panel>
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
            mediaQuery:'max-width: 700px',
        };
    }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";

/* DashboardLayout element styles  */
#dashboard_layout .e-panel .e-panel-container {
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