# Create mobile Contact layout from ListView

You can customize the ListView using the [template](https://ej2.syncfusion.com/vue/documentation/api/list-view/#template) property. Refer to the following steps to customize ListView as mobile contact view with our `ej2-avatar`.

* Render the ListView with [dataSource](https://ej2.syncfusion.com/vue/documentation/api/list-view/#datasource) that has avatar data. You can set avatar data as either text or class names. Refer to the following codes.

```typescript

dataSource: [
  {
    text: "Jenifer", contact: "(206) 555-985774", id: "1", avatar: "", pic: "pic01"
  },
  {
    text: "Amenda", contact: "(206) 555-3412", id: "2", avatar: "A", pic: ""
  }
];

```

* Set `avatar` classes in ListView template to customize contact icon. In the following codes, medium size avatar has been set using the class name `e-avatar e-avatar-circle` from data source.

```typescript

  <div class="listWrapper">
        <span :class="['e-avatar e-avatar-small e-avatar-circle']" v-if="data.avatar !== ''">{{data.avatar}}</span>
        <span :class="[data.pic + ' e-avatar e-avatar-small e-avatar-circle']" v-if="data.pic !== '' "> </span>
        <span class="list-text">{{data.text}}</span>
    </div>

```

> Avatars can be set in different sizes in avatar classes. To know more about avatar classes, refer to [Avatar](https://ej2.syncfusion.com/vue/demos/#/material/avatar/default.html).

* Sort the contact names using the [`sortOder`](https://ej2.syncfusion.com/vue/documentation/api/list-view/#sortorder) property of ListView.
* Enable the [`showHeader`](https://ej2.syncfusion.com/vue/documentation/api/list-view/#showheader) property, and set the [`headerTitle`](https://ej2.syncfusion.com/vue/documentation/api/list-view/#headertitle) as `Contacts`.

{% tab template="listview/avatar", isDefaultActive=true %}

```html
<template>
    <div id="sample">
       <ejs-listview id='List' :dataSource='data' :fields='fields' :template='template' width="350px" showHeader='true' headerTitle='Contacts' sortOrder='Ascending'></ejs-listview>
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

#List .e-avatar {
  position: absolute;
  margin-top: 8px;
  font-size: 14px;
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
  template: `
    <div class="settings">
        <span :class="['e-avatar e-avatar-circle']" v-if="data.avatar !== ''">{{data.avatar}}</span>
        <span :class="[data.pic + ' e-avatar e-avatar-circle']" v-if="data.pic !== '' "> </span>
        <div id="content">
        <div class="name">{{data.text}}</div>
        <div id="info">{{data.contact}}</div>
        </div>
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
