# Customize ListView as Chat Window

ListView can be customized as chat window. To achieve that, use the ListView [template](https://ej2.syncfusion.com/vue/documentation/api/list-view/#template) property and [Avatar](https://ej2.syncfusion.com/vue/documentation/avatar/getting-started) component.

    * The Listview template property is used to showcase the ListView as chat window.
    * Avatar component is used to design the image of contact person.

Refer the below template code snippet for Template of chat window.

```typescript
var demoVue = Vue.component("demo", {
    template: `<div class='settings' v-if='data.chat!="receiver"'>
      <div id='content'>
      <div class='name'>{{data.text}}</div>
            <div id='info'>{{data.contact}}</div>
            </div>
            <div id='image' v-if='data.avatar!=""'><span class='e-avatar img1 e-avatar-circle'>{{data.avatar}}</span></div>
            <div id='image'  v-if='data.avatar==""'><span :class="[data.pic + ' img1 e-avatar e-avatar-circle']"> </span></div>
            </div>
            <div class='settings' v-else>
            <div id='image2'  v-if='data.avatar!=""'><span class='e-avatar img2 e-avatar-circle'>{{data.avatar}}</span></div>
            <div id='image2'  v-if='data.avatar==""'><span :class="[data.pic +' img2 e-avatar e-avatar-circle']"> </span></div>
            <div id='content1'>
            <div class='name1'>{{data.text}}</div>
            <div id='info1'>{{data.contact}}</div>
            </div>
            </div>`,
    data() {
        return {
        data: {}
        };
    }
});
```

## Chat order in template

In ListView template, we have rendered the list items based on receiver and sender information from dataSource of listview.

## Adding messages to chat window

    * Use textbox to get message from user.
    * Add the textbox message to ListView dataSource using [addItem](https://ej2.syncfusion.com/vue/documentation/api/list-view/#additem) method.

```typescript

 btnClick: function() {
      let value = this.$refs.textbox.value;
      this.$refs.listObj.addItem([{ text: "Amenda", contact: value, id: "2", avatar: "A", pic: "", chat: "receiver" }]);
      this.$refs.textbox.value = "";
    }

```

{% tab template="listview/chat-window", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="chat-window-template" %}

```html
<template>
   <div class="control-section">
    <!-- ListView element -->
    <ejs-listview id='List' ref='listObj' :dataSource='data' :headerTitle='headerTitle' :template='Template' :showHeader='true' :fields='fields' :width='width'></ejs-listview>
  <div style="width: 350px;margin: 0 auto;"><input id="name" ref="textbox" style="width: 275px" class="e-input" type="text" placeholder="Type your message"/>
    <ejs-button id="btn" style="float:right" v-on:click.native="btnClick">Send</ejs-button></div>
  </div>
</template>
<style>

#List {
  margin: 0 auto;
  border: 1px solid #ccc;
}

#List .e-list-item {
  height: auto;
  cursor: pointer;
}

#List .e-list-header .e-text {
  font-family: sans-serif;
  font-size: 18px;
  line-height: 26px;
}

#List #info,
#List .name {
  font-size: 11px;
  line-height: 20px;
}

#List .name {
  padding-top: 3px;
  font-weight: 500;
   padding-left:150px;
}
#List #info {
  float: right;
  margin-right:10px;
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

.img2.e-avatar {
  margin-left: 10px;
  margin-top: 7px !important;
  font-size: 13px;
}

#List #content1 {
  width: 200px;
  background-color: aliceblue;
  display: inline-block;
  margin: 5px;
  
}

#List #info1,
#List .name1 {
  font-size: 11px;
  line-height: 20px;
  margin-left: 10px;
}

#List .name1 {
  padding-top: 3px;
  font-weight: 500;
}
#List #content {
    margin: 5px;
    width: 200px;
    margin-left: 90px;
    background-color: aliceblue;
    display:inline-block
}
#image {
    float: right;
    display: inline-block;

}
#image2 {
    float: left;
    display: inline-block;

}
.img1.e-avatar {
    margin-right: 10px;
    margin: 5px;
    font-size: 13px;
}
.e-listview .e-list-item {
  padding: 0px !important;
}
.e-listview .e-list-header{
  color: white !important;
}
.e-listview .e-list-header{
  background: rgb(2, 120, 215) !important;
}
#List.e-listview .e-list-item.e-hover {
  background-color: transparent;
}
</style>
<script>
import Vue from "vue";
import { ListViewPlugin } from "@syncfusion/ej2-vue-lists";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";

Vue.use(ListViewPlugin);
Vue.use(ButtonPlugin);
var demoVue = Vue.component("demo", {
    template: `<div class='settings' v-if='data.chat!="receiver"'>
      <div id='content'>
      <div class='name'>{{data.text}}</div>
            <div id='info'>{{data.contact}}</div>
            </div>
            <div id='image' v-if='data.avatar!=""'><span class='e-avatar img1 e-avatar-circle'>{{data.avatar}}</span></div>
            <div id='image'  v-if='data.avatar==""'><span :class="[data.pic + ' img1 e-avatar e-avatar-circle']"> </span></div>
            </div>
            <div class='settings' v-else>
            <div id='image2'  v-if='data.avatar!=""'><span class='e-avatar img2 e-avatar-circle'>{{data.avatar}}</span></div>
            <div id='image2'  v-if='data.avatar==""'><span :class="[data.pic +' img2 e-avatar e-avatar-circle']"> </span></div>
            <div id='content1'>
            <div class='name1'>{{data.text}}</div>
            <div id='info1'>{{data.contact}}</div>
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
     data:  [
        {
          text: "Jenifer",
          contact: "Hi",
          id: "1",
          avatar: "",
          pic: "pic01", chat: "sender"
        },
        { text: "Amenda", contact: "Hello", id: "2", avatar: "A", pic: "", chat: "receiver" },
        {
          text: "Jenifer",
          contact: "What Knid of application going to launch",
          id: "4",
          avatar: "",
          pic: "pic02",chat: "sender"
        },
        {
          text: "Amenda ",
          contact: "A knid of Emergency broadcast App",
          id: "5",
          avatar: "A",
          pic: "", chat: "receiver"
        },
        {
          text: "Jacob",
          contact: "Can you please elaborate",
          id: "6",
          avatar: "",
          pic: "pic04",chat: "sender"
        },
      ],
      fields: { text: "Name" },
      width:'350px',
      headerTitle: 'Chat',
         Template: function(e) {
            return {
                template: demoVue,
            };
        }
    };
  },
  methods: {
    btnClick: function() {
      let value = this.$refs.textbox.value;
      this.$refs.listObj.addItem([{ text: "Amenda", contact: value, id: "2", avatar: "A", pic: "", chat: "receiver" }]);
      this.$refs.textbox.value = "";
    }
  }
}
</script>

```

{% endtab %}
