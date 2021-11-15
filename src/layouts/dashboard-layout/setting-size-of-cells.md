---
title: "Setting size of cells"
component: "DashboardLayout"
description: "This section explains how to adjust the size of the cells of Essential JS 2 DashboardLayout component"
---

# Configuring the layout

The entire layout dimensions are assigned based on the height and width of the parent element. Hence, a responsive or static layout can be created by assigning a percentage or static dimension values to the parent element. The layout adapts to mobile resolutions by transforming the entire layout into a stacked orientation, so that, the panels will be displayed in a vertical column.

The **Dashboard Layout** is a grid structured component which can be split into subsections of equal size known as cells. The total number of cells in each row is defined by using the [`columns`](../api/dashboard-layout/#columns) property of the component. The width of each cell will be auto calculated based on the total number of cells placed in a row and the height of a cell will be same as that of its width. However, the height of these cells can also be configured to any desired size using the [`cellAspectRatio`](../api/dashboard-layout/#cellaspectratio) property (cellwidth/cellheight ratio) which defines the cell width to height ratio.

The number of rows within the layout has no limits and can have any number of rows based on the panels count and position. Panels which acts as data containers will be placed or positioned over these cells.

## Modifying cell size

In a dashboard, the data to be held by the panel in a cell may be of different size, hence different cell dimensions may be required in different scenarios. In this case, the size of these grid cells can be modified to the required size using the [`columns`](../api/dashboard-layout/#columns) and [`cellAspectRatio`](../api/dashboard-layout/#cellAspectRatio) properties.

The following sample demonstrates how to modify a cell size using the [`columns`](../api/dashboard-layout/#columns) and [`cellAspectRatio`](../api/dashboard-layout/#cellaspectratio) properties. In the following sample the width of the parent element is divided into 5 equal cells based on the columns property value resulting the width of each cell as 100 px. The height of these cells will be 50 px based on the cellAspectRatio value 100/50 (i.e. for every 100 px of width, 50 px will be the height of the cell).

{% tab template="dashboard-layout/modifying-cell-size", isDefaultActive=true %}

```html
<template>
    <div class="control-section">
        <!--  DashboardLayout element declaration -->
        <ejs-dashboardlayout id='dashboard_layout'  :columns="5" :cellSpacing='cellSpacing' :cellAspectRatio='cellAspectRatio'>
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
            cellAspectRatio: 100/50,
        };
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
    line-height: 60px;
}

#dashboard_layout .e-panel {
  transition:none !important;
}
</style>

```

{% endtab %}

## Setting cell spacing

The spacing between each panel in a row and column can be defined using the [`cellSpacing`](../api/dashboard-layout/#cellspacing) property. Adding spacing between the panels will make the layout effective and provides a clear data representation.

The following sample demonstrates the usage of the [`cellSpacing`](../api/dashboard-layout/#cellspacing) property which helps in a neat and clear representation of a data.

{% tab template="dashboard-layout/setting-cell-spacing", isDefaultActive=true %}

```html
<template>
    <div class="control-section">
        <!--  DashboardLayout element declaration -->
        <ejs-dashboardlayout id='dashboard_layout'  :columns="5" :cellSpacing='cellSpacing' >
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
    line-height: 100px;
}

#dashboard_layout .e-panel {
  transition:none !important;
}
</style>

```

{% endtab %}

## Graphical representation of layout

These cells combinedly forms a grid-structured layout which will be hidden initially. This grid structured layout can be made visible by enabling the [`showGridLines`](../api/dashboard-layout/#showgridlines) property, which clearly pictures the cells split-up within the layout. These gridlines will be helpful in panels sizing and placement within the layout during initial designing of a dashboard.

In the following sample, the grid lines indicate the cells split-up of the layout and the data containers placed over these cells are known as panels.

{% tab template="dashboard-layout/graphical-layout", isDefaultActive=true %}

```html
<template>
    <div class="control-section">
        <!--  DashboardLayout element declaration -->
        <ejs-dashboardlayout id='dashboard_layout' :cellSpacing='cellSpacing' :showGridLines='showGridLines' :columns="5">
            <e-panels>
                <e-panel :sizeX="3" :sizeY="2" :row="0" :col="1" content="<div class='content'>1</div>"></e-panel>
                <e-panel :sizeX="1" :sizeY="3" :row="0" :col="4" content="<div class='content'>2</div>"></e-panel>
                <e-panel :sizeX="1" :sizeY="1" :row="2" :col="2" content="<div class='content'>3</div>"></e-panel>
                <e-panel :sizeX="1" :sizeY="1" :row="2" :col="3" content="<div class='content'>4</div>"></e-panel>  
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
            showGridLines: true,
        };
    }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";

/* DashboardLayout element styles  */
#dashboard_layout .e-panel .e-panel-container .content {
    vertical-align: middle;
    font-weight: 600;
    font-size: 20px;
    text-align: center;
    line-height: 100px;
}

#dashboard_layout .e-panel {
  transition:none !important;
}
</style>

```

{% endtab %}

## Rendering component in right-to-left direction

It is possible to render the Dashboard Layout in right-to-left direction by setting the [enableRtl](../api/dashboard-layout/#enablertl) API to true.

The following sample demonstrates Dashboard Layout in right-to-left direction.

{% tab template="dashboard-layout/rtl", isDefaultActive=true %}

```html
<template>
    <div class="col-lg-8 control-section">
        <!--  DashboardLayout element declaration -->
        <ejs-dashboardlayout id="defaultLayout" :cellSpacing="spacing" :columns="5" :enableRtl="enableRtl">
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
            spacing: [10,10],
            enableRtl: true
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
    padding:10px
}

.e-panel-content {
    padding:20px;
}

#defaultLayout .e-panel {
  transition:none !important;
}
</style>

```

{% endtab %}

> You can refer to our [Vue Dashboard Layout](https://www.syncfusion.com/vue-ui-components/vue-dashboard-layout) feature tour page for its groundbreaking feature representations. You can also explore our [Vue Dashboard Layout example](https://ej2.syncfusion.com/vue/demos/#/material/dashboard-layout/default.html) to knows how to present and manipulate data.