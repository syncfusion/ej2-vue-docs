---
title: "ListView Customizing Templates"
component: "ListView"
description: "Vue listView allows customization of list item, header, and category group header using template and group header API."
---

# Customizing templates

The ListView component is designed to customize each list items and group title.

## Header template

The ListView header can be customized with the help of [`headerTemplate`](../api/list-view/#headertemplate) property.

To customize header template in your application, set your customized template string to `headerTemplate` property along with [`showHeader`](../api/list-view/#showheader) property as `true` to display the ListView header.

```typescript

let listviewInstance: ListView = new ListView({
     data: listData,
     headerTemplate: '<div class="header-content"><span>Header</span></div>',
     showHeader: true
})

```

In the below example, we have rendered Listview with customized header which contains search, add and sort buttons.

{% tab template="listview/templates/customizing-templates", isDefaultActive=true %}

```html
<template>
  <div class="control-section">
    <div id = 'flat-list'>
    <!-- ListView element -->
    <ejs-listview id='element' :dataSource='data' :headerTemplate='template' showHeader='true'></ejs-listview>
    </div>
  </div>
</template>
<style>

#element {
    display: block;
    max-width: 353px;
    margin: auto;
    border: 1px solid #dddddd;
    border-radius: 3px;
}

#element .e-list-header {
    padding: 0;
}

#element .headerContainer {
    width: 350px;
    height: 48px;
    line-height: 48px;
    background: rgb(2, 120, 215);
    color: white;
    margin-bottom: 3px;
}

.headerContainer .fruitHeader {
    margin-left: 20px;
    font-weight: 500;
    font-size: 22px;
}

.headerContainer #add,
.headerContainer #sort,
.headerContainer #search {
    float: right;
    margin-right: 15px;
    margin-top: 7px;
    background: white;
    color: black
}

.headerContainer .e-search-icon::before {
    content: '\e961';
    color: lightslategray;
}


.headerContainer .e-add-icon::before {
    content: '\e823';
}

.headerContainer .e-sort-icon::before {
    content: '\e840';
}
</style>
<script>
import Vue from "vue";
import { ListViewPlugin } from "@syncfusion/ej2-vue-lists";
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

Vue.use(ListViewPlugin);
Vue.use(ButtonPlugin);

var demoVue = Vue.component("demo", {
  template: `<div class="headerContainer"><span class="fruitHeader">Fruits</span><ejs-button id="search" iconCss='e-icons e-search-icon' cssClass='e-small e-round' isPrimary='true'></ejs-button><ejs-button id="add" iconCss='e-icons e-add-icon' cssClass='e-small e-round' isPrimary='true'></ejs-button><ejs-button id="sort" iconCss='e-icons e-sort-icon' cssClass='e-small e-round' isPrimary='true'></ejs-button></div>`,
  data() {
    return {
      data: {}
    };
  }
});

export default {
  data: function() {
    return {
      data: [
    { text: 'Date', id: '1', imgUrl: './dates.jpg' },
    { text: 'Fig', id: '2', imgUrl: './fig.jpg' },
    { text: 'Apple', id: '3', imgUrl: './apple.png' },
    { text: 'Apricot', id: '4', imgUrl: './apricot.jpg' },
    { text: 'Grape', id: '5', imgUrl: './grape.jpg' },
    { text: 'Strawberry', id: '6', imgUrl: './strawberry.jpg' },
    { text: 'Pineapple', id: '7', imgUrl: './pineapple.jpg' },
    { text: 'Melon', id: '8', imgUrl: './melon.jpg' },
    { text: 'Lemon', id: '9', imgUrl: './lemon.jpg' },
    { text: 'Cherry', id: '10', imgUrl: './cherry.jpg' },
    ],
    template: function () {
                return { template : demoVue}
            }
    };
  }
}
</script>
```

{% endtab %}

## Template

The ListView items can be customized with the help of [`template`](../api/list-view/#template) property.

To customize list items in your application, set your customized template string to `template` property.

```typescript

var demoVue = Vue.component("demo", {
  template: `
    <div class="list-tem"><span>${text}</span></div>`,
  data() {
    return {
      data: {}
    };
  }
});

```

We provided the following built-in CSS classes to customize the list-items. Refer to the following table.

| CSS class        | Description           |
| ------------- |-------------|
| e-list-template, e-list-wrapper | These classes are used to differentiate normal and template rendering, which are mandatory for template rendering. The `e-list-template` class should be added to the root of the ListView element and `e-list-wrapper` class should be added to the template element wrapper <br/><br/> `<ejs-listview :cssClass="e-list-template" :template="template"></ejs-listview>` <br/> `template: '<div class="e-list-wrapper"></div>'`
| e-list-content | This class is used to align list content and it should be added to the content element <br/><br/> `template: '<div class="e-list-wrapper">' +` <br/> `'<span class="e-list-content">ListItem</span>' +`<br/> `'</div>'`|
| e-list-avatar | This class is used for avatar customization. It should be added to the template element wrapper. After adding it, we can customize our element with [Avatar](https://ej2.syncfusion.com/documentation/avatar/getting-started/) classes <br/><br/> `template: '<div class="e-list-wrapper e-list-avatar">' +` <br/> `'<span class="e-avatar e-avatar-circle">MR</span>' +`<br/> `'<span class="e-list-content">ListItem</span>' +`<br/> `'</div>'`|
| e-list-avatar-right | This class is used to align avatar to right side of the list item. It should be added to the template element wrapper. After adding it, we can customize our element with [Avatar](https://ej2.syncfusion.com/documentation/avatar/getting-started/) classes <br/><br/> `template: '<div class="e-list-wrapper e-list-avatar-right">' +` <br/> `'<span class="e-list-content">ListItem</span>' +`<br/> `'<span class="e-avatar e-avatar-circle">MR</span>' +`<br/> `'</div>'`|
| e-list-badge | This class is used for badge customization .It should be added to the template element wrapper. After adding it, we can customize our element with [Badge](https://ej2.syncfusion.com/documentation/badge/getting-started/) classes <br/><br/> `template: '<div class="e-list-wrapper e-list-badge">'` <br/>`'<span class="e-list-content">ListItem</span>'`<br/>`'<span class="e-badge e-badge-primary">MR</span>'`<br/>`'</div>'`|
| e-list-multi-line | This class is used for multi-line customization. It should be added to the template element wrapper. After adding it, we can customize List item's header and description <br/><br/>`template: '<div class="e-list-wrapper e-list-multi-line">' +` <br/>`'<span class="e-list-content">ListItem</span>' +`<br/>`'</div>'`|
| e-list-item-header |This class is used to align a list header and it should be added to the header element along with the multi-line class <br/><br/> `template: '<div class="e-list-wrapper e-list-multi-line">' +` <br/>`'<span class="e-list-item-header">ListItem Header</span>' +`<br/>`'<span class="e-list-content">ListItem</span>' +`<br/>`'</div>'`|

In the following example, we have customized list items like `Contact` app with our avatar component.

{% tab template="listview/templates/customizing-templates", isDefaultActive=true %}

```html

<template>
  <div class="control-section">
    <div id = 'flat-list'>
    <!-- ListView element -->
    <ejs-listview id='List' :dataSource='data' headerTitle='Contacts' showHeader='true' cssClass='e-list-template' :template='template' sortOrder='Ascending' width='350px'></ejs-listview>
    </div>
  </div>
</template>
<style>

#List {
  margin: 0 auto;
  border: 1px solid #ccc;
}

#List .e-list-item {
  height: 60px;
  cursor: pointer;
}

#List .e-list-header .e-text {
  font-family: sans-serif;
  font-size: 18px;
  line-height: 16px;
}

#List #content {
  margin: 0;
}

#List .e-list-header{
  background: rgb(2, 120, 215);
  color: white;
}

#List #info,
#List .name {
  font-size: 14px;
  margin: 0 60px;
  line-height: 20px;
}

#List .name {
  padding-top: 8px;
  font-weight: 500;
}

.pic01 {
  background-image: url("https://ej2.syncfusion.com/demos/src/grid/images/1.png");
}

.pic02 {
  background-image: url("https://ej2.syncfusion.com/demos/src/grid/images/3.png");
}

.pic03 {
  background-image: url("https://ej2.syncfusion.com/demos/src/grid/images/5.png");
}

.pic04 {
  background-image: url("https://ej2.syncfusion.com/demos/src/grid/images/2.png");
}

#List .e-list-item:nth-child(1) .e-avatar {
  background-color: #039be5;
}

#List .e-list-item:nth-child(2) .e-avatar {
  background-color: #e91e63;
}

#List .e-list-item:nth-child(6) .e-avatar {
  background-color: #009688;
}

#List .e-list-item:nth-child(8) .e-avatar {
  background-color: #0088;
}

</style>
<script>
import Vue from "vue";
import { ListViewPlugin } from "@syncfusion/ej2-vue-lists";
Vue.use(ListViewPlugin);
var demoVue = Vue.component("demo", {
  template:
    `<div class="e-list-wrapper e-list-multi-line e-list-avatar">
      <span :class="['e-avatar e-avatar-circle']" v-if="data.avatar !== ''">{{data.avatar}}</span>
      <span :class="[data.pic + ' e-avatar e-avatar-circle']" v-if="data.pic !== '' "> </span>
      <span class="e-list-item-header">{{data.text}}</span>
      <span class="e-list-content">{{data.contact}}</span>
    </div>`,
  data() {
    return {
      data: {}
    };
  }
});

export default {
  data: function() {
    return {
      data: [
  {
    text: "Jenifer",
    contact: "(206) 555-985774",
    id: "1",
    avatar: "",
    pic: "pic01"
  },
  { text: "Amenda", contact: "(206) 555-3412", id: "2", avatar: "A", pic: "" },
  {
    text: "Isabella",
    contact: "(206) 555-8122",
    id: "4",
    avatar: "",
    pic: "pic02"
  },
  {
    text: "William ",
    contact: "(206) 555-9482",
    id: "5",
    avatar: "W",
    pic: ""
  },
  {
    text: "Jacob",
    contact: "(71) 555-4848",
    id: "6",
    avatar: "",
    pic: "pic04"
  },
  { text: "Matthew", contact: "(71) 555-7773", id: "7", avatar: "M", pic: "" },
  {
    text: "Oliver",
    contact: "(71) 555-5598",
    id: "8",
    avatar: "",
    pic: "pic03"
  },
  {
    text: "Charlotte",
    contact: "(206) 555-1189",
    id: "9",
    avatar: "C",
    pic: ""
  }
],
    fields: {text: 'text'},
    template: function () {
                return { template : demoVue};
            }
    };
  },
}
</script>

```

{% endtab %}

## Group template

The ListView group header can be customized with the help of [`groupTemplate`](../api/list-view/#grouptemplate) property.

To customize the group template in your application, set your customized template string to `groupTemplate` property.

```typescript
var tempVue = Vue.component("demo", {
  template: `<div class="group-header"><span>${items[0].category}</span></div>`,
  data() {
    return {
      data: {}
    };
  }
});

```

In the below example, we have grouped Listview based on the category. The category of each list item should be mapped with [`groupBy`](../api/list-view/fieldSettingsModel/#groupby) field of the data. We have also displayed grouped list items count in the group list header.

{% tab template="listview/templates/customizing-group-templates", isDefaultActive=true %}

```html

<template>
  <div class="control-section">
    <div id = 'flat-list'>
      <!-- ListView element -->
      <ejs-listview id='List' ref='list' :dataSource='data' :fields='fields' :template="demoTemplate" :groupTemplate="groupTemplate" cssClass='e-list-template' width='350px'>
      </ejs-listview>
    </div>
  </div>
</template>
<style>

  #List {
      display: block;
      margin: auto;
      border: 1px solid;
      border-color: #ccc;
      border-color: rgba(0, 0, 0, 0.12);
      width: 60%;
  }

  #List .settings {
      height: auto;
  }

  #List .e-list-item {
      height: auto;
      padding: 0;
      cursor: pointer;
      box-sizing: border-box;
  }
  #List .e-list-header .e-text {
      font-family: sans-serif;
      font-size: 18px;
      line-height: 26px;
  }
</style>
<script>
import Vue from "vue";
import { ListViewPlugin } from "@syncfusion/ej2-vue-lists";
Vue.use(ListViewPlugin);
var demoVue = Vue.component("demo", {
  template:
  `<div class="e-list-wrapper e-list-multi-line e-list-avatar">
    <img class="e-avatar e-avatar-circle" :src='data.image' style="background:#BCBCBC" />
    <span class="e-list-item-header">{{data.Name}}</span>
    <span class="e-list-content">{{data.contact}}</span>
  </div>`,
  data() {
    return {
      data: {}
    };
  }
});
var tempVue = Vue.component("demo", {
  template:
  `<div>
    <span class="category">{{data.items[0].category}}</span>
    <span class="count"> {{data.items.length}} Item(s)</span>
  </div>`,
  data() {
    return {
      data: {}
    };
  }
});
export default {
  data: function() {
    return {
        data: [
        { Name: 'Nancy', contact:'(206) 555-985774', id: '1', image: 'https://ej2.syncfusion.com/demos/src/grid/images/1.png',  category: 'Experience'},
        { Name: 'Janet', contact: '(206) 555-3412', id: '2', image: 'https://ej2.syncfusion.com/demos/src/grid/images/3.png', category: 'Fresher' },
        { Name: 'Margaret', contact:'(206) 555-8122', id:'4', image: 'https://ej2.syncfusion.com/demos/src/grid/images/4.png', category: 'Experience' },
        { Name: 'Andrew ', contact:'(206) 555-9482', id: '5', image: 'https://ej2.syncfusion.com/demos/src/grid/images/2.png', category: 'Experience'},
        { Name: 'Steven', contact:'(71) 555-4848', id: '6', image: 'https://ej2.syncfusion.com/demos/src/grid/images/5.png', category: 'Fresher' },
        { Name: 'Michael', contact:'(71) 555-7773', id: '7', image: 'https://ej2.syncfusion.com/demos/src/grid/images/6.png', category: 'Experience' },
        { Name: 'Robert', contact:'(71) 555-5598', id: '8', image: 'https://ej2.syncfusion.com/demos/src/grid/images/7.png', category: 'Fresher' },
        { Name: 'Laura', contact:'(206) 555-1189', id: '9', image: 'https://ej2.syncfusion.com/demos/src/grid/images/8.png', category: 'Experience' },
        ],
        fields: {text: 'Name', groupBy: 'category'},
        demoTemplate: function () {
            return { template : demoVue};
        },
        groupTemplate: function () {
            return { template : tempVue};
        },
    };
  },
}
</script>

```

{% endtab %}
