---
title: "Scroll Settings"
component: "Diagram"
description: "Scroll settings allow you to scroll the diagram by using the vertical and horizontal scroll bars."
---

# Scroll Settings

The diagram can be scrolled by using the vertical and horizontal scrollbars. In addition to the scrollbars,mousewheel can be used to scroll the diagram.
Diagram’s [`scrollSettings`](../api/diagram/diagram) enable you to read the current scroll status, view port size, current zoom, and zoom factor. It also allows you to scroll the diagram programmatically.

## Get current scroll status

Scroll settings allow you to read the scroll status, [`viewPortWidth`](../api/diagram/scrollSettings), [`viewPortHeight`](../api/diagram/scrollSettings), and [`currentZoom`](../api/diagram/scrollSettings) with a set of properties. To explore those properties, see [`Scroll Settings`](../api/diagram/scrollSettings).

## Define scroll status

Diagram allows you to pan the diagram before loading, so that any desired region of a large diagram is made to view. You can programmatically pan the diagram with the [`horizontalOffset`](../api/diagram/scrollSettings) and [`verticalOffset`](../api/diagram/scrollSettings) properties of scroll settings. The following code illustrates how to set pan the diagram programmatically.

In the following example, the vertical scroll bar is scrolled down by 50px and horizontal scroll bar is scrolled to right by 100px.

