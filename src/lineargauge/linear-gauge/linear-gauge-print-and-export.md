---
title: "Print and Export"
component: "LinearGauge"
description: "Print and Export support in linear gauge"
---

# Print and Export

## Print

The rendered linear gauge can be printed directly from the browser by calling the method [`print`](../api/linear-gauge/#print).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="col-md-8 control-section">
    <div class="content-wrapper">
    <div align='center'>
    <ejs-button id='togglebtn' isToggle="true" v-on:click.native='clickToggle'></ejs-button>
    <ejs-lineargauge id="container">
    </ejs-lineargauge>
   </div>
  </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.use(LinearGaugePlugin, ButtonPlugin);
export default {
  data () {
    return {

    }
  },
methods: {
    clickToggle:function(args){
       this.$refs.gauge.ej2Instances.print();
    }
}
};
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}

@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';

</style>
```

{% endtab %}

## Export

The rendered linear gauge can be exported to the following formats using the [`export`](../api/linear-gauge/#export) method. The input parameters for this method are export type for format and file name of result.

* JPEG
* PNG
* SVG
* PDF

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="col-md-8 control-section">
    <div class="content-wrapper">
    <div align='center'>
    <ejs-button id='togglebtn' isToggle="true" v-on:click.native='clickToggle'>
    </ejs-button>
    <ejs-lineargauge id="container" ref='gauge'>
    </ejs-lineargauge>
   </div>
  </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.use(LinearGaugePlugin, ButtonPlugin);
export default {
  data () {
    return {

    }
  },
methods: {
    clickToggle:function(args){
        this.$refs.gauge.ej2Instances.export('PNG','Gauge');
    }
}
};
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}

@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';

</style>
```

{% endtab %}