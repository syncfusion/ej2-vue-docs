---
title: "How To"
component: "Card"
description: "This example demonstrates how to manually customize title placement anywhere over an image in the Essential JS 2 Card control."
---

# Customize the card image title position

Card Image titles are placed as always Bottom-Left Corner only, You can manually customize to placing titles anywhere over the image by
adding styles.

{% tab template="card/how-to/card_image", isDefaultActive=true %}

```html
<template>
  <div id="app">
       <div>
            <div class="e-card">
                <div class="e-card-image">
                    <div class="e-card-title">Node.js</div>
                </div>
                <div class="e-card-content">
                    Node.js is a wildly popular platform for writing web applications that has revolutionized web development in many ways, enjoying
                    support across the open source community as well as industry.
                </div>
        </div>
    </div>
    <div style="Margin: 5px 0;width:300px">
      <ejs-dropdownlist id='title_position' :dataSource='dropData' placeholder="Select Position" :change="changed"></ejs-combobox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(DropDownListPlugin);

export default {
  name: 'app',
data: function() {
    return {
      dropData: ['BottomLeft', 'TopLeft', 'TopRight', 'BottomRight'];
    };

  }, methods:{

 changed: function(e) {

    var cardEle = document.querySelector('.e-card');
    var titleEle = cardEle.querySelector('.e-card-image .e-card-title');
    titleEle.className = ''
    titleEle.classList.add('e-card-title');
    titleEle.classList.add(e.value.toLowerCase());
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

.e-card-image {
    background: url('./sample.jpg');
    height: 164px;
}

.e-card {
    width: 200px;
    margin: auto;
}

.topleft {
    top: 0;
    bottom: auto !important;
}

.topright {
    top: 0;
    text-align: right;
    bottom: auto !important;
}

.bottomright {
    bottom: 0;
    right: 0;
    text-align: right;
}
</style>
```

{% endtab %}
