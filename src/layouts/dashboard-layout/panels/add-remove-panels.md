---
title: "Adding and removing panels"
component: "DashboardLayout"
description: "This section explains how to add and remove panels dynamically in Essential JS 2 DashboardLayout component"
---
# Adding and removing panels dynamically

In real-time cases, the data being presented within the dashboard should be updated frequently which includes adding or removing the data dynamically within the dashboard. This can be easily achieved by using the [`addPanel`](https://ej2.syncfusion.com/vue/documentation/api/dashboard-layout/#addpanel) and [`removePanel`](https://ej2.syncfusion.com/vue/documentation/api/dashboard-layout/#removepanel) public methods of the component.

## Add or remove panels dynamically

Panels can be added dynamically by using the `addPanel` public method by passing the `panel` property as parameter. Also, they can be removed dynamically by using the `removePanel` public method by passing the `panel id` value as a parameter.

It is also possible to remove all the panels in a Dashboard Layout by calling [removeAll](https://ej2.syncfusion.com/vue/documentation/api/dashboard-layout/#removeall) method.

```js
dashboard.removeAll();

```

The following sample demonstrates how to add and remove the panels dynamically in the dashboard layout component. Here, panels can be added in any desired position of required size by selecting them in the numeric boxes and clicking add button and remove them by selecting the ID of the panel.

{% tab template="dashboard-layout/add-remove-panel", isDefaultActive=true %}

```html
<template>
    <div>
        <div className="col-lg-8 control-section" id="control_dash">
            <div className="content-wrapper">
                <div id = "dashboardElement">
                    <!--  DashboardLayout element declaration -->
                    <ejs-dashboardlayout id='dashboard_default'  :columns="5">
                       <e-panels>
                          <e-panel id="Panel0" :sizeX="1" :sizeY="1" :row="0" :col="0" content="<div class='content'>0</div>"></e-panel>
                          <e-panel id="Panel1" :sizeX="3" :sizeY="2" :row="0" :col="1" content="<div class='content'>1</div>"></e-panel>
                          <e-panel id="Panel2" :sizeX="1" :sizeY="3" :row="0" :col="4" content="<div class='content'>2</div>"></e-panel>
                          <e-panel id="Panel3" :sizeX="1" :sizeY="1" :row="1" :col="0" content="<div class='content'>3</div>"></e-panel>
                          <e-panel id="Panel4" :sizeX="2" :sizeY="1" :row="2" :col="0" content="<div class='content'>4</div>"></e-panel>
                          <e-panel id="Panel5" :sizeX="1" :sizeY="1" :row="2" :col="2" content="<div class='content'>5</div>"></e-panel>  
                          <e-panel id="Panel6" :sizeX="1" :sizeY="1" :row="2" :col="3" content="<div class='content'>6</div>"></e-panel>  
                        </e-panels>
                     </ejs-dashboardlayout>
                    <!-- end of dashboardlayout element -->
                </div>
            </div>
        </div>
    <div className="col-lg-4 property-section dashboard" id="api_property">
        <div className="row property-panel-content">
            <div className="card-body">
                <div className="form-group row">
                    <table id ="add">
                        <tbody>
                            <tr><td id="property">Add Panel properties</td></tr>
                            <tr>
                                <td>SizeX</td>
                                <td>
                                    <ejs-numerictextbox id="sizex" placeholder="Ex: 1" :value="value" :min="min" :max="max" :floatLabelType="floatLabelType"></ejs-numerictextbox>
                                </td>
                            </tr>
                            <tr>
                                <td>SizeX</td>
                                <td>
                                    <ejs-numerictextbox id="sizey" placeholder="Ex: 1" :value="value" :min="min" :max="max" :floatLabelType="floatLabelType"></ejs-numerictextbox>
                                </td>
                            </tr>
                            <tr>
                                <td>Row</td>
                                <td>
                                    <ejs-numerictextbox id="row" placeholder="Ex: 1" :value="value" :min="rowmin" :max="rowmax" :floatLabelType="floatLabelType"></ejs-numerictextbox>
                                </td>
                            </tr>
                            <tr>
                                <td>Column</td>
                                <td>
                                    <ejs-numerictextbox id="column" placeholder="Ex: 1" :value="value" :min="colmin" :max="colmax" :floatLabelType="floatLabelType"></ejs-numerictextbox>
                                </td>
                            </tr>
                            <tr>
                                <td>
                                    <ejs-button id="add" class="e-primary" v-on:click.native="onAdd"  >Add Panel</ejs-button>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                    <table id ="remove">
                        <tbody>
                            <tr><td id="property">Remove panel properties</td></tr>
                                <tr>
                                    <td> Panel Id </td>
                                    <td>
                                        <ejs-dropdownlist id='dropdown' placeholder='Select a id value' :dataSource='data'></ejs-dropdownlist>
                                    </td>
                                </tr>
                                <tr>
                                    <td> <ejs-button id="removeButton" class="e-primary" v-on:click.native="onRemove" >Remove Panel</ejs-button>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Vue from "vue";
// Import syncfusion dashboardlayout component from layouts package
import { DashboardLayoutPlugin } from "@syncfusion/ej2-vue-layouts";
// Import syncfusion button component from buttons package
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
// Import syncfusion numerictextbox component from inputs package
import { NumericTextBoxPlugin  } from "@syncfusion/ej2-vue-inputs";
// Import syncfusion dropdownlist component from dropdowns package
import { DropDownListPlugin   } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(DashboardLayoutPlugin);
Vue.use(ButtonPlugin);
Vue.use(DropDownListPlugin);
Vue.use(NumericTextBoxPlugin );

export default {
    data: function() {
        return {
            floatLabelType: 'Never',
            min: 1,
            max: 5,
            rowmin: 0,
            rowmax: 5,
            colmin: 0,
            colmax: 4,
            value:'',
            data: ['Panel0', 'Panel1', 'Panel2', 'Panel3', 'Panel4', 'Panel5', 'Panel6'],
            count: 7
        };
    },
    methods: {
        onAdd: function(args) {
            var sizeX = document.getElementById("sizex").ej2_instances[0];
            var sizeY = document.getElementById("sizey").ej2_instances[0];
            var row = document.getElementById("row").ej2_instances[0];
            var column = document.getElementById("column").ej2_instances[0];
            var dropdownObject = document.getElementById("dropdown").ej2_instances[0];
            var dashboardObj = document.getElementById("dashboard_default").ej2_instances[0];
            var panel = [{
                'id': "Panel"+ this.count.toString(),
                'sizeX': sizeX.value,
                'sizeY': sizeY.value,
                'row': row.value,
                'col': column.value,
                'content': "<div class='content'>"+ this.count +"</div>"
            }];
            dropdownObject.dataSource.push("Panel" + this.count.toString());
            dropdownObject.refresh();
            this.count = this.count + 1;
            dashboardObj.addPanel(panel[0]);
        },

        onRemove: function(args) {
            var dashboardObj = document.getElementById("dashboard_default").ej2_instances[0];
            var dropdownObject = document.getElementById("dropdown").ej2_instances[0];
            dashboardObj.removePanel(dropdownObject.value);
            dropdownObject.dataSource.splice(dropdownObject.dataSource.indexOf(dropdownObject.value), 1);
            dropdownObject.value = null;
            dropdownObject.refresh();
        },
    },
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
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

#control_dash {
    display: block;
    width: 59%;
    float: left;
}
#api_property {
  display: inline-block;
  margin: 10px;
}

#add {
    border: 1px solid black;
    padding: 10px;
    margin: 10px;
}

#remove {
    border: 1px solid black;
    padding: 10px;
    margin: 10px;
    width: 377px;
}

#property {
    padding:10px;
}

#removeButton {
    border: 1px solid black;
    padding: 10px;
    margin: 10px;
    width: 125px;
}

#dashboardElement {
    padding-top: 30px;
}

#dashboard_default .e-panel {
  transition:none !important;
}
</style>
```

{% endtab %}
