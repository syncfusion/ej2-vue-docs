# Load list items in child list dynamically

To load list items in child list dynamically, push the new list item data into the existing [`dataSource`](https://ej2.syncfusion.com/vue/documentation/api/list-view/#datasource) using the [`select`](https://ej2.syncfusion.com/vue/documentation/api/list-view/#select) event.

Refer to the following steps to load list item into the child list:

1. Initially, render the ListView with the required data source.

2. Bind the [`select`](https://ej2.syncfusion.com/vue/documentation/api/list-view/#select) event that triggers selecting list item in the ListView component. By using the select event, you can push the new list item to the child list of the data source on specifying its item index. Item index can be obtained from the [`SelectEventArgs`](https://ej2.syncfusion.com/vue/documentation/api/list-view/selectEventArgs/) of the select event.

{% tab template="listview/checklist", isDefaultActive=true %}

```html
<template>
  <div class="control-section">
    <div id = 'flat-list'>
    <!-- ListView element -->
    <ejs-listview id='listview' ref='list' :dataSource='data' :fields='fields' headerTitle='Folders' showHeader='true' showIcon='true' :select='onSelect'>
    </ejs-listview>
    </div>
  </div>
</template>
<style>
#listview {
    display: block;
    max-width: 400px;
    margin: auto;
    border: 1px solid #dddddd;
    border-radius: 3px;
}


#listview.e-listview .e-list-icon {
    height: 24px;
    width: 30px;
}

.folder, .file  {
    background: url('https://ej2.syncfusion.com/demos/src/listview/images/file_icons.png') no-repeat;
    background-size: 300%;
}

.folder{
    background-position: -5px -461px;
}

.file {
    background-position: -5px -151px;
}

.list {
    color:deeppink !important;
}
</style>
<script>
import Vue from "vue";
import { ListViewPlugin } from "@syncfusion/ej2-vue-lists";
Vue.use(ListViewPlugin);

export default {
  data: function() {
    return {
      data:[
    {
        id: '01', text: 'Music', icon: 'folder',
        child: [
            { id: '01-01', text: 'Gouttes.mp3', icon: 'file' }
        ]
    },
    {
        id: '02', text: 'Videos', icon: 'folder',
        child: [
            { id: '02-01', text: 'Naturals.mp4', icon: 'file' },
            { id: '02-02', text: 'Wild.mpeg', icon: 'file' },
        ]
    },
    {
        id: '03', text: 'Documents', icon: 'folder',
        child: [
            { id: '03-01', text: 'Environment Pollution.docx', icon: 'file' },
            { id: '03-02', text: 'Global Water, Sanitation, & Hygiene.docx', icon: 'file' },
            { id: '03-03', text: 'Global Warming.ppt', icon: 'file' },
            { id: '03-04', text: 'Social Network.pdf', icon: 'file' },
            { id: '03-05', text: 'Youth Empowerment.pdf', icon: 'file' },
        ]
    },
    {
        id: '04', text: 'Pictures', icon: 'folder',
        child: [
            {
                id: '04-01', text: 'Camera Roll', icon: 'folder',
                child: [
                    { id: '04-01-01', text: 'WIN_20160726_094117.JPG', icon: 'file' },
                    { id: '04-01-02', text: 'WIN_20160726_094118.JPG', icon: 'file' },
                    { id: '04-01-03', text: 'WIN_20160726_094119.JPG', icon: 'file' }
                ]
            },
            {
                id: '04-02', text: 'Wind.jpg', icon: 'file'
            },
            {
                id: '04-02', text: 'Stone.jpg', icon: 'file'
            },
            {
                id: '04-02', text: 'Home.jpg', icon: 'file'
            },
            {
                id: '04-02', text: 'Bridge.png', icon: 'file'
            }
        ]
    },
    {
        id: '05', text: 'Downloads', icon: 'folder',
        child: [
            { id: '05-01', text: 'UI-Guide.pdf', icon: 'file' },
            { id: '05-02', text: 'Tutorials.zip', icon: 'file' },
            { id: '05-03', text: 'Game.exe', icon: 'file' },
            { id: '05-04', text: 'TypeScript.7z', icon: 'file' },
        ]
    },
],
    fields: { iconCss: 'icon', tooltip: 'text'},
    };
  },
  methods:{
    onSelect: function(args){
      this.$refs.list.dataSource[args.index].child.push({ id: '01-02', text: 'Newly Added File', icon: 'file', htmlAttributes: { role: 'li', class: 'list' } });
    }
  }
}
</script>
```

{% endtab %}
