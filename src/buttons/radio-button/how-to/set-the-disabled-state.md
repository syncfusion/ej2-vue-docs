---
title: "RadioButton How To sections"
component: "RadioButton"
description: "Vue RadioButton how to section, name and value in form submit, customize RadioButton appearance."
---

# Set the disabled state

RadioButton component can be enabled/disabled by giving [`disabled`](../../api/radio-button#disabled) property. To disable RadioButton component,
the `disabled` property can be set as `true`.

The following example illustrates how to disable a radio button and the selected one is displayed using [`change`](../../api/radio-button#change) event.

{% tab template= "radio-button/default" %}

```html
<template>
<ul>
<li><div id="text">Selected: Option 1</div></li>
<li> <ejs-radiobutton label="Option 1" name="default" checked="true" :change="onChange" ></ejs-radiobutton></li>
<li> <ejs-radiobutton label="Option 2" name="default" disabled="true" :change="onChange"></ejs-radiobutton></li>
<li> <ejs-radiobutton label="Option 3" name="default" :change="onChange"></ejs-radiobutton></li>
</ul>
</template>

<script>
import Vue from 'vue';
import { RadioButtonPlugin } from '@syncfusion/ej2-vue-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(RadioButtonPlugin);

export default {
  methods: {
    onChange: function(args) {
      document.getElementById('text').innerText = 'Selected : ' + args.event.target.ej2_instances[0].label;
    }
  }
};
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';;

.e-radio-wrapper {
  margin-top: 18px;
}

li {
  list-style: none;
}

#text {
  font-size: 16px;
}

</style>
```

{% endtab %}