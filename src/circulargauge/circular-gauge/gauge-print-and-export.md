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
    <ejs-button id='print' isToggle="true" v-on:click.native='clickPrint'>
    </ejs-button>
    <ejs-circulargauge id="gauge" ref="gauge">
    </ejs-circulargauge>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
Vue.use(CircularGaugePlugin, ButtonPlugin);
export default {
  data () {
    return {

    }
  },
methods: {
    clickPrint:function(args){
        this.$refs.gauge.ej2Instances.print();
    }
}
};
</script>
<style>
  .wrapper {
    max-width: 300px;
    margin: 0 auto;
  }

  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';

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
    <ejs-button id='export' isToggle="true" v-on:click.native='clickExport'></ejs-button>
    <ejs-circulargauge id="gauge" ref="gauge">
    </ejs-circulargauge>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
Vue.use(CircularGaugePlugin, ButtonPlugin);
export default {
  data () {
    return {

    }
  },
methods: {
    clickExport:function(args){
        this.$refs.gauge.ej2Instances.export('PNG','Gauge');
    }
}
};
</script>
<style>
  .wrapper {
    max-width: 300px;
    margin: 0 auto;
  }

@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';

</style>
```

{% endtab %}