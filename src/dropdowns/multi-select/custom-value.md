---
title: "Multiselect Custom value"
component: "MultiSelect"
description: "This section for Syncfusion vue multiselect component demonstrates the addition of a new value that is not present in the predefined list."
---

# CustomValue

The MultiSelect allows user to add a new non-present option to the component value when [`allowCustomValue`](../api/multi-select/#allowcustomvalue) is enabled.
while selecting the new custom value [`customValueSelection`](../api/multi-select/#customvalueselection) event will be triggered.

The following sample demonstrates configuration of custom value support with the MultiSelect component.

{% tab template="multi-select/custom-value", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-multiselect id='multiselect' :dataSource='sportsData' :fields='fields' :allowCustomValue='allowCustomValue' placeholder="Select a game"></ejs-multiselect>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { MultiSelectPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(MultiSelectPlugin);
export default {
  data (){
    return {
      sportsData: [
        { Id: 'game1', Game: 'Badminton' },
        { Id: 'game2', Game: 'Football' },
        { Id: 'game3', Game: 'Tennis' }
      ],
      fields : { text: 'Game', value: 'Id' },
      allowCustomValue : true
    }
  }
}

</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
</style>
```

{% endtab %}
