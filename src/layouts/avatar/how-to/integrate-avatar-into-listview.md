# Integrate avatar into ListView

Avatar can be integrated into various components to make a wide variety of applications. Some of the integrations are shown
in the following section.

## ListView

Avatar is integrated into the listview to create contacts applications. The `xsmall` size avatar is used to match the
size of the list item. Letters and images are also used as avatar content.

{% tab template="avatar/listview", isDefaultActive=true %}

```html
<template>
    <div id='element'>
        <!-- Listview element -->
        <ejs-listview id='letterAvatarList' :dataSource='dataSource' :sortOrder='sortOrder' showHeader='true'
        headerTitle='Contacts' :template='listTemplate' >
    </ejs-listview>
    </div>
</template>
<script>
import Vue from "vue";
import { ListViewPlugin } from "@syncfusion/ej2-vue-lists";
Vue.use(ListViewPlugin);

var listtemplateVue = Vue.component("demo", {
  template: ` <div class="listWrapper">
        <span :class="['e-avatar e-avatar-small e-avatar-circle']" v-if="data.avatar !== ''">{{data.avatar}}</span>
        <span :class="[data.pic + ' e-avatar e-avatar-small e-avatar-circle']" v-if="data.pic !== '' "> </span>
        <span class="list-text">{{data.text}}</span>
    </div>`,
  data() {
    return {
      data: {}
    };
  }
});

export default {
  data() {
    return {
        dataSource: [
            { id: 's_01', text: 'Robert', avatar: '', pic: 'pic04' },
            { id: 's_02', text: 'Nancy', avatar: 'N', pic: '' },
            { id: 's_05', text: 'John', pic: 'pic01', avatar: '' },
            { id: 's_03', text: 'Andrew', avatar: 'A', pic: '' },
            { id: 's_06', text: 'Michael', pic: 'pic02', avatar: '' },
            { id: 's_07', text: 'Steven', pic: 'pic03', avatar: '' },
            { id: 's_08', text: 'Margaret', avatar: 'M', pic: '' }
        ],
         listTemplate: function () {
            return { template : listtemplateVue}
        },
        sortOrder: 'Ascending'
    };
  }
}
</script>
<style>
    @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-layouts/styles/material.css";
    #element {
        width: 400px;
        margin: auto;
        border-radius: 3px;
        justify-content: center;
    }

    /* Listview Customization */

    #letterAvatarList {
        max-width: 350px;
        margin: auto;
        border: 1px solid #dddddd;
        border-radius: 3px;
    }

    #letterAvatarList .listWrapper {
        width: inherit;
        height: inherit;
        position: relative;
    }

    #letterAvatarList .e-list-header {
        height: 54px;
    }

    .material #letterAvatarList .e-list-header .e-text {
        line-height: 22px;
    }

    .fabric #letterAvatarList .e-list-header .e-text {
        line-height: 22px;
    }

    .bootstrap #letterAvatarList .e-list-header .e-text {
        line-height: 13px;
    }

    .highcontrast #letterAvatarList .e-list-header .e-text {
        line-height: 20px;
    }

    #letterAvatarList .e-list-item {
        cursor: pointer;
        height: 50px;
        line-height: 44px;
        border: 0;
    }

    /* Badge Positioning */

    #letterAvatarList .e-badge {
        margin-top: 12px;
    }

    #letterAvatarList .listWrapper .list-text {
        width: 60%;
        display: inline-block;
        vertical-align: middle;
        margin: 0 50px;
    }

    /* Avatar Positioning */

    #letterAvatarList .listWrapper .e-avatar {
        position: absolute;
        top: calc(100% - 40px);
        font-size: 10px;
        left: 5px;
    }

    /* Avatar Background Customization */

    #letterAvatarList .e-list-item:nth-child(1) .e-avatar {
        background-color: #039BE5;
    }

    #letterAvatarList .e-list-item:nth-child(3) .e-avatar {
        background-color: #E91E63;
    }

    #letterAvatarList .e-list-item:nth-child(5) .e-avatar {
        background-color: #009688;
    }

    /* Avatar images using 'background-image' property */

    .pic01 {
        background-image: url(./pic01.png);
    }

    .pic02 {
        background-image: url(./pic02.png);
    }

    .pic03 {
        background-image: url(./pic03.png);
    }

    .pic04 {
        background-image: url(./pic04.png);
    }
</style>

```

{% endtab %}
