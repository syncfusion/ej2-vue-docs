---
title: "Gridlines"
component: "Diagram"
description: "Diagram gridlines are the lines that are draw behind the nodes and connectors."
---

# Gridlines

Gridlines are the pattern of lines drawn behind the diagram elements. It provides a visual guidance while dragging or arranging the objects on the diagram surface.

The model’s [`snapSettings`](../api/diagram#snapsettings-SnapSettingsModel) property is used to customize the gridlines and control the snapping behavior in the diagram.

## Customize the gridlines visibility

The [`snapSettings.snapConstraints`](../api/diagram/snapSettings#constraints-SnapConstraints) enables you to show/hide the gridlines. The following code example illustrates how to show or hide gridlines.

If you need to enable snapping, then inject snapping module into the diagram.

{% tab template="diagram/gridlines/gridlines", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :snapSettings='snapSettings' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,SnapSettingsModel,SnapConstraints,Snapping,Diagram } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);
    Diagram.Inject(Snapping);

    let snapSettings: SnapSettingsModel = {
    // Display both Horizontal and Vertical gridlines
    constraints:  SnapConstraints.ShowLines  };

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            snapSettings:snapSettings
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Appearance

The appearance of the gridlines can be customized by using a set of predefined properties.

* The [`horizontalGridLines`](../api/diagram/snapSettings#horizontalgridlines-GridlinesModel) and the [`verticalGridLines`](../api/diagram/snapSettings#verticalgridlines-GridlinesModel) properties allow to customize the appearance of the horizontal and vertical gridlines respectively.

* The horizontal gridlines [`lineColor`](../api/diagram/gridlines#linecolor-string) and [`lineDashArray`](../api/diagram/gridlines#linedasharray-string) properties are used to customizes the line color and line style of the horizontal gridlines.

* The vertical gridlines [`lineColor`](../api/diagram/gridlines#linecolor-string) and [`lineDashArray`](../api/diagram/gridlines#linedasharray-string) properties are used to customizes the line color and line style of the vertical gridlines.

The following code example illustrates how to customize the appearance of gridlines.

{% tab template="diagram/gridlines/gridlinesAppearance", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :snapSettings='snapSettings' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,SnapSettingsModel,SnapConstraints,Snapping,Diagram } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);
    Diagram.Inject(Snapping);

    let snapSettings: SnapSettingsModel = {
    // Define the Constraints for gridlines and snapping
    constraints: SnapConstraints.ShowLines,
    // Defines the horizontalGridlines for SnapSettings
    horizontalGridlines: {
        // Sets the line color of gridlines
        lineColor: 'blue',
        // Defines the lineDashArray of gridlines
        lineDashArray: '2 2'
    },
    // Defines the verticalGridlines for SnapSettings
    verticalGridlines: {
        lineColor: 'blue',
        lineDashArray: '2 2'
    }
};

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            snapSettings:snapSettings
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Line Intervals

Thickness and the space between gridlines can be customized by using horizontal gridlines’s [`linesInterval`](../api/diagram/gridlines#lineintervals-number) and vertical gridlines’s [`linesInterval`](../api/diagram/gridlines#lineintervals-number) properties. In the lines interval collections, values at the odd places are referred as the thickness of lines and values at the even places are referred as the space between gridlines.

The following code example illustrates how to customize the thickness of lines and the line intervals.

{% tab template="diagram/gridlines/gridlineIntervals", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :snapSettings='snapSettings' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,SnapSettingsModel,SnapConstraints,Snapping,Diagram } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);
    Diagram.Inject(Snapping);

    let snapSettings: SnapSettingsModel = {
    constraints: SnapConstraints.ShowLines,
    horizontalGridlines: {
        // Sets the lineIntervals of Gridlines
        lineIntervals: [1.25, 14, 0.25, 15, 0.25, 15, 0.25, 15, 0.25, 15],
        lineColor: 'blue',
        lineDashArray: '2 2'
    },
    verticalGridlines: {
        // Sets the lineIntervals of Gridlines
        lineIntervals: [1.25, 14, 0.25, 15, 0.25, 15, 0.25, 15, 0.25, 15],
        lineColor: 'blue',
        lineDashArray: '2 2'
    }
};

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            snapSettings:snapSettings
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Snapping

## Snap To Lines

This feature allows the diagram objects to snap to the nearest intersection of gridlines while being dragged or resized. This feature enables easier alignment during layout or design.

Snapping to gridlines can be enabled/disabled with the [`snapSettings.snapConstraints`](../api/diagram/snapSettings#constraints-SnapConstraints). The following code example illustrates how to enable/disable the snapping to gridlines.

{% tab template="diagram/gridlines/snapping", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' :snapSettings='snapSettings' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,SnapSettingsModel,SnapConstraints,Snapping,Diagram } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);
    Diagram.Inject(Snapping);

    let nodes = [{
    id: 'node1',
    style:{fill:'#6BA5D7',strokeColor:'#6BA5D7'},
    width: 100,
    height: 100,
    offsetX: 100,
    offsetY: 100,
}]

    let snapSettings: SnapSettingsModel = {
    // Enables the object to snap with both horizontal and Vertical gridlines
    constraints: SnapConstraints.SnapToLines | SnapConstraints.ShowLines
}

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            snapSettings:snapSettings
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Customization of Snap Intervals

By default, the objects are snapped towards the nearest gridline. The gridline or position towards where the diagram object snaps can be customized with the horizontal gridlines’s [`snapInterval`](../api/diagram/gridlines#snapintervals-number) and the vertical gridlines’s [`snapInterval`](../api/diagram/gridlines#snapintervals-number) properties.

{% tab template="diagram/gridlines/snapintervals", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes'
        :snapSettings='snapSettings' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,SnapSettingsModel,SnapConstraints,Snapping,Diagram } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);
    Diagram.Inject(Snapping);
    let nodes = [{
    id: 'node1',
    width: 100,
    style:{fill:'#6BA5D7',strokeColor:'#6BA5D7'},
    height: 100,
    offsetX: 100,
    offsetY: 100
}]

    let snapSettings: SnapSettingsModel = {
    horizontalGridlines: {
        // Defines the snap interval for object
        snapIntervals: [10]
    },
    verticalGridlines: {
        snapIntervals: [10]
    },
    constraints: SnapConstraints.All
}

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            snapSettings:snapSettings
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Snap To Objects

The snap-to-object provides visual cues to assist with aligning and spacing Diagram elements. A node can be snapped with its neighbouring objects based on certain alignments. Such alignments are visually represented as smart guides.

The [`snapObjectDistance`](../api/diagram/snapSettings/#snapobjectdistance) property allows you to define minimum distance between the selected object and the nearest object.

The [`snapAngle`](../api/diagram/snapSettings/#snapangle) property allows you to define the snap angle by which the object needs to be rotated.

[`snapconstraints`](../api/diagram/snapSettings/#constraints) property allow you to enable or disable the certain features of the snapping , refer to `snapconstraints`

{% tab template="diagram/gridlines/snapobjects", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes'
        :snapSettings='snapSettings' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,SnapSettingsModel,SnapConstraints,Snapping,Diagram } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);
    Diagram.Inject(Snapping);

    let nodes = [{
    id: 'node1',
    style:{fill:'#6BA5D7',strokeColor:'#6BA5D7'},
    width: 100,
    height: 100,
    offsetX: 100,
    offsetY: 100
},{
    id: 'node2',
    style:{fill:'#6BA5D7',strokeColor:'#6BA5D7'},
    width: 100,
    height: 100,
    offsetX: 300,
    offsetY: 100
}]

    let snapSettings: SnapSettingsModel = {
    // Enable snap to object constraint
    constraints: SnapConstraints.SnapToObject|SnapConstraints.ShowLines,
    // Sets the Snap object distance
    snapObjectDistance: 10,
    // Snap Angle for object
    snapAngle: 10
}

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            snapSettings:snapSettings,
            nodes: nodes,
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}