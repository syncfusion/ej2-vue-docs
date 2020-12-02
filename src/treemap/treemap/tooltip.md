# Tooltip

Tooltip is used to display details about the items in tree map when the mouse hovers over the item.

## Default tooltip

By default, tooltip is not visible. You can enable the tooltip by setting the `enable` property to true and injecting the `TreeMapTooltip` module using the `TreeMap.Inject(TreeMapTooltip)`.

The following example shows the default tooltip.

{% tab template="treemap/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
        <ejs-treemap id="treemap"  :dataSource='dataSource' :tooltipSettings='tooltipSettings' :weightValuePath='weightValuePath' :leafItemSettings='leafItemSettings'></ejs-treemap>
    </div>
</template>
<script>
import Vue from 'vue';
import { TreeMapPlugin, TreeMapTooltip } from "@syncfusion/ej2-vue-treemap";
Vue.use(TreeMapPlugin);

export default {
  data: function() {
    return {
     dataSource: [
        { fruit:'Apple', count:5000 },
                       { fruit:'Mango', count:3000 },
                       { fruit:'Orange', count:2300 },
                       { fruit:'Banana', count:500 },
                       { fruit:'Grape', count:4300 },
                       { fruit:'Papaya', count:1200 },
                       { fruit:'Melon', count:4500 }
    ],
   weightValuePath: 'count',
     tooltipSettings: {
            visible: true
    },
    leafItemSettings: {
        labelPath: 'fruit'
     }
    }
  },
  provide:{
    treemap:[TreeMapTooltip]
},
}
</script>
```

{% endtab %}

## Format tooltip

By default, tooltip shows information about weight value of current item. In addition, to show more information in tooltip, format the tooltip as `${dataField}` from data source.

The following example shows formatting the tooltip.

{% tab template="treemap/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
        <ejs-treemap id="treemap"  :dataSource='dataSource' :tooltipSettings='tooltipSettings' :weightValuePath='weightValuePath' :leafItemSettings='leafItemSettings'></ejs-treemap>
    </div>
</template>
<script>
import Vue from 'vue';
import { TreeMapPlugin, TreeMapTooltip } from "@syncfusion/ej2-vue-treemap";
Vue.use(TreeMapPlugin);

export default {
  data: function() {
    return {
     dataSource: [
        { fruit:'Apple', count:5000 },
                       { fruit:'Mango', count:3000 },
                       { fruit:'Orange', count:2300 },
                       { fruit:'Banana', count:500 },
                       { fruit:'Grape', count:4300 },
                       { fruit:'Papaya', count:1200 },
                       { fruit:'Melon', count:4500 }
    ],
   weightValuePath: 'count',
     tooltipSettings: {
            visible: true,
            format:'Name:${fruit} - TotalCount:${count}'
    },
    leafItemSettings: {
        labelPath: 'fruit'
     }
    }
  },
  provide:{
    treemap:[TreeMapTooltip]
},
}
</script>
```

{% endtab %}

## Tooltip template

Any HTML element can be displayed in tooltip using the ‘template’ property. You can use `${dataField}` as placeholder in HTML element to display the values from data source.

The following example shows tooltip template.

{% tab template="treemap/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
        <ejs-treemap id="treemap"  :dataSource='dataSource' :tooltipSettings='tooltipSettings' :weightValuePath='weightValuePath' :leafItemSettings='leafItemSettings'></ejs-treemap>
    </div>
</template>
<script>
import Vue from 'vue';
import Template1 from "./LabelTemplate.vue";
import { TreeMapPlugin, TreeMapTooltip } from "@syncfusion/ej2-vue-treemap";
Vue.use(TreeMapPlugin);

let contentVue = Vue.component("contentTemplate", {
  template: '<div><p>Name : {{data.fruit}}</p><p>TotalCount : {{data.count}}</p></div>',
  data() {
    return {
      data: {}
    };
  }
});

let contentTemplate = function() {
  return { template: contentVue };
};
export default {
  data: function() {
    return {
     dataSource: [
        { fruit:'Apple', count:5000 },
                       { fruit:'Mango', count:3000 },
                       { fruit:'Orange', count:2300 },
                       { fruit:'Banana', count:500 },
                       { fruit:'Grape', count:4300 },
                       { fruit:'Papaya', count:1200 },
                       { fruit:'Melon', count:4500 }
    ],
   weightValuePath: 'count',
     tooltipSettings: {
            visible: true,
            template:contentTemplate
    },
    leafItemSettings: {
        labelPath: 'fruit'
     }
    }
  },
  provide:{
    treemap:[TreeMapTooltip]
},
}
</script>
```

{% endtab %}
