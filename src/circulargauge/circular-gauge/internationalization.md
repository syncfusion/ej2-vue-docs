---
title: "Internationalization"
component: "CircularGauge"
description: "Internationalization support in circular gauge"
---

# Internationalization

Circular gauge provide supports for internationalization for below gauge elements.

* Axis label.
* Tooltip.

For more information about number formatter you can refer
[`internationalization`](http://ej2.syncfusion.com/documentation/base/intl.html).

<!-- markdownlint-disable MD036 -->

## Globalization

Globalization is the process of designing and developing a component that works in different cultures/locales.
Internationalization library is used to globalize number in CircularGauge component
using [`format`](../api/circular-gauge/label/#format-string) property in [`labelStyle`](../api/circular-gauge/label/).

<!-- markdownlint-disable MD036 -->

### Numeric Format

In the below example axis labels are `globalized` to EUR.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
<div id="app">
  <div class='wrapper'>
    <ejs-circulargauge :axes='axes' >
    </ejs-circulargauge>
  </div>
</div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";
import { loadCldr, L10n, setCulture, setCurrencyCode } from '@syncfusion/ej2-base';
setCulture('de');
setCurrencyCode('EUR');

Vue.use(CircularGaugePlugin);
export default {
    data: function () {
return {
 axes: [{
        labelStyle: {
            position: 'Inside',
            format: 'c'
        }
    }]
}
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