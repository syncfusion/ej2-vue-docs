---
title: "Integrate other component inside the card"
component: "Card"
description: "This example demonstrates how to integrate other Essential JS 2 controls inside the Essential JS 2 Card control."
---

# Integrate other component inside the card

You can integrate any component inside the card element. Here ListView component is placed inside the card for showcasing the To-Do list.

{% tab template="card/how-to/card_component", isDefaultActive=true %}

```html
<template>
  <div id="app">
        <div style="margin: 50px;">
            <!--element which is going to render the Card-->
            <div tabindex="0" class="e-card" id="basic">
                <div class="e-card-title">To-Do List</div>
                <div class="e-card-separator"></div>
                <div class="e-card-content">
                    <div id='element'></div>
                </div>
            </div>
        </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ListView } from '@syncfusion/ej2-lists';

export default {
  name: 'app',
  data(){


  },mounted(){

//Initialize ListView component
var listviewInstance: ListView = new ListView({
    dataSource: [
    {  todoList: 'Pay Bills' },
    {  todoList: 'Call Chris' },
    {  todoList: 'Meet Andrew' },
    {  todoList: 'Visit Manager' },
    {  todoList: 'Customer Meeting' },
],
    //map the appropriate columns to fields property
    fields: { text: 'todoList' },
},"#element");
  }
  }
}
</script>
<style>
  @import '../../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css';

#container {
    visibility: hidden;
}

#loader {
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
