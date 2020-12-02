# Selection and Highlight

## Selection

Selection is used to select a particular group or item to differentiate from other items. Each item or group can be selected and deselected when interacting with the items.

By tapping on the specific legend, the treemap items which are bounded to the selected legend is also selected and vice versa.

The layer `selectionSettings.fill` property is used to change the selected item color. The `selectionSettings.border.color` and `selectionSettings.border.width` properties are used to customize the selected item's border.

The selection is enabled using the `selectionSettings.enable` property. To use selection feature in tree map, import the `TreeMapSelection`, and inject using the `TreeMap.Inject(TreeMapSelection);`.

Tree map selection is shown in the following example.

{% tab template="treemap/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
        <ejs-treemap id="treemap" :dataSource='dataSource' :levels='levels' :selectionSettings='selectionSettings' :weightValuePath='weightValuePath' :leafItemSettings='leafItemSettings'></ejs-treemap>
    </div>
</template>
<script>
import Vue from 'vue';
import { TreeMapPlugin, TreeMapSelection } from "@syncfusion/ej2-vue-treemap";
Vue.use(TreeMapPlugin);

export default {
  data: function() {
    return {
     dataSource: [
        { dataType: "Import", type: "Animal products",   product: "2010", sales: 20839332874 },
    { dataType: "Import", type: "Animal products",   product: "2011", sales: 23098635589 },
    { dataType: "Import", type: "Chemical products", product: "2010", sales: 141637951510 },
    { dataType: "Import", type: "Chemical products", product: "2011", sales: 161550338209 },
    { dataType: "Import", type: "Base metals",       product: "2010", sales: 86079439944 },
    { dataType: "Import", type: "Base metals",       product: "2011", sales: 103821671535 },
    { dataType: "Import", type: "Textile articles",       product: "2010", sales: 97126140830 },
    { dataType: "Import", type: "Textile articles",       product: "2011", sales: 104980750811 },
    { dataType: "Export", type: "Animal products",   product: "2010", sales:  15845503378 },
    { dataType: "Export", type: "Animal products",   product: "2011", sales:  20650111620 },
    { dataType: "Export", type: "Chemical products", product: "2010", sales: 136100054087 },
    { dataType: "Export", type: "Chemical products", product: "2011", sales: 146341672411 },
    { dataType: "Export", type: "Base metals",       product: "2010", sales: 59060592813 },
    { dataType: "Export", type: "Base metals",       product: "2011", sales: 71785882641 },
    { dataType: "Export", type: "Textile articles",       product: "2010", sales: 20982380561 },
    { dataType: "Export", type: "Textile articles",       product: "2011", sales: 26016143783 }
    ],
    weightValuePath: 'sales',
        levels: [
            { groupPath: 'dataType', fill: '#c5e2f7', headerStyle: { size: '16px' }, headerAlignment: 'Center', groupGap: 5 },
            { groupPath: 'product', fill: '#a4d1f2', headerAlignment: 'Center' , groupGap: 2 }
        ],
        leafItemSettings: {
            labelPath: 'type',
            fill: '#8ebfe2',
            labelPosition: 'Center'
        },
        selectionSettings: {
            enable: true,
            fill: '#58a0d3',
            border: { width: 0.3, color: 'black' },
            opacity: '1'
        },
    }
  },
  provide:{
    treemap:[ TreeMapSelection]
},
}
</script>
```

{% endtab %}

## Highlight

Highlight is used to highlight an item or group from other items. Each item or group can be highlighted when hovering the mouse over items.

Hovering on the specific legend, the treemap items which are bounded to the selected legend is also highlighted and vice versa.

The layer `highlightSettings.fill` property is used to change the highlighted item color. The `highlightSettings.border.color` and `highlightSettings.border.width` properties are used to customize the highlighted shape border. You can highlight an item by hovering the mouse over the item. The highlight is enabled using the `highlightSettings.enable` property.

The following code example shows highlighting the item.

{% tab template="treemap/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
        <ejs-treemap id="treemap" :dataSource='dataSource' :levels='levels' :highlightSettings='highlightSettings' :weightValuePath='weightValuePath' :leafItemSettings='leafItemSettings'></ejs-treemap>
    </div>
</template>
<script>
import Vue from 'vue';
import { TreeMapPlugin, TreeMapHighlight } from "@syncfusion/ej2-vue-treemap";
Vue.use(TreeMapPlugin);

export default {
  data: function() {
    return {
     dataSource: [
        { dataType: "Import", type: "Animal products",   product: "2010", sales: 20839332874 },
    { dataType: "Import", type: "Animal products",   product: "2011", sales: 23098635589 },
    { dataType: "Import", type: "Chemical products", product: "2010", sales: 141637951510 },
    { dataType: "Import", type: "Chemical products", product: "2011", sales: 161550338209 },
    { dataType: "Import", type: "Base metals",       product: "2010", sales: 86079439944 },
    { dataType: "Import", type: "Base metals",       product: "2011", sales: 103821671535 },
    { dataType: "Import", type: "Textile articles",       product: "2010", sales: 97126140830 },
    { dataType: "Import", type: "Textile articles",       product: "2011", sales: 104980750811 },
    { dataType: "Export", type: "Animal products",   product: "2010", sales:  15845503378 },
    { dataType: "Export", type: "Animal products",   product: "2011", sales:  20650111620 },
    { dataType: "Export", type: "Chemical products", product: "2010", sales: 136100054087 },
    { dataType: "Export", type: "Chemical products", product: "2011", sales: 146341672411 },
    { dataType: "Export", type: "Base metals",       product: "2010", sales: 59060592813 },
    { dataType: "Export", type: "Base metals",       product: "2011", sales: 71785882641 },
    { dataType: "Export", type: "Textile articles",       product: "2010", sales: 20982380561 },
    { dataType: "Export", type: "Textile articles",       product: "2011", sales: 26016143783 }
    ],
   weightValuePath: 'sales',
        levels: [
            { groupPath: 'dataType', fill: '#c5e2f7', headerStyle: { size: '16px' }, headerAlignment: 'Center', groupGap: 5 },
            { groupPath: 'product', fill: '#a4d1f2', headerAlignment: 'Center' , groupGap: 2 }
        ],
        leafItemSettings: {
            labelPath: 'type',
            fill: '#8ebfe2',
            labelPosition: 'Center'
        },
         highlightSettings: {
            enable: true,
            fill: '#71b0dd',
            border: { width: 0.3, color: 'black' },
            opacity: '1'
        }
    }
  },
  provide:{
    treemap:[TreeMapHighlight]
},
}
</script>
```

{% endtab %}
