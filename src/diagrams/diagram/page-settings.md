---
title: "Page Settings"
component: "Diagram"
description: "Page settings enable you to customize the appearance, width, and height of the diagram page."
---

# Page Settings

Page settings enable to customize the appearance, width, and height of the diagram page.

## Page size and appearance

* The size and appearance of the diagram pages can be customized with the page settings property.

* The [`width`](../api/diagram/pageSettings#width-number) and [`height`](../api/diagram/pageSettings#height-number) properties of page settings define the size of the page and based on the size, the [`orientation`](../api/diagram/pageSettings#orientation-PageOrientation) will be set for the page. In addition to that, the appearance of the page can be customized with [`source`](../api/diagram/background#source-string) and set of appearance specific properties.

* The [`color`](../api/diagram/background#color-string) property is used to customize the background color and border color of the page.

* The [`margin`](../api/diagram/pageSettings#margin-MarginModel) property is used to define the page margin.

* To explore those properties, refer to [`Page Settings`](../api/diagram/pageSettings).

{% tab template="diagram/page-settings/pagesettings", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' :getNodeDefaults='getNodeDefaults'
        :connectors='connectors'
        :pageSettings='pageSettings' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,PageSettings } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let connectors = [{
    id: 'connector1',
    style: { strokeColor: '#6BA5D7', fill: '#6BA5D7', strokeWidth: 2 },
    targetDecorator: { style: { fill: '#6BA5D7', strokeColor: '#6BA5D7' } },
    sourceID: 'node1',
    targetID: 'node2',
}]

    let nodes = [{
    id: 'node1',
    width: 100,
    height: 100,
    offsetX: 100,
    offsetY: 100,
    annotations: [{
        content: 'Node1'
    }]
},{
    id: 'node2',
    width: 100,
    height: 100,
    offsetX: 300,
    offsetY: 350,
    annotations: [{
        content: 'Node3'
    }]
}]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            getNodeDefaults: (node) => {
                node.height = 100;
                node.width = 100;
                node.style.fill = '#6BA5D7';
                node.style.strokeColor = 'white';
                return node;
            },
            connectors: connectors,
            pageSettings: {
        // Sets the PageOrientation for the diagram to page
        orientation: 'Landscape',
        // Sets the Page Break for diagram
        showPageBreaks: true,
        // Defines the background color and image  of diagram
        background: {
            color: 'grey'
        },
        // Sets the width for the Page
        width: 300,
        // Sets the height for the Page
        height: 300,
        // Sets the space to be left between an annotation and its parent node/connector
        margin: {
            left: 10,
            top: 10,
            bottom: 10
        },
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

## Set background image

Stretch and align the background image anywhere over the diagram area.
The [`source`](../api/diagram/background#source-string) property of [`background`](../api/diagram/pageSettings#background-BackgroundModel) allows you to set the path of the image.
The [`scale`](../api/diagram/background#scale-string) and the [`align`](../api/diagram/background#align-ImageAlignment) properties help to stretch/align the background images.

The following code illustrates how to stretch and align the background image.

{% tab template="diagram/page-settings/BGImage", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height'
        :pageSettings='pageSettings' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,PageSettings } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            pageSettings: {
        orientation: 'Landscape',
        showPageBreaks: true,
        // Defines the background Image source
        background: {
            source: 'https://www.w3schools.com/images/w3schools_green.jpg',
            // Defines the scale values for the background image
            scale:'Meet',
            // Defines the align values for the background image
            align:'XMinYMin'
        },
        width: 300,
        height: 300,
        margin: {
            left: 10,
            top: 10,
            bottom: 10
        },
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

## Multiple page and page breaks

When multiple page is enabled, the size of the page dynamically increases or decreases in multiples of page width and height and completely fits diagram within the page boundaries. Page breaks is used as a visual guide to see how pages are split into multiple pages.

The [`multiplePage`](../api/diagram/pageSettings#multiplepage-boolean) and [`showPageBreak`](../api/diagram/pageSettings#showpagebreaks-boolean) properties of page settings allow you to enable/disable multiple pages and page breaks respectively.
The following code illustrates how to enable multiple page and page break lines.

{% tab template="diagram/page-settings/multiplepage", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' :getNodeDefaults='getNodeDefaults'
        :connectors='connectors'
        :pageSettings='pageSettings' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,PageSettings } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let connectors = [{
    id: 'connector1',
    style: { strokeColor: '#6BA5D7', fill: '#6BA5D7', strokeWidth: 2 },
    targetDecorator: { style: { fill: '#6BA5D7', strokeColor: '#6BA5D7' } },
    sourceID: 'node1',
    targetID: 'node2',
}]

    let nodes = [{
    id: 'node1',
    width: 100,
    height: 100,
    offsetX: 100,
    offsetY: 100,
    annotations: [{
        content: 'Node1'
    }]
},{
    id: 'node2',
    width: 100,
    height: 100,
    offsetX: 300,
    offsetY: 350,
    annotations: [{
        content: 'Node3'
    }]
}]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            getNodeDefaults: (node) => {
                node.height = 100;
                node.width = 100;
                node.style.fill = '#6BA5D7';
                node.style.strokeColor = 'white';
                return node;
            },
            connectors: connectors,
            pageSettings: {
        orientation: 'Landscape',
        // Sets the Multiple page for diagram
        multiplePage: true,
        // Sets the Page Break for diagram
        showPageBreaks: true,
        width: 300,
        height: 300,
        margin: {
            left: 10,
            top: 10,
            bottom: 10
        },
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

## Boundary constraints

The diagram provides support to restrict/customize the interactive region, out of which the elements cannot be dragged, resized, or rotated. The [`boundaryConstraints`](../api/diagram/pageSettings#boundaryconstraints-BoundaryConstraints) property of page settings allows you to customize the interactive region.
To explore the boundary constraints, refer to [`Boundary Constraints`](../api/diagram/boundaryConstraints).

The following code example illustrates how to define boundary constraints with respect to the page.

{% tab template="diagram/page-settings/boundaryconstraints", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' :getNodeDefaults='getNodeDefaults'
        :connectors='connectors'
        :pageSettings='pageSettings' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,PageSettings } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let connectors = [{
    id: 'connector1',
    style: { strokeColor: '#6BA5D7', fill: '#6BA5D7', strokeWidth: 2 },
    targetDecorator: { style: { fill: '#6BA5D7', strokeColor: '#6BA5D7' } },
    sourcePoint: {
        x: 300,
        y: 100
    },
    targetPoint: {
        x: 400,
        y: 100
    }
}]

    let nodes = [{
    id: 'node1',
    width: 150,
    height: 100,
    offsetX: 100,
    offsetY: 100,
},{
    id: 'node2',
    width: 80,
    height: 130,
    offsetX: 200,
    offsetY: 200,
}]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            getNodeDefaults: (node) => {
                node.height = 100;
                node.width = 100;
                node.style.fill = '#6BA5D7';
                node.style.strokeColor = 'white';
                return node;
            },
            connectors: connectors,
            pageSettings: {
        // Sets the BoundaryConstraints to page
        boundaryConstraints: 'Page',
        background: {
            color: 'grey'
        },
        width: 400,
        height: 400,
        showPageBreaks: true,
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