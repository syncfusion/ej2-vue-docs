---
title: "Drop-down list How to detect value change"
component: "DropDownList"
description: "This section explains on how to detect whether the value change happened by manual or programmatic in drop-down list component."
---

# Detect whether the value change happened by manual or programmatic

You can check about whether value change happened by manual or programmatic by
using [change](../../api/drop-down-list/#change) event argument that argument name is `isInteracted`.

The following example demonstrate, how to check whether value change happened by manual or programmatic.

{% tab template="drop-down-list/how-to/change", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:0 auto; width:250px;">
        <br>
        <ejs-dropdownlist id='dropdownlist' ref='dropdown' :dataSource='sportsData' :fields='fields' :change='onChange' placeholder='Select a game'></ejs-dropdownlist>
    </div>
    <div style='margin: 50px'>
      <button id='button' class="e-control e-btn" v-on:click="onClick"> Set value dynamically</button>
    </div>
    <p style='margin: 5px' id='event'> </p>
  </div>
</template>
<script>
import Vue from 'vue';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(DropDownListPlugin);
export default {
  data (){
    return {
      sportsData: [
            { Id: 'game1', Game: 'Badminton' },
            { Id: 'game2', Game: 'Football' },
            { Id: 'game3', Game: 'Tennis' }
      ],
      fields : { text: 'Game', value: 'Id' }
    }
  },
  methods: {
        onClick: function (event) {
            this.$refs.dropdown.ej2Instances.value = 'game3';
        },
        onChange : function(args) {
            let element = document.createElement('p');
            if (args.isInteracted) {
                element.innerText = 'Changes happened by Interaction';
            } else {
                element.innerText = 'Changes happened by programmatic';
            }
            document.getElementById('event').append(element);
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