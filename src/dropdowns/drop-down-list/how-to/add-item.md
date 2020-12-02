---
title: "Drop-down list How to add list item"
component: "DropDownList"
description: "This section explains on how to add list item to the Syncfusion Vue drop-down list component."
---

# Add item in between in DropDownList

You can add item in between based on item [index](../../api/drop-down-list/#index).
If you add new item without item index, item will be added as last item in list.

To add and remove items dynamically in Vue DropDownList component, you can check on this video:

`youtube:xJaCPILBK9k`

The following example demonstrate how to add item in between in DropDownList.

{% tab template="drop-down-list/how-to/valuechange", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:0 auto; width:250px;">
        <br>
        <ejs-dropdownlist id='dropdownlist' ref='dropdown' :index='index' :dataSource='sportsData' :fields='fields' placeholder='Select a game'></ejs-dropdownlist>
    </div>
    <div style='padding: 50px 0'>
      <button id='first' class="e-control e-btn" v-on:click="onFirst"> add item (Hockey) in first</button>
    </div>
    <div style='padding-left: 50px 0'>
      <button id='between' class="e-control e-btn" v-on:click="onMiddle"> add item (Golf) in between</button>
    </div>
    <div style='padding: 50px 0'>
      <button id='last' class="e-control e-btn" v-on:click="onLast"> add item (Cricket) in last</button>
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
      fields : { text: 'Game', value: 'Id' },
      index : 2
    }
  },
  methods: {
        onFirst: function (event) {
            this.$refs.dropdown.addItem({Id: 'game0', Game: 'Hockey'}, 0);
        },
        onMiddle: function (event) {
            this.$refs.dropdown.addItem({Id: 'game4', Game: 'Golf'}, 2);
        },
        onLast: function (event) {
            this.$refs.dropdown.addItem({Id: 'game5', Game: 'Cricket'});
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