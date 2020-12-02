---
title: "Drop-down list How to clear the list item"
component: "DropDownList"
description: "This section explains on how to clear the selected items of the Syncfusion Vue drop-down list component."
---

# Clear the selected item in DropDownList

You can clear the selected item in the below two different ways.

By clicking on the `clear icon` which is shown in DropDownList element, you can clear the selected item in
DropDownList through **interaction**. By using [`showClearButton`](../../api/drop-down-list/#showclearbutton)
property, you can enable the clear icon in DropDownList element.

Through **programmatic** you can set `null` value to anyone of the index, text or value property to clear the selected item in DropDownList.

The following example demonstrate about how to clear the selected item in DropDownList.

{% tab template="drop-down-list/how-to/value", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:0 auto; width:250px;">
        <br>
        <ejs-dropdownlist id='dropdownlist' ref='dropdownObj' :value='dropDownValue' :dataSource='sportsData' :showClearButton='true' placeholder='Select a game'></ejs-dropdownlist>
    </div>
    <div style='padding: 50px'>
      <button id='button' class="e-control e-btn" v-on:click="onClick"> Set null to value property</button>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(DropDownListPlugin);
export default {
  data (){
    return {
        dropDownValue: null,
        sportsData: ["American Football", "Badminton", "Basketball", "Cricket", "Football", "Golf", "Hockey", "Rugby", "Snooker", "Tennis"]
    }
  },
  methods: {
        onClick: function (event) {
            this.$refs.dropdownObj.ej2Instances.value = null;
            this.$refs.dropdownObj.dataBind();
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
