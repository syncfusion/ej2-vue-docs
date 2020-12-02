---
title: "Drop-down list How to remove list item"
component: "DropDownList"
description: "This section explains on how to remove the list item of the Syncfusion Vue drop-down list component."
---

# Remove an item from DropDownList

The following example demonstrate about how to remove an item from DropDownList.

{% tab template="drop-down-list/how-to/valuechange", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:0 auto; width:250px;">
        <br>
        <ejs-dropdownlist id='dropdownlist' ref="dropdownObj" :dataSource='sportsData' :fields='fields' placeholder='Select a game'></ejs-dropdownlist>
    </div>
    <div style='padding: 50px 0'>
      <button id='first' class="e-control e-btn" v-on:click="remove"> Remove 0th item</button>
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
      sportsData: [
            { Id: 'game1', Game: 'Badminton' },
            { Id: 'game2', Game: 'Football' },
            { Id: 'game3', Game: 'Tennis' }
      ],
      fields : { text: 'Game', value: 'Id' }
    }
  },
  methods: {
        remove: function (event) {
            if(this.$refs.dropdownObj.getItems().length > 1) {
                this.$refs.dropdownObj.getItems()[0].remove();
                this.$refs.dropdownObj.dataSource.splice(0, 1);
            } else {
              this.sportsData = [];
            }
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