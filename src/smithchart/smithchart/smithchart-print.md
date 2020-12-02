---
title: "Print and Export"
component: "Smith Chart"
description: "Print and export support in smith chart"
---

# Print and Export

## Print

The rendered smithchart can be printed directly from the browser by calling the public method print. ID of the smithchart's div element must be passed as argument to that method.

```html
<template>
    <div class="control_wrapper">
        <ejs-smithchart id="smithchart" ref='smithchart' >
                <e-seriesCollection>
                    <e-series :dataSource='dataSource' :name='name' :reactance='reactance' :resistance='resistance' :loaded='loaded'></e-series>
                </e-seriesCollection>
        </ejs-smithchart>
    </div>
</template>
<script>
import Vue from 'vue';
import { SmithchartPlugin } from "@syncfusion/ej2-vue-charts";
Vue.use(SmithchartPlugin);

export default {
  data: function() {
    return {
        dataSource: [
                 { resistance: 10, reactance: 25 }, { resistance: 8, reactance: 6 },
                { resistance: 6, reactance: 4.5 }, { resistance: 4.5, reactance: 2 },
                { resistance: 3.5, reactance: 1.6 }, { resistance: 2.5, reactance: 1.3 },
                { resistance: 2, reactance: 1.2 }, { resistance: 1.5, reactance: 1 },
                { resistance: 1, reactance: 0.8 }, { resistance: 0.5, reactance: 0.4 },
                { resistance: 0.3, reactance: 0.2 }, { resistance: 0, reactance: 0.15 },
            ],
            name: 'Transmission1',
            reactance: 'reactance', resistance: 'resistance',
    }
  },
   methods: {
    loaded: function(args) {
         args.smithchart.print();
   }
  }
}
</script>
```

## Export

The rendered smithchart can be exported to JPEG , PNG, SVG or PDF format by using export method in smithchart. Input parameters for this method are Export Type for format and fileName of result.

```html
<template>
    <div class="control_wrapper">
        <ejs-smithchart id="smithchart" ref='smithchart'  >
                <e-seriesCollection>
                    <e-series :dataSource='dataSource' :name='name' :reactance='reactance' :resistance='resistance' :loaded='loaded'></e-series>
                </e-seriesCollection>
        </ejs-smithchart>
    </div>
</template>
<script>
import Vue from 'vue';
import { SmithchartPlugin } from "@syncfusion/ej2-vue-charts";
Vue.use(SmithchartPlugin);

export default {
  data: function() {
    return {
        dataSource: [
                 { resistance: 10, reactance: 25 }, { resistance: 8, reactance: 6 },
                { resistance: 6, reactance: 4.5 }, { resistance: 4.5, reactance: 2 },
                { resistance: 3.5, reactance: 1.6 }, { resistance: 2.5, reactance: 1.3 },
                { resistance: 2, reactance: 1.2 }, { resistance: 1.5, reactance: 1 },
                { resistance: 1, reactance: 0.8 }, { resistance: 0.5, reactance: 0.4 },
                { resistance: 0.3, reactance: 0.2 }, { resistance: 0, reactance: 0.15 },
            ],
            name: 'Transmission1',
            reactance: 'reactance', resistance: 'resistance',
    }
  },
  methods: {
    loaded: function(args) {
         args.smithchart.export('PNG', 'export');
   }
  }
}
</script>
```