---
title: "Different layouts"
component: "Splitter"
description: "This section explains about user can construct different layouts using mulitple and nested panes."
---

# Different layouts

By using splitter component, you can create the different layouts with multiple and nested panes.

## Code editor style layout

**Step 1**:

Create the element with two child to render the outer splitter and render the first pane of vertical splitter as a horizontal splitter.

```html

<template>
   <ejs-splitter id='outerSplitter' ref="splitterObj" :created='onCreate' orientation='Vertical' class='splitterContent' width='100%' height='400px'>
            <e-panes>
                <e-pane size="53%" min ="30%" ></e-pane>
                <e-pane :content='pane4Content'></e-pane>
            </e-panes>
    </ejs-splitter>
</template>

<style>
    .code-editor #code-text {
        margin-left: 5px;
    }
    .code-editor .code-preview {
        margin-top: 15px;
        font-size: 12px;
    }
    .code-editor #target {
        margin: 20px auto;
        max-width: 600px;
    }
    .code-editor.control-section{
        min-height: 370px;
        margin-bottom: 15px;
        margin-top: 10px;
    }

    .code-editor .h3 {
        font-size: 14px;
        margin: 4px;
    }

    .code-editor .content {
        padding: 12px;
    }
    .code-editor .splitter-image {
        margin: 0 auto;
        display: flex;
        height: 115px;
        margin-top: 10px;
    }
</style>

```

```javascript

<script>
import Vue from "vue";
import { SplitterPlugin } from '@syncfusion/ej2-vue-layouts';
import { Splitter } from '@syncfusion/ej2-layouts';

Vue.use(SplitterPlugin);

export default Vue.extend({
    data: function() {
        return {
            pane4Content: function () {
                return { template : pane4Content }
            },
            pane1Content: `<div><div class="content"><h3 class="h3">HTML</h3><div class="code-preview"><<span>!DOCTYPE html></span><div><<span>html></span></div>
            <div><<span>body></span></div><<span>div</span> id="custom-image"><div style="margin-left: 5px"><<span>img</span> src="src/albert.png"></div>
            <div><<span>div</span>></div><div><<span>/body></span></div><div><<span>/html></span></div></div></div></div>`,
            pane2Content: `<div><div class="content"><h3 class="h3">CSS</h3><div class="code-preview"><span>img {</span><div id="code-text">margin:<span>0 auto;</span></div>
            <div id="code-text">display:<span>flex;</span></div><div id="code-text">height:<span>70px;</span></div><span>}</span></div></div></div>`,
            pane3Content: `<div><div class="content"><h3 class="h3">JavaScript</h3><div class="code-preview"><span>var </span>
            image = document.getElementById("custom-image");<div>image.addEventListener("click", function() {</div>
            <div style="padding-left: 20px;">// Code block for click action</div><span> }</span></div></div></div>`,
            pane4Content: `
            <div>
                <div class="content">
                    <h3 class="h3">Preview of sample</h3>
                    <div class="splitter-image">
                        <img class="img1" src="https://ej2.syncfusion.com/demos/src/listview/images/albert.png" style="width: 20%;margin: 0 auto;">
                    </div>
                </div>
            </div>
`
        }
    },
    methods: {
        onCreate: function () {
            document.getElementById('outerSplitter').querySelector('.e-pane-vertical').setAttribute('id', 'Innersplitter');
            this.splitterObj1 = new Splitter({
                height: '220px',
                paneSettings: [
                    { size: '29%', min: '23%', content: this.pane1Content },
                    { size: '20%', min: '15%', content: this.pane2Content },
                    { size: '35%', min: '35%', content: this.pane3Content }
                ],
                width: '100%'
            });
            this.splitterObj1.appendTo('#Innersplitter');
        }
    }
});
</script>

