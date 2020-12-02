---
title: "Combo box autofill"
component: "ComboBox"
description: "This section explains how to acheive autofill functionality in combo box control."
---

# Autofill supports with ComboBox

The ComboBox supports the `autofill` behaviour with the help of
[autofill](../../api/combo-box/#autofill) property. Whenever you change
the input value, the ComboBox will autocomplete your data by matching the typed character. Suppose, if no
matches found then, ComboBox doesn't suggest any item.

The following examples, showcase that how to work autofill with ComboBox.

{% tab template="combobox/autofill", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-combobox id='combobox' :dataSource='sportsData' :autofill='autofill' placeholder='Select a game'></ejs-combobox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ComboBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(ComboBoxPlugin);

export default {
  data () {
    return {
      sportsData: ['Badminton', 'Cricket', 'Football', 'Golf', 'Tennis'],
      autofill : true,
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
</style>
```

{% endtab %}
