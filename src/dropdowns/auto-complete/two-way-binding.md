---
title: "Two Way Binding"
component: "AutoComplete"
description: "This section for Vue AutoComplete component demonstrates two-way binding."
---

# Two-Way Binding

Two-way binding can be achieved by using the `v-model` directive in Vue. In the following sample, when you change the value in one AutoComplete component, v-model will automatically update the value in the other AutoComplete.

The following example demonstrates how to set the `two-way-binding` in the AutoComplete.

{% tab template="auto-complete/two-way", isDefaultActive=true %}

```html
<template>
<div id="app">
    <div id="wrapper1">
          <ejs-autocomplete id='first':dataSource='sportsData' :fields='fields' :placeholder="waterMark" v-model="value" ></ejs-autocomplete>
    </div>
    <div id="wrapper2">
          <ejs-autocomplete id='second' :dataSource='sportsData' :fields='fields' :placeholder="waterMark" v-model="value" ></ejs-autocomplete>
    </div>
</div>
</template>
<script>
import Vue from 'vue';
import { AutoCompletePlugin } from '@syncfusion/ej2-vue-dropdowns';

Vue.use(AutoCompletePlugin);
export default {
  name: 'app',
   data () {
    return {
      waterMark : 'Select a game',
      value: null,
      sportsData: [
     { Id: 'Game1', Game: 'Badminton' },
    { Id: 'Game2', Game: 'Basketball' },
    { Id: 'Game3', Game: 'Cricket' },
    { Id: 'Game4', Game: 'Football' },
    { Id: 'Game5', Game: 'Golf' },
    { Id: 'Game6', Game: 'Hockey' },
    { Id: 'Game7', Game: 'Rugby' },
    { Id: 'Game8', Game: 'Snooker' }
    ],
    fields: { value: 'Game' }
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
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