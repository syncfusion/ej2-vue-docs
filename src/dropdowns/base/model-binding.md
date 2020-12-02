# Model Binding

## Integrating Vue Model Binding in Essential JS 2 Vue Components

Essential JS 2 for Vue Components support Model Binding through `v-model` directive.
Model Binding support in Essential JS2 Vue Components uses custom 'modelchanged' event,
which is used to notify Vue that a model is changed.

* Essential JS 2 for Vue Components which are initialized from Form Elements support Model Binding.

Refer the code snippet given below.

{% tab template="base/model", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <ejs-checkbox v-model="checked" label="EJ2 Vue Checkbox" :checked="checked" />
    <p>
      Checkbox State: <span id="checked-state" v-text="checked" ></span>
    </p>
  </div>
</template>
<script>
import Vue from 'vue';
import { CheckBoxPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.use(CheckBoxPlugin);

export default {
  data () {
    return {
      checked: true
    }
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  #app {
    color: #008cff;
    height: 40px;
    left: 45%;
    position: absolute;
    top: 45%;
    width: 30%;
  }
</style>
```

{% endtab %}