```

Once the above configurations has been completed, you will get the output like [this](https://ej2.syncfusion.com/vue/demos/#/material/splitter/code-editor-layout.html)

## Outlook style layout

**Step 1**:

Create the element with three panes and place the elements within the pane to render `treeview`, `listview` and `RTE`.

```html
<template>
    <ejs-splitter id='splitter' ref="splitterObj" width='100%' height='498px'>
            <e-panes>
                <e-pane size="28%" min="27%" :content='pane1Content'></e-pane>
                <e-pane size="33%" min ="23%" :content='pane2Content'></e-pane>
                <e-pane size="37%" min ="30%" :content='pane3Content'></e-pane>
            </e-panes>
    </ejs-splitter>
</template>

<style>
    .outlook-style #target {
        margin: 20px auto;
        max-width: 820px;
    }
    .outlook-style #discard {
        margin-left: 7px;
    }
    .outlook-style table {
        width: 100%;
        border: none;
    }
    .outlook-style td {
        padding: 2px;
    }
    .outlook-style.control-section {
        min-height: 370px;  
    }
    .outlook-style .e-treeview .e-list-text {
        width: 100%;
    }
    .outlook-style #groupedList.e-listview .e-list-group-item {
        height: 0;
    }
    .outlook-style #splitter1 .settings.e-list-wrapper.e-list-multi-line.e-list-avatar {
        padding: 15px;
    }
    .outlook-style #buttonSection {
        padding: 7px;
    }
    .outlook-style #createpostholder {
        padding-left: 3px;
        padding-right: 4px;
    }
</style>
<script>
import Vue from "vue";
import { SplitterPlugin } from '@syncfusion/ej2-vue-layouts';
import pane1Content from "./outlook-pane1-content.vue";
import pane2Content from "./outlook-pane2-content.vue";
import pane3Content from "./outlook-pane3-content.vue";


Vue.use(SplitterPlugin);

export default Vue.extend({
    data: function() {
        return {
            pane1Content: function () {
                return { template : pane1Content }
            },
            pane2Content: function () {
                return { template : pane2Content }
            },
            pane3Content: function () {
                return { template : pane3Content }
            }
        }
    }
});
</script>

```

**Step 2** :

Create the separate template files to render the inner components.

Below template defined for treeview

```html

<template>
<div>
    <div class="tree-template-control-wrapper">
        <ejs-treeview id="template" :fields="fields" cssClass="custom" :nodeTemplate="treeTemplate"></ejs-treeview>
    </div>
</div>
</template>
<style>
    .tree-template-control-wrapper .e-treeview .e-list-text {
        width: 100%;
    }
</style>
<script>
import Vue from "vue";
import { TreeViewPlugin } from "@syncfusion/ej2-vue-navigations";

Vue.use(TreeViewPlugin);

var mailBox = [
        { id: 1, name: 'Favorites', hasChild: true},
        { id: 2, pid: 1, name: 'Sales Reports', count: '4' },
        { id: 3, pid: 1, name: 'Sent Items'},
        { id: 4, pid: 1, name: 'Marketing Reports ', count: '6'},
        { id: 5, name: 'Andrew Fuller', hasChild: true, expanded: true },
        { id: 6, pid: 5, name: 'Inbox',  selected: true , count: '20'},
        { id: 7, pid: 5,  name: 'Drafts', count: '5'},
        { id: 8, pid: 5,  name: 'Deleted Items'},
        { id: 9, pid: 5, name: 'Sent Items'},
        { id: 10, pid: 5, name: 'Sales Reports' , count: '4'},
        { id: 11, pid: 5, name: 'Marketing Reports', count: '6' },
        { id: 12, pid: 5, name: 'Outbox' },
        { id: 13, pid: 5, name: 'Junk Email'},
        { id: 14, pid: 5, name: 'RSS Feed'},
        { id: 15, pid: 5, name: 'Trash' }
];

