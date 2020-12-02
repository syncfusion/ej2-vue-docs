# Multiple sidebar

Two Sidebars can be initialized in a web page with same main content.
Sidebars can be initialized on right side or left side of the main content using [position](../../api/sidebar#position) property.

>The HTML element with class name `e-main-content` will be considered as the
main content and both the Sidebars will behave as side content to this main content area.

{% tab template="sidebar/howto", isDefaultActive=true %}

```html
<template>
<div id="app">
        <ejs-sidebar id="default" ref="leftsidebar" :width="leftWidth" :type="leftType">
          <div class="title"> Left Sidebar content</div>
        </ejs-sidebar>

        <ejs-sidebar id="default1" ref="rightsidebar" :width="width"  :position="position"
           :type="type">
           <div class="title">Right Sidebar content</div>
        </ejs-sidebar>
    <div class="e-main-content">
           <p>Place your main content here.....</p>
        <div id="button-align">
            <button ejs-button id="toggle" class="e-btn e-info" v-on:click="leftToggle">Toggle Sidebar1</button>
        </div>
        <div id="button-align">
          <button ejs-button id="toggle2" class="e-btn e-info" v-on:click="rightToggle">Toggle Sidebar2</button>
        </div>
    </div>
</div>
</template>
<script>
import Vue from 'vue';
import { SidebarPlugin } from '@syncfusion/ej2-vue-navigations';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

Vue.use(SidebarPlugin);
Vue.use(ButtonPlugin);
export default {
       data () {
          return {
         leftWidth: '250px'
         leftType: 'Push'
         width : '250px',
         position: 'Right',
         type: 'Push'
     }
     },
     methods: {
        leftToggle :function() {
          this.$refs.leftsidebar.toggle();
        },
        rightToggle: function() {
         this.$refs.rightsidebar.toggle();
        }
    }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";

.e-main-content{
    text-align: center;
    height: 100vh;
    background: #f5f5f5;
    font-size: 16px;
    padding: 100px;
}

#button-align{
    padding: 15px;
}

.title {
    text-align: center;
    font-size: 20px;
    padding: 15px;
}

#default,#default1 {
    background-color: rgb(25, 118, 210);
    color: #ffffff;
    overflow: hidden;
}
</style>
```

{% endtab %}