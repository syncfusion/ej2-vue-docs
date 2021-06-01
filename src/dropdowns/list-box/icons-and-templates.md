---
title: "ListBox with icons and customization"
component: "ListBox"
description: "Vue ListBox supports icons, images and customization of each list elements."
---

# Icons and Customization

## Icons

To place the icon on a list box, set the [`iconCss`](../api/list-box/fieldSettingsModel/#iconcss) property to `e-icons` with the required icon CSS. By default, the icon is positioned to the left side of the list.

In the following sample, icon classes are mapped with `iconCss` field.

{% tab template="list-box/getting-started/getting-started", isDefaultActive=true %}

```html

<template>
  <div id="app">
    <div id='container' style="margin:10px auto 0; width:250px;">
        <ejs-listbox :dataSource='data' :fields="fields" ></ejs-listbox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ListBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(ListBoxPlugin);
export default {
  data (){
    return {
       data: [
    { text: 'Account Settings', iconCss: 'e-list-icons e-list-user-settings' },
    { text: 'Address Book', iconCss: 'e-list-icons e-list-address-book' },
    { text: 'Delete', iconCss: 'e-list-icons e-list-delete' },
    { text: 'Forward', iconCss: 'e-list-icons e-list-forward' },
    { text: 'Reply', iconCss: 'e-list-icons e-list-reply' },
    { text: 'Reply All', iconCss: 'e-list-icons e-list-reply-all' },
    { text: 'Save All Attachments', iconCss: 'e-list-icons e-list-save-all-attachments' },
    { text: 'Save As', iconCss: 'e-list-icons e-list-icon-save-as' },
    { text: 'Touch/Mouse Mode', iconCss: 'e-list-icons e-list-touch' },
    { text: 'Undo', iconCss: ' e-list-icons e-list-undo' }
];
fields: { text: "text", iconCss: "iconCss" }
    }
  }
}

</script>

<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";

@font-face {
  font-family: 'e-listbox-icons';
  src:
  url(data:application/x-font-ttf;charset=utf-8;base64,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) format('truetype');
  font-weight: normal;
  font-style: normal;
}
  
.e-list-icons {
  font-family: 'e-listbox-icons';
  speak: none;
  font-style: normal;
  font-weight: normal;
  font-variant: normal;
  text-transform: none;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.e-list-touch:before {
  content: "\e700";
}

.e-list-reply-all:before {
  content: "\e701";
}
.e-list-reply:before {
  content: "\e702";
}

.e-list-save-all-attachments:before {
  content: "\e703";
}

.e-list-icon-save-as:before {
  content: "\e704";
}

.e-list-user-settings:before {
  content: "\e705";
}

.e-list-address-book:before {
  content: "\e706";
}

.e-list-delete:before {
  content: "\e707";
}

.e-list-forward:before {
  content: "\e708";
}

.e-list-undo:before {
  content: "\e709";
}

</style>

```

{% endtab %}

## Templates

ListBox items can be customized according to the requirement using [`itemTemplate`](../api/list-box/#itemtemplate) property.

In the following sample, the items in the cart are displayed using list box template,

{% tab template="list-box/getting-started/getting-started", isDefaultActive=true %}

```html

<template>
  <div id="app">
    <div id='container' style="margin:10px auto 0; width:250px;">
        <ejs-listbox :dataSource='data' :itemTemplate= "itemtemplate" ></ejs-listbox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ListBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(ListBoxPlugin);
export default {
  data (){
    return {
    itemtemplate: "<div class='list-wrapper'><span class='${pic} e-avatar e-avatar-xlarge e-avatar-circle'></span><span class='text'>${text}</span><span class='description'>${description}</span></div>",
       data: [
    { text: 'JavaScript', pic: 'javascript', description: 'It is a lightweight interpreted or JIT-compiled programming language.' },
    { text: 'TypeScript', pic: 'typeScript', description: 'It is a typed superset of Javascript that compiles to plain JavaScript.' },
    { text: 'Angular', pic: 'angular', description: 'It is a TypeScript-based open-source web application framework.' },
    { text: 'React', pic: 'react', description: 'A JavaScript library for building user interfaces. It can also render on the server using Node.' },
    { text: 'Vue', pic: 'vue', description: 'A progressive framework for building user interfaces. it is incrementally adoptable.' }
];
    }
  }
}

</script>

<style>

@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";

.e-listbox-wrapper {
  margin: auto;
  max-width: 400px;
  box-sizing: border-box;
}

#container {
  box-sizing: border-box;
}

#container .e-listbox-wrapper:not(.e-list-template) .e-list-item {
  padding: 0;
  position: unset;
  cursor: pointer;
  height: 76px;
  line-height: normal;
}

.list-wrapper {
    height: inherit;
    position: relative;
    padding: 14px 12px 14px 78px;
}

.list-wrapper .text,
.list-wrapper .description {
  display: block;
  margin: 0;
  padding-bottom: 3px;
  white-space: normal;
}

.list-wrapper .description {
  font-size: 12px;
  font-weight: 500;
}

#container .e-listbox-wrapper .list-wrapper .text {
  font-weight: bold;
  font-size: 13px;
}

.list-wrapper .e-avatar {
    position: absolute;
    left: 5px;
    background-color: transparent;
    font-size: 22px;
    top: calc(50% - 33px);
}

.javascript {
  background-image: url('jses5-1.svg');
  width: 70px;
  height: 60px;
  background-repeat: no-repeat;
}

.typeScript {
  background-image: url('javascript1.svg');
  width: 70px;
  height: 60px;
  background-repeat: no-repeat;
}

.angular {
  background-image: url('angular1.svg');
  width: 70px;
  height: 60px;
  background-repeat: no-repeat;
}

.vue {
  background-image: url('vue.svg');
  width: 70px;
  height: 60px;
  background-repeat: no-repeat;
}

.react {
  background-image: url('react.svg');
  width: 70px;
  height: 60px;
  background-repeat: no-repeat;
}

</style>

```

{% endtab %}