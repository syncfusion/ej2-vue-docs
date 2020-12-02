# Restrict the drag-and-drop for particular tree nodes

You can able to restrict to drag and drop files under folder only.
These can be achieved by using `nodeDragStop` and `nodeDragging` event of TreeView.

{% tab template="treeview/how-to/restrict-drag-drop", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div class="control_wrapper">
        <ejs-treeview id='treeview' :fields="fields" :allowDragAndDrop='true' :nodeDragStop='dragStop' :nodeDragging='nodeDrag'></ejs-treeview>
    </div>
    <div id="display"></div>
  </div>
</template>
<script>
import Vue from 'vue';
import { TreeViewPlugin } from "@syncfusion/ej2-vue-navigations";

Vue.use(TreeViewPlugin);
export default {
  data () {
         var dataSource =  [
        {
            nodeId: '01', nodeText: 'Music', icon: 'folder',
            nodeChild: [
                { nodeId: '01-01', nodeText: 'Gouttes.mp3', icon: 'audio' }
            ]
        },
        {
            nodeId: '02', nodeText: 'Videos', icon: 'folder',
            nodeChild: [
                { nodeId: '02-01', nodeText: 'Naturals.mp4', icon: 'video' },
                { nodeId: '02-02', nodeText: 'Wild.mpeg', icon: 'video' },
            ]
        },
        {
            nodeId: '03', nodeText: 'Documents', icon: 'folder',
            nodeChild: [
                { nodeId: '03-01', nodeText: 'Environment Pollution.docx', icon: 'docx' },
                { nodeId: '03-02', nodeText: 'Global Water, Sanitation, & Hygiene.docx', icon: 'docx' },
                { nodeId: '03-03', nodeText: 'Global Warming.ppt', icon: 'ppt' },
                { nodeId: '03-04', nodeText: 'Social Network.pdf', icon: 'pdf' },
                { nodeId: '03-05', nodeText: 'Youth Empowerment.pdf', icon: 'pdf' },
            ]
        },
        {
            nodeId: '04', nodeText: 'Pictures', icon: 'folder', expanded: true,
            nodeChild: [
                {
                    nodeId: '04-01', nodeText: 'Camera Roll', icon: 'folder', expanded: true,
                    nodeChild: [
                        { nodeId: '04-01-01', nodeText: 'WIN_20160726_094117.JPG', image: 'https://ej2.syncfusion.com/demos/src/treeview/images/employees/9.png' },
                        { nodeId: '04-01-02', nodeText: 'WIN_20160726_094118.JPG', image: 'https://ej2.syncfusion.com/demos/src/treeview/images/employees/3.png' },
                    ]
                },
                { nodeId: '04-02', nodeText: 'Wind.jpg', icon: 'images' },
                { nodeId: '04-03', nodeText: 'Stone.jpg', icon: 'images' },
            ]
        },
        {
            nodeId: '05', nodeText: 'Downloads', icon: 'folder',
            nodeChild: [
                { nodeId: '05-01', nodeText: 'UI-Guide.pdf', icon: 'pdf' },
                { nodeId: '05-02', nodeText: 'Tutorials.zip', icon: 'zip' },
                { nodeId: '05-03', nodeText: 'Game.exe', icon: 'exe' },
                { nodeId: '05-04', nodeText: 'TypeScript.7z', icon: 'zip' },
            ]
        },
    ];
    return {
        fields: { dataSource: dataSource, id: 'nodeId', text: 'nodeText', child: 'nodeChild', iconCss: 'icon', imageUrl: 'image' },
    }
  },
  methods: {

      nodeDrag: function(args) {
          if (args.droppedNode != null && args.droppedNode.getElementsByClassName('folder') && args.droppedNode.getElementsByClassName('folder').length === 0) {
            args.dropIndicator = 'e-no-drop';
          }
      }

      dragStop: function(args) {
         if (args.droppedNode != null && args.droppedNode.getElementsByClassName('folder') && args.droppedNode.getElementsByClassName('folder').length === 0) {
            args.cancel = true;
         }
    }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
 .control_wrapper {
        display: block;
        max-width: 400px;
        max-height: 320px;
        margin: auto;
        overflow: auto;
        border: 1px solid #dddddd;
        border-radius: 3px;
    }
.e-treeview .e-list-img {
        width: 25px;
        height: 25px;
    }

 /* Loading sprite image for TreeView */
 .e-treeview .e-list-icon {
         background-repeat: no-repeat;
         background-image: url(https://ej2.syncfusion.com/demos/src/treeview/images/icons/file_icons.png);
         height: 20px;
    }

 /* Specify the icon positions based upon class name */
 .e-treeview .e-list-icon.folder {
         background-position: -10px -552px;
    }

 .e-treeview .e-list-icon.docx {
         background-position: -10px -20px;
     }

 .e-treeview .e-list-icon.ppt {
         background-position: -10px -48px;
     }

 .e-treeview .e-list-icon.pdf {
         background-position: -10px -104px;
     }

.e-treeview .e-list-icon.images {
         background-position: -10px -132px;
     }

.e-treeview .e-list-icon.zip {
         background-position: -10px -188px;
     }

.e-treeview .e-list-icon.audio {
         background-position: -10px -244px;
     }

.e-treeview .e-list-icon.video {
         background-position: -10px -272px;
     }

.e-treeview .e-list-icon.exe {
         background-position: -10px -412px;
     }
</style>

```

{% endtab %}