var treeTemplate = Vue.component("demo", {
  template: '<div><div class="treeviewdiv"><div style="float:left"><span class="treeName">{{data.name}}</span></div>' +
        '<div v-if="data.count" style="margin-right: 5px; float:right"><span class="treeCount e-badge e-badge-primary">{{data.count}}</span></div></div></div>',
  data() {
    return {
      data: {}
    };
  }
});

export default Vue.extend ({
    data: function() {
        return {
            fields: { dataSource: mailBox, id: 'id', parentID: 'pid', text: 'name', hasChildren: 'hasChild' },
            treeTemplate: function(e) {
                return {
                    template: treeTemplate
                };
            },
        };
    }
});
</script>

```

Below template defined for listview

```html

<template>
<div>
    <ejs-listview id='listview' :dataSource='outlookdata' :cssClass='cssClass' :template='datatemplate'></ejs-listview>
</div>
</template>
<script>
import Vue from "vue";
import { ListViewPlugin } from "@syncfusion/ej2-vue-lists";
import { enableRipple } from "@syncfusion/ej2-base";
import datatempVue from "./data-vue-template.vue";

enableRipple(false);
Vue.use(ListViewPlugin);
export default Vue.extend({
  data: function() {
    return {
      cssClass: "e-list-template",
      outlookdata: [
       { Name: 'Selma Tally', content1: 'Apology marketing email', content2:'Hello Ananya Singleton' },
       { Name: 'Illa Russo', content1: 'Annual conference', content2: 'Hi jeani Moresa' },
       { Name: 'Camden Macmellon', content1: 'Reference request- Camden hester', content2: 'Hello Kerry Best,' },
       { Name: 'Garth Owen', content1: 'Application for job Title', content2: 'Hello Illa Russo' },
       { Name: 'Ursula Patterson', content1: 'Programmaer Position Applicant', content2: 'Hello Kerry best,' }
      ],
      datatemplate: function() {
        return {
          template: datatempVue
        };
      }
    };
  }
});
</script>

```

Below template defined for RTE

```html

<template>
<div>
        <div style="width: 100%; padding: 15px;">
            <table>
                <tr>
                    <td><ejs-button cssClass='e-flat e-outline' isprimary=true >To...</ejs-button></td>
                    <td><ejs-textbox id="firstname" /></td>
                </tr>
                <tr>
                    <td><ejs-button cssClass='e-flat e-outline'>Cc...</ejs-button></td>
                    <td><ejs-textbox id="lastname" /></td>
                </tr>
                <tr>
                    <td><div id="subject-text">Subject</div></td>
                    <td><ejs-textbox id="subject" /></td>
                </tr>
            </table>
        </div>
        <div class="forum">
        <div id="createpostholder">
                <ejs-richtexteditor ref="rteInstance" height='262px'></ejs-richtexteditor>
                <div id="buttonSection">
                    <ejs-button :isPrimary="isPrimary" id="send" >Send</ejs-button>
                    <ejs-button id="discard" >Discard</ejs-button>
                </div>
        </div>
    </div>
</div>
</template>
<script>
import Vue from "vue";
import { RichTextEditorPlugin, Link, Image, HtmlEditor, Toolbar } from "@syncfusion/ej2-vue-richtexteditor";
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
import { TextBoxPlugin } from '@syncfusion/ej2-vue-inputs';

Vue.use(TextBoxPlugin);
Vue.use(RichTextEditorPlugin);
Vue.use(ButtonPlugin);

export default Vue.extend({
    data: function() {
        return {
        isPrimary: true
        };
    },
    mounted: function() {
        this.$nextTick(function () {
            this.$refs.rteInstance.$el.ej2_instances[0].refresh();
        })
    },
    provide:{
        richtexteditor:[Link, Image, HtmlEditor, Toolbar]
    }
});
</script>

```

Once the above configurations has been completed, you will get the output like [this](https://ej2.syncfusion.com/vue/demos/#/material/splitter/outlook-style-layout.html).

## See Also

* [Multiple panes in Splitter](./split-panes/)