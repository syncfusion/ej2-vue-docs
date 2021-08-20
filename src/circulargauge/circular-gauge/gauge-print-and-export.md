---
title: "Print and Export"
component: "CircularGauge"
description: "Print and Export support in circular gauge"
---

# Print and Export

## Print

The rendered circular gauge can be printed directly from the browser by calling the method [`print`](../api/circular-gauge/#print).

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
        <div class='wrapper'>
             <button v-on:click="clickPrint">Print</button>
            <ejs-circulargauge id="gauge" ref="gauge" allowPrint="true">
            </ejs-circulargauge>
        </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin, Print } from "@syncfusion/ej2-vue-circulargauge";
Vue.use(CircularGaugePlugin);
export default {
  data () {
    return {
    }
  },
methods: {
    clickPrint:function(args){
        this.$refs.gauge.ej2Instances.print();
    }
},
provide: {
  circulargauge: [Print]
}
};
</script>
<style>
  .wrapper {
    max-width: 300px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Export

The rendered circular gauge can be exported to the following formats using the [`export`](../api/circular-gauge/#export) method. The input parameters for this method are export type for format and file name of result.

* JPEG
* PNG
* SVG
* PDF

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
        <div class='wrapper'>
            <button v-on:click="clickExport">Export</button>
            <ejs-circulargauge id="gauge" ref="gauge" allowImageExport="true">
            </ejs-circulargauge>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin, ImageExport } from "@syncfusion/ej2-vue-circulargauge";
Vue.use(CircularGaugePlugin);
export default {
  data () {
    return {
    }
  },
methods: {
    clickExport:function(args){
        this.$refs.gauge.ej2Instances.export('PNG','Gauge');
    }
},
provide: {
  circulargauge: [ImageExport]
}
};
</script>
<style>
  .wrapper {
    max-width: 300px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}