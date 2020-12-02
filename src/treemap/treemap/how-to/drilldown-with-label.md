# Drilldown customization

## Add label template with drill down

Yon can add a label template as <div> element to the tree map control when using the label template. To add a label template to the tree map control, you have to hide another labels by setting the `showLabels` property to false in `leafItemSettings` to show only the label template.

To add label template to tree map drilldown, follow the given steps:

**Step 1**:

Create a tree map control and enable the drill-down option.

```html
<template>
      <div class='control_wrapper'>
         <ejs-treemap id='container' :dataSource="dataSource" weightValuePath="Sales" enableDrillDown="true" :palette="palette"
         :leafItemSettings='leafItemSettings' :levels='levels' >
         </ejs-treemap>
      </div>
</template>

<script>
import Vue from 'vue';
import { TreeMapPlugin } from '@syncfusion/ej2-vue-treemap';

Vue.use(TreeMapPlugin);
export default {
   data () {
    return {
      dataSource:  [
            { Continent: "China", Company: "Volkswagen", Sales: 3005994 },
            { Continent: "China", Company: "General Motors", Sales: 1230044 },
            { Continent: "China", Company: "Honda", Sales: 1197023 },
            { Continent: "United States", Company: "General Motors", Sales: 3042775 },
            { Continent: "United States", Company: "Ford", Sales: 2599193 },
            { Continent: "United States", Company: "Toyota", Sales: 2449587 },
            { Continent: "Japan", Company: "Toyota", Sales: 1527977 },
            { Continent: "Japan", Company: "Honda", Sales: 706982 },
            { Continent: "Japan", Company: "Suzuki", Sales: 623041 },
            { Continent: "Germany", Company: "Volkswagen", Sales: 655977 },
            { Continent: "Germany", Company: "Mercedes", Sales: 310845 },
            { Continent: "Germany", Company: "BMW", Sales: 261931 },
            { Continent: "United Kingdom", Company: "Ford ", Sales: 319442 },
            { Continent: "United Kingdom", Company: "Vauxhall", Sales: 251146 },
            { Continent: "United Kingdom", Company: "Volkswagen", Sales: 206994 }
        ],
        palette: ['white'],
        levels: [
            {
                groupPath: 'Continent', border: { color: 'black', width: 0.5 },
            },
            {
              groupPath: 'Company', border: { color: 'black', width: 0.5 },
            }
        ],
        leafItemSettings: {
          showLabels: false,
          labelTemplate: '<div style="background-color: red">{{:Company}}</div>',
          templatePosition: 'Center'
        }
    }
  }
}
}
</script>
```

**Step 2**:

Add the label template in the `leafItemSettings` options, and then set the `showLabels` property to false to hide another labels and show only label template.

{% tab template="treemap/getting-started", isDefaultActive=true %}

```html
<template>
      <div class='control_wrapper'>
         <ejs-treemap id='container' :dataSource="dataSource" weightValuePath="Sales" enableDrillDown="true" :palette="palette"
         :leafItemSettings='leafItemSettings' :levels='levels' :drillStart='drillStart' >
         </ejs-treemap>
      </div>
</template>

<script>
import Vue from 'vue';
import { TreeMapPlugin } from '@syncfusion/ej2-vue-treemap';

Vue.use(TreeMapPlugin);
export default {
   data () {
    return {
      dataSource:  [
            { Continent: "China", Company: "Volkswagen", Sales: 3005994 },
            { Continent: "China", Company: "General Motors", Sales: 1230044 },
            { Continent: "China", Company: "Honda", Sales: 1197023 },
            { Continent: "United States", Company: "General Motors", Sales: 3042775 },
            { Continent: "United States", Company: "Ford", Sales: 2599193 },
            { Continent: "United States", Company: "Toyota", Sales: 2449587 },
            { Continent: "Japan", Company: "Toyota", Sales: 1527977 },
            { Continent: "Japan", Company: "Honda", Sales: 706982 },
            { Continent: "Japan", Company: "Suzuki", Sales: 623041 },
            { Continent: "Germany", Company: "Volkswagen", Sales: 655977 },
            { Continent: "Germany", Company: "Mercedes", Sales: 310845 },
            { Continent: "Germany", Company: "BMW", Sales: 261931 },
            { Continent: "United Kingdom", Company: "Ford ", Sales: 319442 },
            { Continent: "United Kingdom", Company: "Vauxhall", Sales: 251146 },
            { Continent: "United Kingdom", Company: "Volkswagen", Sales: 206994 }
        ],
        palette: ['white'],
        levels: [
            {
                groupPath: 'Continent', border: { color: 'black', width: 0.5 },
            },
            {
              groupPath: 'Company', border: { color: 'black', width: 0.5 },
            }
        ],
        leafItemSettings: {
          showLabels: false,
          labelTemplate: '<div style="background-color: red">{{:Company}}</div>',
          templatePosition: 'Center'
        }
    }
  },
  methods:{
    drillStart:function(args){
        let labelElementGroup = document.getElementById('container_Label_Template_Group');
        labelElementGroup.remove();
    }
}
}
</script>
```

{% endtab %}