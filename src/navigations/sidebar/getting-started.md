---
title: "Getting Started"
component: "Sidebar"
description: "This getting started section briefly explains how to create a sidebar component in application."
---

# Getting Started

This section briefly explains how to create a simple **Sidebar** component, and
configure it in VueJS using Essential JS 2 [quickstart](https://github.com/syncfusion/ej2-quickstart)
&nbsp;seed repository.

## Dependencies

The following list of dependencies are required to use the Sidebar component in your application.

```js
|-- @syncfusion/ej2-vue-navigations
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-vue-base
    |-- @syncfusion/ej2-navigations
        |-- @syncfusion/ej2-inputs
            |-- @syncfusion/ej2-splitbuttons
        |-- @syncfusion/ej2-lists
        |-- @syncfusion/ej2-popups
            |-- @syncfusion/ej2-buttons
```

## Get Started with Vue CLI

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your vue applications.
To install Vue CLI use the following command.

```bash
npm install -g @vue/cli
npm install -g @vue/cli-init
```

Start a new project using below Vue CLI command.

```bash
vue init webpack-simple quickstart

cd quickstart
npm install

```

## Adding Syncfusion packages

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.
You can choose the component that you want to install. For this application, we are going to use Sidebar component.

To install Sidebar component, use the following command

```bash
npm install @syncfusion/ej2-vue-navigations --save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.
* Vue.use()
* Vue.component()

### Using Vue.use()

Import the Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { SidebarComponent, SidebarPlugin } from '@syncfusion/ej2-vue-navigations';

Vue.component(SidebarPlugin.name, SidebarComponent);
```

> By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Creating Vue Sample

Add the EJ2 Vue Sidebar using `<ejs-sidebar>` to the `<template>` section of the `App.vue` file in src directory,
the content attribute of the Sidebar component is provided as name in data option in the `<script>` section.

```html
<template>
    <div id="app">
        <ejs-sidebar>
              <div class="title"> Sidebar content</div>
        </ejs-sidebar>
  </div>
</template>
<script>
import Vue from 'vue';
import { SidebarPlugin } from '@syncfusion/ej2-vue-navigations';

Vue.use(SidebarPlugin);
export default {
}
</script>
```

## Adding CSS Reference

To render the Sidebar component, need to import Sidebar and its dependent component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
</style>
```

>Note: If you want to refer the combined component styles, please make use of our [`CRG`](https://crg.syncfusion.com/) (Custom Resource Generator) in your application.

## Running the Application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

{% tab template="sidebar/getting-started", isDefaultActive=true %}

```html
<template>
<div id="app">
    <div class="wrapper">
        <ejs-sidebar id="default-sidebar">
           <div class="title"> Sidebar content</div>
        </ejs-sidebar>
        <div>
           <div class="title">Main content</div>
                <div class="sub-title">Content goes here.</div>
            </div>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { SidebarPlugin } from '@syncfusion/ej2-vue-navigations';

Vue.use(SidebarPlugin);
export default {
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";

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
  #default-sidebar {
    background-color: rgb(25, 118, 210);
    color: #ffffff;
}
</style>
```

{% endtab %}

## Enable backdrop

Enabling the [showBackdrop](../api/sidebar#showbackdrop) in the Sidebar component will prevent
the main content from user interactions, when it is in expanded state.
Here, the DOM elements will not get changed. It only closes the main content by covering with a black backdrop overlay and focuses the Sidebar in the screen. Sidebar can be rendered with specific width by setting `width` property

{% tab template="sidebar/backdrop", isDefaultActive=true %}

```html
<template>
<div id="app">
    <div class="wrapper">
        <ejs-sidebar id="default-sidebar" ref="sidebar" :showBackdrop="showBackdrop" :closeOnDocumentClick="closeOnDocumentClick">
           <div class="title"> Sidebar content</div>
            <div class="sub-title">
               Click the button to close the Sidebar.
            </div>
            <div class="center-align">
               <button  ejs-button  id="close" v-on:click="closeClick"  class="e-btn close-btn">Close Sidebar</button>
            </div>
        </ejs-sidebar>
        <div>
            <div class="title">Main content</div>
                <div class="sub-title"> Click the button to open/close the Sidebar.</div>
                   <div style="padding:20px" class="center-align">
                       <button ejs-button id="toggle"  class="e-btn e-info" v-on:click="toggleClick" >Toggle Sidebar</button>
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
Vue.use(SidebarPlugin);
Vue.use(ButtonPlugin);

export default {
     data () {
        return {
          showBackdrop :true,
          closeOnDocumentClick:true,
        }
    },
    methods: {
        toggleClick :function() {
          this.$refs.sidebar.toggle();
        },
        closeClick: function() {
         this.$refs.sidebar.hide();
        }
    }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
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
    color: #fafafa;
}
</style>
```

{% endtab %}

## Position

Positioning the Sidebar to the right or left of the main content can be achieved by using the [position](../api/sidebar#position) property. If the position is not set, the Sidebar will expand from the left to the body element. [`enablePersistence`](../api/sidebar#enablepersistence) will persist the component's state between page reloads. [`change`](../api/sidebar#change) event will be triggered when the state(expand/collapse) of the component is changed.

{% tab template="sidebar/position", isDefaultActive=true %}

```html
<template>
<div id="app">
    <ejs-sidebar id="default-sidebar" ref="sidebar" :type="type" :target="target" :position="position" :enablePersistence="enablePersistence">
      <div class="title"> Sidebar content</div>
       <div class="sub-title">
        Click the button to close the Sidebar.
    </div>
    <div class="center-align">
        <button ejs-button id="close" v-on:click="closeClick" class="e-btn close-btn">Close Sidebar</button>
    </div>
</ejs-sidebar>
<div id="head">
    <ejs-button id="toggle" ref="togglebtn" class="e-btn e-info"  cssClass="e-flat" iconCss="e-icons burg-icon" isToggle="true" v-on:click.native="btnClick">Open</ejs-button>
</div>
<div>
<div id="maincontent" class="content">
    <div>
        <div class="title">Main content</div>
            <div class="rows">
                <div class="row">
                  <ejs-radiobutton id="left" label='Left' name='state' checked='true' :change="positionChange"></ejs-radiobutton>
                </div>
                <div class="row">
                  <ejs-radiobutton id="right" label='Right' name='state' :change="positionChange"></ejs-radiobutton>
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
import { ButtonPlugin ,RadioButtonPlugin } from '@syncfusion/ej2-vue-buttons';
import { enableRipple } from '@syncfusion/ej2-base';
Vue.use(SidebarPlugin);
Vue.use(ButtonPlugin);
Vue.use(RadioButtonPlugin);
export default {
    data () {
        return {
         type :'Push',
         target : '.content',
         position : 'Left',
         enablePersistence: true
        }
    },
    methods: {
        positionChange:function(args) {
          this.position = args.event.target.id == "left" ? "Left" : "Right";
        },
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
        }
    }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
.rows{
    margin:auto;
    text-align:center;
}

.row{
    display:inline-block;
    padding:10px;
    margin:auto;
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

#toggle,#container .e-btn.e-info:hover,#toggle:focus { /* csslint allow: adjoining-classes*/
    background:#00695C;
    box-shadow:none;
    border-radius:0;
    height:39px;
    width:100px;
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

.content{
    height:305px;
    border: 1px solid grey;
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

## Animate

Animation transitions can be set while expanding or collapsing the Sidebar using the [`animate`](../api/sidebar#animate) property. By default , [`animate`](../api/sidebar#animate) property is set to true. [`enableRTL`](../api/sidebar#enablertl) will display the sidebar in the right-to-left direction.

{% tab template="sidebar/animate", isDefaultActive=true %}

```html
<template>
<div id="app">
    <div class="wrapper">
        <ejs-sidebar id="default-sidebar" ref="sidebar" :type="type" :width="width" :animate="animate" :enableRtl="enableRtl">
           <div class="title"> Sidebar content</div>
            <div class="sub-title">
               Click the button to close the Sidebar
            </div>
            <div class="center-align">
               <button  ejs-button  id="close" v-on:click="closeClick"  class="e-btn close-btn">Close Sidebar</button>
            </div>
        </ejs-sidebar>
        <div>
            <div class="title">Main content</div>
                <div class="sub-title"> Click the button to open/close the Sidebar.</div>
                   <div style="padding:20px" class="center-align">
                       <button ejs-button id="toggle"  class="e-btn e-info" v-on:click="toggleClick" >Toggle Sidebar</button>
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
Vue.use(SidebarPlugin);
Vue.use(ButtonPlugin);

export default {
     data () {
        return {
            animate:false,
            enableRtl: true,
            width:'280px',
            type:'Push'
        }
    },
    methods: {
        toggleClick :function() {
          this.$refs.sidebar.toggle();
        },
        closeClick: function() {
         this.$refs.sidebar.hide();
        }
    }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
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
    color: #fafafa;
}
</style>
```

{% endtab %}

## Close on document click

Sidebar can be closed on document click by setting [`closeOnDocumentClick`](../api/sidebar#closeondocumentclick) to true. If this property is not set, the Sidebar will not close on document click since its default value is false. Sidebar can be kept opened during rendering using [`isOpen`](../api/sidebar#isopen) property.

{% tab template="sidebar/document-click", isDefaultActive=true %}

```html
<template>
<div id="app">
    <div class="wrapper">
        <ejs-sidebar id="default-sidebar" ref="sidebar" :width="width" :type="type" :isOpen="isOpen" :closeOnDocumentClick="closeOnDocumentClick">
           <div class="title"> Sidebar content</div>
        </ejs-sidebar>
        <div>
            <div class="title">Main content</div>
                <div class="sub-title"> Click the button to open the Sidebar.</div>
                   <div style="padding:20px" class="center-align">
                       <button ejs-button id="toggle"  class="e-btn e-info" v-on:click="toggleClick" >Open Sidebar</button>
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
Vue.use(SidebarPlugin);
Vue.use(ButtonPlugin);

export default {
     data () {
        return {
            closeOnDocumentClick: true,
            isOpen:true,
            type:'Push',
            width:'280px'
        }
    },
    methods: {
        toggleClick :function() {
          this.$refs.sidebar.toggle();
        },
    }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
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
    color: #fafafa;
}
</style>
```

{% endtab %}

## Enable gestures

Expand or collapse the Sidebar while swiping in touch devices using `enableGestures` property. By default, `enableGestures` is set to true.

{% tab template="sidebar/gestures", isDefaultActive=true %}

```html
<template>
<div id="app">
    <div class="wrapper">
        <ejs-sidebar id="default-sidebar" ref="sidebar" :width="width" :type="type" :enableGestures="enableGestures">
           <div class="title"> Sidebar content</div>
            <div class="sub-title">
               Click the button to close the Sidebar.
            </div>
            <div class="center-align">
               <button  ejs-button  id="close" v-on:click="closeClick"  class="e-btn close-btn">Close Sidebar</button>
            </div>
        </ejs-sidebar>
        <div>
            <div class="title">Main content</div>
                <div class="sub-title"> Click the button to open/close the Sidebar.</div>
                   <div style="padding:20px" class="center-align">
                       <button ejs-button id="toggle"  class="e-btn e-info" v-on:click="toggleClick" >Toggle Sidebar</button>
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
Vue.use(SidebarPlugin);
Vue.use(ButtonPlugin);

export default {
     data () {
        return {
            enableGestures: false,
            type:'Push',
            width:'280px'
        }
    },
    methods: {
        toggleClick :function() {
            this.$refs.sidebar.toggle();
        },
        closeClick: function() {
            this.$refs.sidebar.hide();
        }
    }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
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
    color: #fafafa;
}
</style>
```

{% endtab %}

## See Also

* [Sidebar with navigation menu](https://ej2.syncfusion.com/vue/demos/#/material/sidebar/sidebar-menu.html)
* [Sidebar responsive panel](https://ej2.syncfusion.com/vue/demos/#/material/sidebar/responsive-panel.html)
* [Sidebar with listView](./how-to/sidebar-with-listview)