{% tab template="diagram/scroll-settings/scroll", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' scrollSettings='scrollSettings'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);
 export default {
     name: 'app'
     data() {
         return {
             width: "100%",
             height: "350px",
             scrollSettings: {
                 horizontalOffset: 100,
                 verticalOffset: 50
             }
         }
     }
 }
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Update scroll status

You can programmatically change the scroll offsets at runtime by using the client-side method update. The following code illustrates how to change the scroll offsets and zoom factor at runtime.

{% tab template="diagram/scroll-settings/scrollSettings", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' scrollSettings='scrollSettings'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
import {
    DiagramPlugin
} from '@syncfusion/ej2-vue-diagrams';

Vue.use(DiagramPlugin);


export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        //Updates scroll settings
        diagramInstance.scrollSettings.horizontalOffset = 200;
        diagramInstance.scrollSettings.verticalOffset = 30
        diagramInstance.dataBind();
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## AutoScroll

Autoscroll feature automatically scrolls the diagram, whenever the node or connector is moved beyond the boundary of the diagram. So that, it is always visible during dragging, resizing, and multiple selection operations. Autoscroll is automatically triggered when any one of the following is done towards the edges of the diagram.

* Node dragging, resizing
* Connection editing
* Rubber band selection
* Label dragging

The diagram client-side event [`ScrollChange`](../api/diagram/diagram) gets triggered when the autoscroll (scrollbars) is changed and you can do your own customization in this event.

The autoscroll behavior in your diagram can be enabled/disabled by using the [`canAutoScroll`](../api/diagram/scrollSettings) property of the diagram.

## Autoscroll border

The autoscroll border is used to specify the maximum distance between the object and diagram edge to trigger autoscroll. The default value is set as 15 for all sides (left, right, top, and bottom) and it can be changed by using the [`autoScrollBorder`](../api/diagram/scrollSettings) property of page settings. The following code example illustrates how to set autoscroll border.

{% tab template="diagram/scroll-settings/autoScroll", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' scrollSettings='scrollSettings' :getNodeDefaults='getNodeDefaults'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

let nodes = [{
    id: 'Start',
    width: 140,
    height: 50,
    offsetX: 300,
    offsetY: 50,
    annotations: [{
        id: 'label1',
        content: 'Start'
    }],
    shape: {
        type: 'Flow',
        shape: 'Terminator'
    }
}]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            scrollSettings: {
                autoScrollBorder: {
                    left: 100,
                    right: 100,
                    top: 100,
                    bottom: 100
                }
            },
            getNodeDefaults: (node) => {
                node.height =  100;
                node.width =  100;
                node.style.fill =  '#6BA5D7';
                node.style.strokeColor =  'white';
                return  node;
            }
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Scroll limit

The scroll limit allows you to define the scrollable region of the diagram. It includes the following options:

* Allows to scroll in all directions without any restriction.
* Allows to scroll within the diagram content.
* Allows to scroll within the specified scrollable area.
* The [`scrollLimit`](../api/diagram/scrollSettings) property of scroll settings helps to limit the scrolling.

The scrollSettings [`scrollableArea`](../api/diagram/scrollSettings) allow to extend the scrollable region that is based on the scroll limit.
The following code example illustrates how to specify the scroll limit.

{% tab template="diagram/scroll-settings/scrollLimit", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' scrollSettings='scrollSettings' :getNodeDefaults='getNodeDefaults'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import {
    DiagramPlugin
} from '@syncfusion/ej2-vue-diagrams';

Vue.use(DiagramPlugin);

let nodes = [{
    id: 'Start',
    width: 140,
    height: 50,
    offsetX: 300,
    offsetY: 50,
    annotations: [{
        id: 'label1',
        content: 'Start'
    }],
    shape: {
        type: 'Flow',
        shape: 'Terminator'
    }
}]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            // set the autoScrollBorder
            scrollSettings: {
                //Sets the scroll limit
                scrollLimit: 'infinity'
            },
            getNodeDefaults: (node) => {
                node.height =  100;
                node.width =  100;
                node.style.fill =  '#6BA5D7';
                node.style.strokeColor =  'white';
                return  node;
            }
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Scroll padding

[`padding`](../api/diagram/scrollSettings) property of scroll settings  allows you to extend the scrollable region that is based on the scroll limit.

The following code example illustrates how to set scroll padding to diagram region.

{% tab template="diagram/scroll-settings/scrollLimit", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' scrollSettings='scrollSettings' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import {
    DiagramPlugin
} from '@syncfusion/ej2-vue-diagrams';

Vue.use(DiagramPlugin);

let nodes = [{
    id: 'Start',
     width: 100, height: 100,
    offsetX: 350, offsetY: 350,
    shape: {
        type: 'Flow',
        shape: 'Terminator'
    }
}]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            // set the autoScrollBorder
            scrollSettings: {
                //Sets the scroll limit
                padding: { right: 50, bottom: 50 }
            },
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Scrollable Area

Scrolling beyond any particular rectangular area can be restricted by using the [`scrollableArea`](../api/diagram/scrollSettings) property of scroll settings. To restrict scrolling beyond any custom region, set the [`scrollLimit`](../api/diagram/scrollSettings) as “limited”. The following code example illustrates how to customize scrollable area.

{% tab template="diagram/scroll-settings/scrollArea", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' scrollSettings='scrollSettings' :getNodeDefaults='getNodeDefaults'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
import {
    DiagramPlugin
} from '@syncfusion/ej2-vue-diagrams';

Vue.use(DiagramPlugin);

let nodes = [{
    id: 'Start',
    width: 140,
    height: 50,
    offsetX: 300,
    offsetY: 50,
    annotations: [{
        id: 'label1',
        content: 'Start'
    }],
    shape: {
        type: 'Flow',
        shape: 'Terminator'
    }
}]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            // set the autoScrollBorder
            scrollSettings: {
                //Sets the scroll limit
                scrollLimit: 'infinity',
                //Sets the scrollable Area
                scrollableArea: {
                    x: 0,
                    y: 0,
                    width: 500,
                    height: 500
                }

            },
            getNodeDefaults: (node) => {
                node.height =  100;
                node.width =  100;
                node.style.fill =  '#6BA5D7';
                node.style.strokeColor =  'white';
                return  node;
            }
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## UpdateViewport

The [`updateViewPort`](../api/diagram/diagram) method is used to update the diagram page and view size at runtime.