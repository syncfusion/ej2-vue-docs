---
title: "Internationalization"
component: "LinearGauge"
description: "Internationalization support in linear gauge"
---

# Internationalization

Linear gauge provide supports for internationalization for below gauge elements.

* Axis label.
* Tooltip

For more information about number and date formatter you can refer
[`internationalization`](http://ej2.syncfusion.com/documentation/base/intl.html).

<!-- markdownlint-disable MD036 -->

**Globalization**

Globalization is the process of designing and developing an component that works in different cultures/locales. Internationalization library is used to globalize number in LinearGauge component
using [`format`](../api/linear-gauge/label/#format-string) property in [`labelStyle`](../api/linear-gauge/label/).

**Numeric Format**

In the below example axis labels are `globalized` to EUR.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge :axes= 'axes'>
    </ejs-lineargauge>
   </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";
Vue.use(LinearGaugePlugin);
export default {
      data: function () {
        return {
            axes: [{
        minimum: 0,
        maximum: 120,
        majorTicks: {
            interval: 10,
            height: 10
        },
        minorTicks: {
            interval: 5,
            height: 5
        },
        labelStyle: {
            format: 'c'
        }
    }]
        }
      }
};
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}