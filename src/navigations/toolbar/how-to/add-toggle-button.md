---
title: "Add Toggle Button"
component: "Toolbar"
description: "This example demonstrates how to add the Essential JS 2 Toggle Button into Essential JS Toolbar items."
---

# Add Toggle Button

Toolbar supports to add a toggle Button by using the template property. Refer below steps

* By using Toolbar template property, pass required HTML String to render toggle button.

```html
   <e-item template='<button class="e-btn" id="media_btn"></button>'></e-item>
```

* Now render the toggle Button into the targeted element in Toolbar created event handler and bind click event for it. On clicking the
toggle Button, change the required icon and content based on current active state.

{% tab template="toolbar/how-to/toggle-button", isDefaultActive=true %}

```html

<template>
  <div id="app">
        <br>
         <ejs-toolbar id="toolbar" class="toggle" :created='create'>
    <e-items>
             <e-item template='<button class="e-btn" id="media_btn"></button>'></e-item>
                <e-item type='Separator'></e-item>
                <e-item template='<button class="e-btn" id="zoom_btn"></button>'></e-item>
                <e-item type='Separator'></e-item>
                <e-item template='<button class="e-btn" id="undo_btn"></button>'></e-item>
                <e-item type='Separator'></e-item>
                <e-item template='<button class="e-btn" id="filter_btn"></button>'></e-item>
                <e-item type='Separator'></e-item>
                <e-item template='<button class="e-btn" id="visible_btn"></button>'></e-item>
          </e-items>
    </ejs-toolbar>
    <br/>
        <div id="content">
          This content will be hidden, when you click on hide button and toggle get an active state as show, otherwise it will be visible.
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { ToolbarPlugin } from "@syncfusion/ej2-vue-navigations";
import { Button} from "@syncfusion/ej2-buttons";
Vue.use(ToolbarPlugin);

export default {
  name: 'app',
  data () {

},
  methods: {
    create: function(args) {
     var zoomBtn = new Button({ cssClass: `e-flat`, iconCss: 'e-icons e-zoomin-icon', isToggle: true });
    zoomBtn.appendTo('#zoom_btn');

    var mediaBtn = new Button({ cssClass: `e-flat`, iconCss: 'e-icons e-play-icon', isToggle: true });
    mediaBtn.appendTo('#media_btn');

    var undoBtn = new Button({ cssClass: `e-flat`, iconCss: 'e-icons e-undo-icon', isToggle: true });
    undoBtn.appendTo('#undo_btn');

    var filterBtn = new Button({ cssClass: `e-flat`, iconCss: 'e-icons e-filter-icon', isToggle: true });
    filterBtn.appendTo('#filter_btn');

    var visibleBtn = new Button({ cssClass: `e-flat`, iconCss: 'e-icons e-hide-icon', isToggle: true, content:'Hide'});
    visibleBtn.appendTo('#visible_btn');


    //Toggle button click event handlers
    zoomBtn.element.onclick = (): void => {
        if (zoomBtn.element.classList.contains('e-active')) {
            zoomBtn.iconCss = 'e-icons e-zoomout-icon';
        } else {
            zoomBtn.iconCss = 'e-icons e-zoomin-icon';
        }
    };

    mediaBtn.element.onclick = (): void => {
        if (mediaBtn.element.classList.contains('e-active')) {
            mediaBtn.iconCss = 'e-icons e-pause-icon';
        } else {
            mediaBtn.iconCss = 'e-icons e-play-icon';
        }
    };

    undoBtn.element.onclick = (): void => {
        if (undoBtn.element.classList.contains('e-active')) {
            undoBtn.iconCss = 'e-icons e-redo-icon';
        } else {
            undoBtn.iconCss = 'e-icons e-undo-icon';
        }
    };

    filterBtn.element.onclick = (): void => {
        if (filterBtn.element.classList.contains('e-active')) {
            filterBtn.iconCss = 'e-icons e-filternone-icon';
        } else {
            filterBtn.iconCss = 'e-icons e-filter-icon';
        }
    };

    visibleBtn.element.onclick = (): void => {
        if (visibleBtn.element.classList.contains('e-active')) {
            document.getElementById('content').style.display = 'none';
            visibleBtn.content = 'Show';
            visibleBtn.iconCss = 'e-icons e-show-icon';
        } else {
            document.getElementById('content').style.display = 'block';
            visibleBtn.content = 'Hide';
            visibleBtn.iconCss = 'e-icons e-hide-icon';
        }
    };
}
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";


        @font-face {
            font-family: 'toolbar';
            src:
                url(data:application/x-font-ttf;charset=utf-8;base64,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) format('truetype');
            font-weight: normal;
            font-style: normal;
        }

        .e-toolbar.toggle .e-btn .e-icons {
            font-family: 'toolbar' !important;
            font-size: 16px;
            font-style: normal;
            font-weight: normal;
            font-variant: normal;
            text-transform: none;
        }

        .e-hide-icon::before {
            content: '\a701';
        }

        .e-show-icon::before {
            content: '\a700';
        }

        .e-filter-icon::before {
            content: '\a709';
        }

        .e-filternone-icon::before {
            content: '\a708';
        }

        .e-undo-icon::before {
            content: '\a706';
        }

        .e-redo-icon::before {
            content: '\a707';
        }

        .e-play-icon::before {
            content: '\a704';
        }

        .e-pause-icon::before {
            content: '\a705';
        }

        .e-zoomin-icon::before {
            content: '\a702';
        }

        .e-zoomout-icon::before {
            content: '\a703';
        }

</style>
```

{% endtab %}