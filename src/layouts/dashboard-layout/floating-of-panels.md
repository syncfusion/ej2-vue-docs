---
title: "Floating"
component: "Dashboard Layout"
description: "This section explains the floating functionality of Essential JS 2 DashboardLayout component"
---

# Floating panels

The floating functionality of the component allows you to effectively use the entire layout for the panel's placement. If the floating functionality is enabled, the panels within the layout get floated upwards automatically to occupy the empty cells available in previous rows. This functionality can be enabled or disabled using the [`allowFloating`](../api/dashboard-layout/#allowfloating) property of the component.

The following sample demonstrates how to enable or disable the floating of panels in the Dashboard Layout component.

{% tab template="dashboard-layout/floating", isDefaultActive=true %}

```html
<template>
    <div>
        <div>
            <!--  Button element declaration -->
                <ejs-button id="toggle" ref="toggle" class="e-flat e-primary e-outline" :isToggle="true" v-on:click.native="onChange" >Enable Floating</ejs-button>
            <!-- end of button element -->
        </div>
        <div  id="control_dash">
            <!--  DashboardLayout element declaration -->
            <ejs-dashboardlayout id='dashboard_default' ref="dashboard" :allowFloating="false" :cellSpacing='cellSpacing' :columns="6">
                <e-panels>
                    <e-panel :sizeX="2" :sizeY="2" :row="1" :col="0" content="<div class='content'>0</div>"></e-panel>
                    <e-panel :sizeX="2" :sizeY="2" :row="2" :col="2" content="<div class='content'>1</div>"></e-panel>
                    <e-panel :sizeX="2" :sizeY="2" :row="3" :col="4" content="<div class='content'>2</div>"></e-panel>
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
// Import syncfusion button component from buttons package
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";

Vue.use(DashboardLayoutPlugin);
Vue.use(ButtonPlugin);

export default {
    data: function() {
        return {
            cellSpacing: [10, 10],
            resetPanels:[],
        };
    },
    methods: {
        onChange: function(args) {
            if (this.$refs.toggle.content == "Disable Floating and Reset") {
                this.$refs.toggle.content = 'Enable Floating';
                this.$refs.dashboard.allowFloating = false;
                this.$refs.dashboard.panels = this.resetPanels;
            } else {
                this.$refs.toggle.content = 'Disable Floating and Reset';
                this.$refs.dashboard.allowFloating = true;
            }
        }
    },
    mounted() {
        this.resetPanels = this.$refs.dashboard.serialize();
        this.resetPanels[0].content = '<div class="content">0</div>';
        this.resetPanels[1].content = '<div class="content">1</div>';
        this.resetPanels[2].content = '<div class="content">2</div>';
    }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";

#dashboard_default .e-panel .e-panel-content {
    vertical-align: middle;
    font-weight: 600;
    font-size: 20px;
    text-align: center;
    line-height: 100px;
}

#control_dash {
    display: block;
    width: 60%;
    float: left;
    padding-top: 30px;
}

#dashboard_default .e-panel {
  transition:none !important;
}
</style>

```

{% endtab %}
