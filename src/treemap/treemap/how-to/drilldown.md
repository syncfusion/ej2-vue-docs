# Drilldown

<!-- markdownlint-disable MD033 -->

## Customize the header for treemap drilldown

Yon can add a header element as <div> and customize it to show the population of a particular country or continent on treemap drill-down.

To customize the header for treemap drill-down, follow the given steps:

**Step 1**:

<!-- markdownlint-disable MD031 -->
Initialize the treemap and enable the drill-down option.

```html
 <template>
<div>
    <div id="header" style="background-color: #179bd7"></div>
      <div class='control_wrapper'>
         <ejs-treemap id='container' :dataSource="dataSource" weightValuePath="Population" format="n"
                     useGroupingSeparator="true" enableDrillDown="true" :palette="palette"
         :leafItemSettings='leafItemSettings' :levels='levels'>
         </ejs-treemap>
      </div>
  </div>
</template>

<script>
import Vue from 'vue';
import { TreeMapPlugin } from '@syncfusion/ej2-vue-treemap';
import { data } from './datasource.js';

Vue.use(TreeMapPlugin);
export default {
   data () {
    return {
      dataSource:  data,
        palette: ["#9999ff", "#CCFF99", "#FFFF99", "#FF9999", "#FF99FF", "#FFCC66"],
        levels: [
            {
                groupPath: 'Continent', border: { color: 'black', width: 0.5 },
            },
            {
              groupPath: 'States', border: { color: 'black', width: 0.5 },
            },
            {
              groupPath: 'Region', border: { color: 'black', width: 0.5 },
            }
        ],
        leafItemSettings: {
          labelPath:'Name',
          showLabels: false
        }
    }
  },
}
</script>
```

**Step 2**:

Show the population of a particular continent in the treemap `loaded` event. In this event, you can get the header element.

```javascript
    loaded:function(args) {
      let header = document.getElementById('header');
        var population = 0;
        for (let i = 0; i < args.treemap.layout.renderItems[0]['parent'].Continent.length; i++) {
            population += +(args.treemap.layout.renderItems[0]['parent'].Continent[i]['data'].Population);
        }
        header.innerHTML = 'Continent - Population : ' + population
    }
```

**Step 3**:

Customize the population for drilled countries or states in the header element when drill-down the treemap. The `drillEnd` event will be triggered when treemap is drilled.

{% tab template="treemap/getting-started", isDefaultActive=true %}

```html
<template>
<div>
    <div id="header" style="background-color: #179bd7"></div>
      <div class='control_wrapper'>
         <ejs-treemap id='container' :dataSource="dataSource" weightValuePath="Population" format="n"
                     useGroupingSeparator="true" enableDrillDown="true" :palette="palette"
         :leafItemSettings='leafItemSettings' :levels='levels' :drillEnd='drillEnd' :loaded="loaded">
         </ejs-treemap>
      </div>
  </div>
</template>

<script>
import Vue from 'vue';
import { TreeMapPlugin } from '@syncfusion/ej2-vue-treemap';
import { data } from './datasource.js';

Vue.use(TreeMapPlugin);
export default {
   data () {
    return {
      dataSource:  data,
        palette: ["#9999ff", "#CCFF99", "#FFFF99", "#FF9999", "#FF99FF", "#FFCC66"],
        levels: [
            {
                groupPath: 'Continent', border: { color: 'black', width: 0.5 },
            },
            {
              groupPath: 'States', border: { color: 'black', width: 0.5 },
            },
            {
              groupPath: 'Region', border: { color: 'black', width: 0.5 },
            }
        ],
        leafItemSettings: {
          labelPath:'Name',
          showLabels: false
        }
    }
  },
  methods:{
    drillEnd:function(args){
        let header = document.getElementById('header');
        let layout = document.getElementById("container_TreeMap_Squarified_Layout");
        let population = 0;
        if (args.treemap.layout.renderItems[0]['isDrilled']) {
            for (let i = 0; i < args.treemap.layout.renderItems.length; i++) {
                population += +(args.treemap.layout.renderItems[i]['data'].Population);
            }
            header.innerHTML = layout.children[0].children[1].innerHTML.split(']')[1] + ' - ' + population;
        }
        else if (args.treemap.layout.renderItems[0]['parent'].Continent) {
            for (let i = 0; i < args.treemap.layout.renderItems[0]['parent'].Continent.length; i++) {
                population += +(args.treemap.layout.renderItems[0]['parent'].Continent[i]['data'].Population);
            }
            header.innerHTML = 'Continent - Population : ' + population;
        } else {
            population = args.treemap.layout.renderItems[0]['data'].Population;
            header.innerHTML = layout.children[0].children[1].innerHTML.split(']')[1] + ' - Population : ' + population;
        }
    },
    loaded:function(args) {
      let header = document.getElementById('header');
        var population = 0;
        for (let i = 0; i < args.treemap.layout.renderItems[0]['parent'].Continent.length; i++) {
            population += +(args.treemap.layout.renderItems[0]['parent'].Continent[i]['data'].Population);
        }
        header.innerHTML = 'Continent - Population : ' + population
    }
}
}
</script>
```

{% endtab %}