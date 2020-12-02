# Customize the expand and collapse icons

You can customize TreeView expand and collapse icons by using the [`cssClass`](../../api/treeview#cssclass)&nbsp;property of TreeView.
Refer to the sample to customize expand/collapse icons.

{% tab template="treeview/how-to/icon", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div class="control_wrapper">
        <ejs-treeview id='treeview' :fields="fields" cssClass='custom'></ejs-treeview>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { TreeViewPlugin } from "@syncfusion/ej2-vue-navigations";

Vue.use(TreeViewPlugin);
export default {
  data () {
    var dataSource =  [
        { id: '01', name: 'Local Disk (C:)', expanded: true,
        subChild: [
            {
                id: '01-01', name: 'Program Files',
                subChild: [
                    { id: '01-01-01', name: '7-Zip' },
                    { id: '01-01-02', name: 'Git' },
                    { id: '01-01-03', name: 'IIS Express' },
                ]
            },
            {
                id: '01-02', name: 'Users', expanded: true,
                subChild: [
                    { id: '01-02-01', name: 'Smith' },
                    { id: '01-02-02', name: 'Public' },
                    { id: '01-02-03', name: 'Admin' },
                ]
            },
            {
                id: '01-03', name: 'Windows',
                subChild: [
                    { id: '01-03-01', name: 'Boot' },
                    { id: '01-03-02', name: 'FileManager' },
                    { id: '01-03-03', name: 'System32' },
                ]
            },
        ]
    },
    {
        id: '02', name: 'Local Disk (D:)',
        subChild: [
            {
                id: '02-01', name: 'Personals',
                subChild: [
                    { id: '02-01-01', name: 'My photo.png' },
                    { id: '02-01-02', name: 'Rental document.docx' },
                    { id: '02-01-03', name: 'Pay slip.pdf' },
                ]
            },
            {
                id: '02-02', name: 'Projects',
                subChild: [
                    { id: '02-02-01', name: 'ASP Application' },
                    { id: '02-02-02', name: 'TypeScript Application' },
                    { id: '02-02-03', name: 'React Application' },
                ]
            },
            {
                id: '02-03', name: 'Office',
                subChild: [
                    { id: '02-03-01', name: 'Work details.docx' },
                    { id: '02-03-02', name: 'Weekly report.docx' },
                    { id: '02-03-03', name: 'Wish list.csv' },
                ]
            },
        ]
    },
    {
        id: '03', name: 'Local Disk (E:)', icon: 'folder',
        subChild: [
            {
                id: '03-01', name: 'Pictures',
                subChild: [
                    { id: '03-01-01', name: 'Wind.jpg' },
                    { id: '03-01-02', name: 'Stone.jpg' },
                    { id: '03-01-03', name: 'Home.jpg' },
                ]
            },
            {
                id: '03-02', name: 'Documents',
                    subChild: [
                    { id: '03-02-01', name: 'Environment Pollution.docx' },
                    { id: '03-02-02', name: 'Global Warming.ppt' },
                    { id: '03-02-03', name: 'Social Network.pdf' },
                ]
            },
            {
                id: '03-03', name: 'Study Materials',
                subChild: [
                    { id: '03-03-01', name: 'UI-Guide.pdf' },
                    { id: '03-03-02', name: 'Tutorials.zip' },
                    { id: '03-03-03', name: 'TypeScript.7z' },
                ]
            },
            ]
        }
    ];
    return {
        fields: { dataSource: dataSource, id: 'id', text: 'name', child: 'subChild' },
    }
  }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
 .control_wrapper {
        display: block;
        max-width: 450px;
        max-height: 350px;
        margin: auto;
        overflow: auto;
        border: 1px solid #dddddd;
        border-radius: 3px;
    }
.custom .e-list-item .e-icons {
    font-family: "Customize-icon";
  }
  
  .custom.e-treeview .e-list-item .e-icon-expandable::before, .custom.e-treeview .e-list-item .e-icon-collapsible:before {
    content: '\e700';
    font-size: 12px;
  }
  
  @font-face {
    font-family: 'Customize-icon';
    src: url(data:application/x-font-ttf;charset=utf-8;base64,AAEAAAAKAIAAAwAgT1MvMj0gSRcAAAEoAAAAVmNtYXDnEOdaAAABjAAAADhnbHlmcYqIngAAAcwAAAD8aGVhZBWT124AAADQAAAANmhoZWEHmANtAAAArAAAACRobXR4C9AAAAAAAYAAAAAMbG9jYQBAAH4AAAHEAAAACG1heHABEAAxAAABCAAAACBuYW1l/qscPAAAAsgAAAJ5cG9zdIPGFvoAAAVEAAAAVgABAAADUv9qAFoEAAAA//8D6QABAAAAAAAAAAAAAAAAAAAAAwABAAAAAQAAIKcGUl8PPPUACwPoAAAAANlGSVAAAAAA2UZJUAAAAAAD6QPpAAAACAACAAAAAAAAAAEAAAADACUAAwAAAAAAAgAAAAoACgAAAP8AAAAAAAAAAQPwAZAABQAAAnoCvAAAAIwCegK8AAAB4AAxAQIAAAIABQMAAAAAAAAAAAAAAAAAAAAAAAAAAAAAUGZFZABA5wDnAQNS/2oAWgPpAJYAAAABAAAAAAAABAAAAAPoAAAD6AAAAAAAAgAAAAMAAAAUAAMAAQAAABQABAAkAAAABAAEAAEAAOcB//8AAOcA//8AAAABAAQAAAABAAIAAAAAAEAAfgADAAAAAAPpA+kACAAWACQAAAEhFSEHMzcnIyUWEAcGICcmEDc+ATIWBQYQFxYgNzYQJy4BIgYCMf6kAWqUqMK8rgF+goKK/qCEfn5Coquf/amRkZoBkpqRkUq3xLcCKmSTybt4if6ghYKChQFgiUJBQRma/m6akZGaAZKaSElJAAMAAAAAA+gD6QAGABQAIgAAASMXNyMRIyUWEAcGICcmEDc+ATIWBQYQFxYgNzYQJy4BIgYBvrLp6JmGAW6BgYf+oYiBgUGhqqH9qZOTmgGOmpOTSrbCtgGy6ekBbwuI/qGHgYGIAV6IQEFBFpr+cZmTk5oBj5lKSUkAAAAAABIA3gABAAAAAAAAAAEAAAABAAAAAAABAA4AAQABAAAAAAACAAcADwABAAAAAAADAA4AFgABAAAAAAAEAA4AJAABAAAAAAAFAAsAMgABAAAAAAAGAA4APQABAAAAAAAKACwASwABAAAAAAALABIAdwADAAEECQAAAAIAiQADAAEECQABABwAiwADAAEECQACAA4ApwADAAEECQADABwAtQADAAEECQAEABwA0QADAAEECQAFABYA7QADAAEECQAGABwBAwADAAEECQAKAFgBHwADAAEECQALACQBdyBDdXN0b21pemUtaWNvblJlZ3VsYXJDdXN0b21pemUtaWNvbkN1c3RvbWl6ZS1pY29uVmVyc2lvbiAxLjBDdXN0b21pemUtaWNvbkZvbnQgZ2VuZXJhdGVkIHVzaW5nIFN5bmNmdXNpb24gTWV0cm8gU3R1ZGlvd3d3LnN5bmNmdXNpb24uY29tACAAQwB1AHMAdABvAG0AaQB6AGUALQBpAGMAbwBuAFIAZQBnAHUAbABhAHIAQwB1AHMAdABvAG0AaQB6AGUALQBpAGMAbwBuAEMAdQBzAHQAbwBtAGkAegBlAC0AaQBjAG8AbgBWAGUAcgBzAGkAbwBuACAAMQAuADAAQwB1AHMAdABvAG0AaQB6AGUALQBpAGMAbwBuAEYAbwBuAHQAIABnAGUAbgBlAHIAYQB0AGUAZAAgAHUAcwBpAG4AZwAgAFMAeQBuAGMAZgB1AHMAaQBvAG4AIABNAGUAdAByAG8AIABTAHQAdQBkAGkAbwB3AHcAdwAuAHMAeQBuAGMAZgB1AHMAaQBvAG4ALgBjAG8AbQAAAAACAAAAAAAAAAoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAMBAgEDAQQAFy1hcnJvdy1jaXJjbGUtcmlnaHQtXzAxEi1hcnJvdy1jaXJjbGUtZG93bgAAAAA=) format('truetype');
    font-weight: normal;
    font-style: normal;
  }
</style>
```

{% endtab %}