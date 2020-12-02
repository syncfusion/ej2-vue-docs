---
title: "Enable or disable items in list box"
component: "ListBox"
description: "Vue ListBox component supports customization of menu items so that the items can be enabled or disabled."
---

# Enable or disable items

To enable or disable items in the list box, [`enableItems`](../api/list-box/#enableitems) method can be used. In the following example, the `Bugatti Veyron Super Sport` and `SSC Ultimate Aero` items are disabled by default and by clicking `Enable Items` buttons, the disabled items will be enabled.

{% tab template="list-box/getting-started/getting-started", isDefaultActive=true %}

```html

<template>
  <div id="app">
    <div id='container' style="margin:10px auto 0; width:250px;">
        <ejs-listbox id="listbox" :dataSource='data' :created="onCreated" ></ejs-listbox>
        <button id="enableitem" class="e-btn" v-on:click="enableitem">Enable Items</button>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ListBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(ListBoxPlugin);
export default {
  data (){
    return {
       data: [
    { text: 'Hennessey Venom', id: 'list-01' },
    { text: 'Bugatti Chiron', id: 'list-02' },
    { text: 'Bugatti Veyron Super Sport', id: 'list-03' },
    { text: 'SSC Ultimate Aero', id: 'list-04' },
    { text: 'Koenigsegg CCR', id: 'list-05' },
    { text: 'McLaren F1', id: 'list-06' },
    { text: 'Aston Martin One- 77', id: 'list-07' },
    { text: 'Jaguar XJ220', id: 'list-08' },
    { text: 'McLaren P1', id: 'list-09' },
    { text: 'Ferrari LaFerrari', id: 'list-10' },
];
    }
  },
  methods:{
  onCreated: function(e){
    var listboxobj= document.getElementById("listbox").ej2_instances[0];
    listboxobj.enableItems(["Bugatti Veyron Super Sport", "SSC Ultimate Aero"],false)
}

  enableitem: function(e){
    var listboxobj1= document.getElementById("listbox").ej2_instances[0];
    listboxobj1.enableItems(["Bugatti Veyron Super Sport", "SSC Ultimate Aero"],true)
  }
}
}

</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
</style>

```

{% endtab %}