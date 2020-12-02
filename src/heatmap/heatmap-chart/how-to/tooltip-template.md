---
title: " HeatMap How To | Vue "

component: "HeatMap Chart"

description: "The How to section explains knowledge base samples and how to access different types of properties and events of the HeatMap."
---

# Customizing tooltip as a table

You can show a tooltip as a table using the `template` property in `tooltipSettings`.

The following steps describe how to show the table tooltip.

**Step 1**:

Initialize the tooltip template div as shown in the following html page.

**Step 2**:

Set the element id to the `template` property in `tooltipSettings` to show the tooltip template.

{% tab template="heatmap-chart/how-to" %}

```html

<template>
    <div id="app">
        <ejs-heatmap id="heatmap" :titleSettings='titleSettings' :xAxis='xAxis' :yAxis='yAxis' :dataSource='dataSource' :cellSettings='cellSettings' :showTooltip='showTooltip' :tooltipSettings='tooltipSettings' ></ejs-heatmap>
    </div>
</template>
<script>
import Vue from 'vue';
import { HeatMapPlugin, Tooltip, Legend } from '@syncfusion/ej2-vue-heatmap';
Vue.use(HeatMapPlugin);
let template =  '<div>'+
                '<table>'+
                    '<tr bgcolor="#00FFFF"><td align="right">${xValue}</td><td>${yValue}:</td><td >${value}</td></tr>' +
                '</table>'+
                '</div>'
export default {
  data: function() {
    return {
        dataSource: [
            [0.72, 0.71, 0.71, 0.67, 0.72, 0.53, 0.53, 0.56, 0.58, 0.56],
            [2.28, 2.29, 2.09, 1.84, 1.64, 1.49, 1.49, 1.39, 1.32, 1.23],
            [2.02, 2.17, 2.30, 2.39, 2.36, 2.52, 2.62, 2.57, 2.57, 2.74],
            [3.21, 3.26, 3.45, 3.47, 3.42, 3.34, 3.14, 2.83, 2.64, 2.61],
            [3.22, 3.13, 3.04, 2.95, 2.69, 2.49, 2.27, 2.18, 2.06, 1.87],
            [3.30, 3.39, 3.40, 3.48, 3.60, 3.67, 3.73, 3.79, 3.79, 4.07],
            [5.80, 5.74, 5.64, 5.44, 5.18, 5.08, 5.07, 5.00, 5.35, 5.47],
            [6.91, 7.40, 8.13, 8.80, 9.04, 9.24, 9.43, 9.35, 9.49, 9.69]
        ],
        titleSettings: {
            text: 'Crude Oil Production of Non-OPEC Countries (in Million barrels per day)',
            textStyle: {
                size: '15px',
                fontWeight: '500',
                fontStyle: 'Normal',
                fontFamily: 'Segoe UI'
            }
        },
        xAxis: {
            labels: ['Canada', 'China', 'Egypt', 'Mexico', 'Norway', 'Russia', 'UK', 'USA']
        },
        yAxis: {
            labels: ['2000', '2001', '2002', '2003', '2004', '2005', '2006', '2007', '2008', '2009', '2010']
        },
        cellSettings: {
            showLabel: false,
        },
        tooltipSettings: {
            fill: '#696295',
            textStyle: {
                color: '#FFFFFF',
                size: '12px'
            },
             border: {
                width: 2,
                color: '#F0C27B'
            },
            template: template
        },
        showTooltip: true
    }
},
    provide:{
    heatmap:[Tooltip, Legend]
    },
}
</script>
<style>
    table,
    th,
    td {
        border: 1px solid rgb(105, 105, 105);
        border-collapse: collapse;
    }
</style>
<style>
@import '../node_modules/@syncfusion/ej2-vue-heatmap/styles/material.css';
</style>

```

{% endtab %}
