---
title: "Variatons"
component: "Sidebar"
description: "The different types in type property of the sidebar gives flexibility to view or hide the content (primary/secondary) over/above the main content by pushing, sliding, or overlaying it."
---

# Types

The Sidebar component's expand behaviour can be modified based on the purpose of use.

## Expanding types of sidebar

The Sidebar can be set to initialize based on four different types that are consistent with the main component as explained below. When `dataBind` is invoked, this applies the pending property changes immediately to the component.

 | Item | Description |
|-----|-----|
| [`Over`](../api/sidebar#type) | Sidebar floats over the main content area.|
| [`Push`](../api/sidebar#type) | Sidebar pushes the main content area to appear side-by-side, and shrinks the main content within the screen width.|
| [`Slide`](../api/sidebar#type) |Sidebar translates the x and y positions of main content area based on the Sidebar width. The main content area will not be adjusted within the screen width. |
| [`Auto`](../api/sidebar#type) | Sidebar with `Over` type in mobile resolution, and `Push` type in other higher resolutions. |

> `Auto` is the default expand mode.

In the following sample, the types of Sidebar are demonstrated.

{% tab template="sidebar/position", isDefaultActive=true %}

```html
<template>
<div id="app">
<ejs-sidebar id="default-sidebar" ref="sidebar" :type="type" :target="target">
    <div class="title"> Sidebar content</div>
    <div class="sub-title">
        Click the button to close the Sidebar.
    </div>
    <div class="center-align">
        <button ejs-button id="close" v-on:click="closeClick" class="e-btn close-btn">Close Sidebar</button>
    </div>
</ejs-sidebar>
<div id="head">
    <ejs-button id="toggle" ref="togglebtn"  cssClass="e-flat" iconCss="e-icons burg-icon" isToggle="true" v-on:click.native="btnClick" >Open</ejs-button>
</div>
<div>
<div id="maincontent" class="content">
    <div>
        <div class="title">Main content</div>
        <div class="rows">
            <div class="row">
                <ejs-radiobutton id='push' label="Push" name="type"  :change="changeHandler" ></ejs-radiobutton>
            </div>
            <div class="row">
                <ejs-radiobutton id='slide'  label="Slide" name="type" :change="changeHandler"></ejs-radiobutton>
            </div>
            <div class="row">
                <ejs-radiobutton id='over'  label="Over" name="type"  :change="changeHandler"></ejs-radiobutton>
            </div>
            <div class="row">
                <ejs-radiobutton id='auto'  label="Auto" name="type" checked="true" :change="changeHandler"></ejs-radiobutton>
            </div>
        </div>
    </div>
</div>
</div>
</div>
<!--end of main content declaration -->
</template>
<script>
import Vue from 'vue';
import { SidebarPlugin } from '@syncfusion/ej2-vue-navigations';
import { ButtonPlugin,RadioButtonPlugin} from '@syncfusion/ej2-vue-buttons';
import { enableRipple } from '@syncfusion/ej2-base';
Vue.use(SidebarPlugin);
Vue.use(ButtonPlugin);
Vue.use(RadioButtonPlugin);

export default {
    data () {
        return {
         type :'Push',
         target : '.content'
        }
    },
    methods: {
        btnClick: function(){
        if(this.$refs.togglebtn.$el.classList.contains('e-active')){
            this.$refs.togglebtn.Content = 'Open';
            this.$refs.sidebar.hide();
        }
        else{
            this.$refs.togglebtn.Content = 'Close';
            this.$refs.sidebar.show();
        }
    },
        closeClick: function() {
         this.$refs.sidebar.hide();
         this.$refs.togglebtn.$el.classList.remove('e-active');
         this.$refs.togglebtn.Content = 'Open';
        },
        changeHandler:  function(args) {
        if(args.event.target.id == 'over') {
            this.type = 'Over';
            this.dataBind();
        } else if (args.event.target.id == 'push') {
             this.type = 'Push';
             this.dataBind();
        } else if (args.event.target.id == 'slide') {
             this.type = 'Slide';
             this.dataBind();
        } else {
             this.type = 'Auto';
             this.dataBind();
        }
    }
    }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
.rows{
    margin:auto;
    text-align:center;
}

.row{
    padding:10px;
    margin:auto;
}

.header {
    width:100%;
    height: 40px;
    font-size:20px;
    line-height: 40px;
    font-weight: 500;
    background: #eee;
    display: inline-block;
}

.center-align {
    text-align: center;
    padding: 20px;
}

.burg-icon:before{
    content: '\e10d';
    font-size:16px;
}

.title {
    text-align: center;
    font-size: 20px;
    padding: 15px;
}

#head {
    border: 1px solid #424242;
    border-bottom-color:transparent;
    background:#00897B;
}

#toggle,#container .e-btn.e-info:hover,
#toggle:focus {/* csslint allow:   adjoining-classes*/
    background: #00695C;
    box-shadow: none;
    border-radius: 0;
    height: 39px;
    width: 100px;
}

#close,#close:hover,#close:active,#close:focus{ /* csslint allow: adjoining-classes*/
    background: #fafafa;
    color:black
}

.sub-title {
    text-align: center;
    font-size: 16px;
    padding: 10px;
}

.radiobutton{
    display:inline-block;
    padding:10px;
}

.center {
    text-align: center;
    display: none;
    font-size: 13px;
    font-weight: 400;
    margin-top: 20px;
}

.content{
    height:305px;
    border: 1px solid grey;
}

  #default-sidebar {
    background-color: #26A69A;
    color: #ffffff;
}

.close-btn:hover {
    color: #fafafa;
}

#toggle {
    color:white;
}

@font-face {
    font-family: 'e-icons';
    src: url(data:application/x-font-ttf;charset=utf-8;base64,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) format('truetype');
    font-weight: normal;
    font-style: normal;
}

</style>
```

{% endtab %}

## See Also

* [How to add sidebar with custom animation](./how-to/sidebar-with-variation-animation)
* [How to add multiple sidebar](./how-to/multiple-sidebar)
