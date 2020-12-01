# Model Binding

## Integrating Vue model binding in Syncfusion Vue UI components

Syncfusion Vue UI components support model binding through the `v-model` directive.
The model binding support in Syncfusion Vue components uses custom 'modelchanged' event, which is used to notify Vue that a model is changed.

* Syncfusion Vue UI components that are initialized from form elements support model binding.

Refer to the following code snippet.

{% tab template="common/model", isDefaultActive=true %}

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
