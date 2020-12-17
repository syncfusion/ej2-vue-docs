---
title: "Vue Dialog Resizing"
component: "Dialog"
description: "Explains about the resizeable dialog which allows changing its size dynamically."
---

# Resizing

The Dialog supports resizing feature. To resize the dialog, we have to select and resize it by using its handle (grip) or hovering on any of the edges or borders of the dialog within the sample container.

The resizable dialog can be created by setting the [enableResize](../api/dialog/#enableresize) property to true, which is used to change the size of a dialog dynamically and view its content with expanded mode. The [resizeHandles](../api/dialog/#resizehandles) property can also be configured for all the which directions in which the dialog should be resized. When you configure the target property along with the [enableResize](../api/dialog/#enableresize) property, the dialog can be resized within its specified target container.

{% tab template="dialog/resize" %}

```html
<template>
    <div id="target"  class="control-section">
        <ejs-dialog :header="header" :content="content" :enableResize='true' :resizeHandles='resizeHandles' :allowDragging="draggable" :target='target' :width='width'> </ejs-dialog>
    </div>
</template>
<script>
import Vue from 'vue';
import { DialogPlugin } from '@syncfusion/ej2-vue-popups';
Vue.use(DialogPlugin);
export default {
   data : function() {
    return {
        target: '#target',
        width: '300px',
        header: 'Dialog',
        resizeHandles: ['All'],
        draggable: true,
        content: 'This is a Dialog with resize enabled.'
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
    #app {
        color: #008cff;
        height: 40px;
        left: 45%;
        position: absolute;
        top: 45%;
        width: 30%;
    }
    .control-section {
        min-height: 355px;
        margin: 10px;
    }
</style>
```

{% endtab %}
