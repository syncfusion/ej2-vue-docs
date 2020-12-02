---
title: "Customize progress using cssClass"
component: "ProgressButton"
description: "Vue ProgressButton how to section, change text content and styles, hide spinner, customize progress."
---

# Customize progress using cssClass

You can customize the background filler UI using the [`cssClass`](../../api/progress-button#cssClass) property.

* Adding `e-vertical` to `cssClass` shows vertical progress.
* Adding `e-progress-top` to `cssClass` shows progress at the top.

You can also show reverse progress by adding custom class to the [`cssClass`](../../api/progress-button#cssClass) property.

{% tab template="progress-button/custom-progress", isDefaultActive=true %}

```html
<template>
 <div>
 <ejs-progressbutton content='Vertical Progress' :enableProgress="true" cssClass='e-hide-spinner e-vertical' duration=4000></ejs-progressbutton>
 <ejs-progressbutton content='Progress Top' :enableProgress="true" cssClass='e-hide-spinner e-progress-top' duration=4000></ejs-progressbutton>
 <ejs-progressbutton content='Reverse Progress' :enableProgress="true" cssClass='e-hide-spinner e-reverse-progress' duration=4000></ejs-progressbutton>
 </div>
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
#container {
    visibility: hidden;
}

#loader {
    color: #008cff;
    height: 40px;
    left: 45%;
    position: absolute;
    top: 45%;
    width: 30%;
}

button {
    margin: 25px;
}

.e-reverse-progress .e-progress {
    right: 0;
    left: auto;
}
</style>
```

{% endtab %}