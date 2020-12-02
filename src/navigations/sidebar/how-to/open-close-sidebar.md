# Open and close the Sidebar

Opening and closing the Sidebar can be achieved with built-in public methods.

* [show()](../../api/sidebar#show): Method to open the Sidebar.
* [hide()](../../api/sidebar#hide): Method to close the Sidebar.
* [toggle()](../../api/sidebar#toggle): Method to toggle between open and close states of the Sidebar.

In the following sample, toggle method has been used to show or hide the Sidebar on button click.

{% tab template="sidebar/howto", isDefaultActive=true %}

```html
<template>
<div id="app">
        <ejs-sidebar id="default-sidebar" ref="sidebar" :open="open" :close="close" :showBackdrop="showBackdrop">
    <div class="title"> Sidebar content</div>
    <div class="sub-title">
        Click the button to close the Sidebar.
    </div>
    <div class="center-align">
        <button ejs-button id="close" v-on:click="closeClick" class="e-btn close-btn">Close Sidebar</button>
    </div>
</ejs-sidebar>
<div>
    <div>
        <div class="title">Main content</div>
        <div class="sub-title"> Click the button to open/close the Sidebar.
            <div style="padding:20px" class="center-align">
                <button ejs-button id="toggle" class="e-btn e-info" v-on:click="toggleClick">Toggle Sidebar</button>
            </div>

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
            showBackdrop :false,
        };
     },
     methods: {
        toggleClick :function() {
          this.$refs.sidebar.toggle();
        },
        closeClick: function() {
         this.$refs.sidebar.hide();
        },
        close:function() {
            console.log("sidebar closed");
        },
        open:function() {
            console.log("sidebar opened");
        }
    }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";

.center-align {
    text-align: center;
    padding: 20px;
}

.title {
    text-align: center;
    font-size: 20px;
    padding: 15px;
}

.sub-title {
    text-align: center;
    font-size: 16px;
    padding: 10px;
}

.center {
    text-align: center;
    display: none;
    font-size: 13px;
    font-weight: 400;
    margin-top: 20px;
}

#default-sidebar {
    background-color: rgb(25, 118, 210);
    color: #ffffff;
}

.close-btn:hover {
    color: rgba(0, 0, 0, .87);
    background-color: #fafafa;
}

</style>
```

{% endtab %}