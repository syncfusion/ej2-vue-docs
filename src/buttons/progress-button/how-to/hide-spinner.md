---
title: "Hide spinner"
component: "ProgressButton"
description: "Vue ProgressButton how to section, change text content and styles, hide spinner, customize progress."
---

# Hide spinner

You can hide spinner in the ProgressButton by setting the `e-hide-spinner` property to [`cssClass`](../../api/progress-button#cssClass).

{% tab template="progress-button/default", isDefaultActive=true %}

```html
<template>
<ejs-progressbutton content="Progress" :enableProgress="true" cssClass='e-hide-spinner'></ejs-progressbutton>
</template>

<script>
import Vue from 'vue';
import { ProgressButtonPlugin } from "@syncfusion/ej2-vue-splitbuttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ProgressButtonPlugin);

export default {}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
</style>
```

{% endtab %}