---
title: "Drop-down list How to close popup on scroll"
component: "DropDownList"
description: "This section explains on how to close popup on scroll in the Syncfusion Vue drop-down list component."
---

# Close the popup on scroll

By using the `hidePopup` method in DropDownList, you can close the popup on scroll when triggered the windows scroll event.

The following example demonstrate about how to close the popup on scroll.

{% tab template="drop-down-list/how-to/scroll", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div style ='padding: 50px'>
        <h4> You can close the opened popup by scroll the page.</h4>
    </div>
    <div id='container' style="margin:0 auto; width:250px;">
        <br>
        <ejs-dropdownlist id='dropdownlist' popupHeight="220px" :dataSource='sportsData' placeholder='Select a game'></ejs-dropdownlist>
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
      sportsData: ['Badminton', 'Cricket', 'Football', 'Golf', 'Tennis']
    }
  }
}

document.onscroll = () =>  {
            var dropObj = document.getElementById("dropdownlist"); //to get dropdown list object
            dropObj.ej2_instances[0].hidePopup(); // hide the popup using hidePopup method
};
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  body {
  height: 500px;
}
</style>
```

{% endtab %}