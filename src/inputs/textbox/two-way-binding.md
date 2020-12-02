---
title: "Two Way Binding"
component: "Textbox"
description: "This section for Vue Textbox component demonstrates two-way binding."
---

# Two-Way Binding

Two-way binding can be achieved by using the `v-model` directive in Vue. In the following sample, when you change the value in one Textbox component, v-model will automatically update the value in the other Textbox.

The following example demonstrates how to set the `two-way-binding` in the Textbox.

{% tab template="textbox/two-way" %}

```html
<template>
<div id="app">
    <div id="wrapper1">
        <ejs-textbox floatLabelType="Auto" placeholder="Enter a name" v-model="value"></ejs-textbox>
    </div>
    <div id="wrapper2">
        <ejs-textbox floatLabelType="Auto" placeholder="Enter a name" v-model="value"></ejs-textbox>
    </div>
</div>
</template>
<script>
import Vue from 'vue';
import { TextBoxPlugin } from '@syncfusion/ej2-vue-inputs';
Vue.use(TextBoxPlugin);

export default {
 data: function(){
        return {
            value: null
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
#wrapper1{
    min-width: 250px;
    float: left;
    margin-left: 100px;
}
#wrapper2{
    min-width: 250px;
    float: right;
    margin-right: 100px;
}

</style>
```

{% endtab %}