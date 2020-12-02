---
title: "User Interactions"
component: "Maps"
description: "Explains the user interactions in maps component"
---

# User Interactions

Options like zooming, panning, single click and double click, highlight and map selection enables the effective interaction on Map elements.

## Zooming

The zooming feature enables you to zoom in and out the Map to show in-depth information. It is controlled by the `zoomFactor` property of the `zoomSettings` of the map. When the zoomFactor is increased, the Map is zoomed in. When the zoomFactor is decreased, then the Map is zoomed out.

### Enable Zooming

To enable the zooming feature, set the `zoomSettings.enable` as true in maps. Zooming feature needs the `Zoom` module injection to perform zooming actions, use module injection to inject zoom into Maps by using `provide` option.

### Enable Panning

To enable the panning feature, set the [`enablePanning`](../api/maps/zoomSettings/#enablepanning) property of [`zoomSettings`](../api/maps/zoomSettings) to **true**.

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :zoomSettings='zoomSettings' >
                <e-layers>
                    <e-layer :shapeData='shapeData' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Zoom } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        zoomSettings: {
            enable: true,
            enablePanning: true
        },
        shapeData: world_map,
    }
},
provide: {
    maps: [Zoom]
}
}
</script>
<style>
  .wrapper {
    max-width: 400px;
    margin: 0 auto;
  }
</style>
```

### Various type of zooming

Zooming can be performed in following types:

<b>Zooming toolbar</b>

By default, the toolbar is rendered with `zoom-in`, `zoom-out`, and `reset` options when it is set to 'true' in the `enable` property of `zoomSettings`. You can also customize the toolbar items using the `toolBArs` property in `zoomSettings`.

The following options are available in toolbar, and you can use the options as needed:

1. Zoom - Provides rectangular zoom support.
2. ZoomIn - Zooms in the maps.
3. ZoomOut - Zooms out the maps.
4. Pan - Switches to panning if rectangular zoom is activated.
5. Reset - Restores the maps to the default view.

Refer the [`API`](../api/maps/zoomSettingsModel) links for Zooming.

<b>Pinch Zooming</b>

Use the `pinchZooming` property in `zoomSettings` to enable or disable the pinch zooming.

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :zoomSettings='zoomSettings' >
                <e-layers>
                    <e-layer :shapeData='shapeData' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Zoom } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        zoomSettings: {
            enable: true,
            pinchZooming: true
        },
        shapeData: world_map,
    }
},
provide: {
    maps: [Zoom]
}
}
</script>
<style>
  .wrapper {
    max-width: 400px;
    margin: 0 auto;
  }
</style>
```

<b>Single-click zooming</b>

Use the `zoomOnClick` property in `zoomSettings` to enable or disable the single-click zooming

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :zoomSettings='zoomSettings' >
                <e-layers>
                    <e-layer :shapeData='shapeData' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Zoom } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        zoomSettings: {
            enable: true,
            zoomOnClick: true
        },
        shapeData: world_map,
    }
},
provide: {
    maps: [Zoom]
}
}
</script>
<style>
  .wrapper {
    max-width: 400px;
    margin: 0 auto;
  }
</style>
```

<b>Double-click zooming</b>

Use the `doubleClickZoom` property in `zoomSettings` to enable or disable the double-click zooming.

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :zoomSettings='zoomSettings' >
                <e-layers>
                    <e-layer :shapeData='shapeData' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Zoom } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        zoomSettings: {
            enable: true,
            doubleClickZoom: true
        },
        shapeData: world_map,
    }
},
provide: {
    maps: [Zoom]
}
}
</script>
<style>
  .wrapper {
    max-width: 400px;
    margin: 0 auto;
  }
</style>
```

<b>Mouse wheel zooming</b>

Use the `mouseWheelZoom` property in `zoomSettings` to enable or disable mouse wheel zooming.

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :zoomSettings='zoomSettings' >
                <e-layers>
                    <e-layer :shapeData='shapeData' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Zoom } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        zoomSettings: {
            enable: true,
            mouseWheelZoom: true
        },
        shapeData: world_map,
    }
},
provide: {
    maps: [Zoom]
}
}
</script>
<style>
  .wrapper {
    max-width: 400px;
    margin: 0 auto;
  }
</style>
```

### Zooming with animation

You can use the `animationDuration` property in  `layers` property to zoom in or zoom out the maps with animation.

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :zoomSettings='zoomSettings' >
                <e-layers>
                    <e-layer :shapeData='shapeData' :animationDuration='animationDuration' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Zoom } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        zoomSettings: {
            enable: true,
            mouseWheelZoom: true
        },
        shapeData: world_map,
        animationDuration: 500
    }
},
provide: {
    maps: [Zoom]
}
}
</script>
<style>
  .wrapper {
    max-width: 400px;
    margin: 0 auto;
  }
</style>
```

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :zoomSettings='zoomSettings' >
                <e-layers>
                    <e-layer :shapeData='shapeData' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Zoom } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        zoomSettings: {
            enable: true,
        },
        shapeData: world_map,
    }
},
provide: {
    maps: [Zoom]
}
}
</script>
<style>
  .wrapper {
    max-width: 400px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Selection

Each shape in the Map can be selected and deselected during interaction with the shapes.

By tapping on the specific legend, the map items which are bounded to the selected legend is also selected and vice versa.

The layer `selectionSettings.fill` property is used to change the selected layer shape color. The `selectionSettings.border.color` and `selectionSettings.border.width` properties are used to customize the selected shape border.

You can select the shape by tapping the shape. The Single selection is enabled by the `selectionSettings.enable` property of shape layer. When `selectionSettings.enable` is set to false, the shapes cannot be selected.

Refer the [`API`](../api/maps/selectionSettingsModel/) and code snippet for Selection.

**Note:** Selection is separate module, need to inject to work on Selection.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' :selectionSettings='selectionSettings' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Selection } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        shapeData: world_map,
        selectionSettings: {
            enable: true,
            fill: 'green',
            border: { color: 'white', width: 2}
        }
    }
},
provide: {
    maps: [Selection]
}
}
</script>
<style>
  .wrapper {
    max-width: 400px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Public method for the shape selection

Each shape in the map can be selected by calling the `shapeSelection` method. Input parameters for this method are layerIndex, propertyName, country name and selected value as in boolean state(true / false).

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps ref='maps'>
                <e-layers>
                    <e-layer :shapeData='shapeData' :selectionSettings='selectionSettings' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
        <ejs-button id='selection' @click.native='select'>selection</ejs-button>
        <ejs-button id='unselection' @click.native='unselect'>unselection</ejs-button>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Selection } from '@syncfusion/ej2-vue-maps';
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
Vue.use(ButtonPlugin);
export default {
data () {
    return{
        shapeData: world_map,
        selectionSettings: {
            enable: true,
            fill: 'green',
            border: { color: 'white', width: 2}
        }
    }
},
provide: {
    maps: [Selection]
},
methods:{
    select:function(){
        this.$refs.maps.shapeSelection(0, "continent", "Asia", true);
    },
    unselect:function(){
        this.$refs.maps.shapeSelection(0, "continent", "Asia", false);
    }
}

}
</script>
<style>
  .wrapper {
    max-width: 400px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Initial shape selection

Initially, the shape can be selected by using the property `initialShapeSelection` and the values are mapped to the `shapePath` and `shapeValue`.

**Note:** initialShapeSelection is an Array property.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps  >
                <e-layers>
                    <e-layer :shapeData='shapeData' :selectionSettings= 'selectionSettings' :initialShapeSelection= 'initialShapeSelection'></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Marker, Legend, Selection } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        selectionSettings: {
            enable: true,
            fill: 'green',
            border: { color: 'white', width: 2}
        },
        shapeData: world_map,
        initialShapeSelection: [
            { shapePath: 'continent', shapeValue: 'Africa' },
            { shapePath: 'name', shapeValue: 'India' }
        ],
    }
},
provide: {
    maps: [Selection, Marker]
}
}
</script>
<style>
  .wrapper {
    max-width: 400px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## State Persistence

State persistence allows the Maps to retain the current modal value in the browser cookies for state maintenance. This action is handled through the `enablePersistence` property which is set to false by default. When it is set to true, some of the Maps component model values will be retained even after refreshing the page.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :enablePersistence='enablePersistence' :zoomSettings='zoomSettings'>
                <e-layers>
                    <e-layer :shapeData='shapeData'></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Zoom } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        zoomSettings: {
          enable: true
        },
        enablePersistence:true,
        shapeData: world_map
    }
},
provide: {
    maps: [Zoom]
}
}
</script>
<style>
  .wrapper {
    max-width: 400px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Highlight

Each shape in the Map can be highlighted during mouse over on the shapes.

Hovering on the specific legend, the map items which are bounded to the selected legend is also highlighted and vice versa.

The layer `highlightSettings.fill` property is used to change the highlighted layer shape color. The `highlightSettings.border.color` and `highlightSettings.border.width` properties are used to customize the highlighted shape border.

You can highlight the shape by mouse over on the shape. The highlight is enabled by the `highlightSettings.enable` property of shape layer. When `highlightSettings.enable` is set to false, the shapes cannot be highlighted.

**Note:** Highlight is separate module, need to inject to work on Highlight.

Refer the [`API`](../api/maps/highlightSettingsModel/) and code snippet for Highlight.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' :highlightSettings='highlightSettings' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Highlight } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        shapeData: world_map,
        highlightSettings: {
            enable: true,
            fill: 'green',
            border: { color: 'white', width: 2}
        }
    }
},
provide: {
    maps: [Highlight]
}
}
</script>
<style>
  .wrapper {
    max-width: 400px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Tooltip

Tooltip used to get more information about layer or bubble or marker on mouse over or touch end event performing on that. Tooltip is a separate module, So it needs module injection to work maps tooltip. Using `provide` option you can inject maps tooltip module into maps.

Tooltip can be enabled separately for layer or bubble or marker by using `tooltipSettings.visible` as **true**. Tooltip `valuePath` value need to set to display dataSource which field as tooltip text.
Below code snippet illustrate the tooltip enabled for layer to show shape data name field.

Refer the [`API`](../api/maps/tooltipSettingsModel/) for Tooltip feature.

**Step: 1** Import the world map geo json data from already created world-map.ts file and assign to `shapeData`.

**Step: 2** Import MapsTooltip module from `ej2-maps` package and Inject to Maps.

**Step: 3** Enable tooltip for layer using `tooltipSettings.visible` as true and bind `valuePath` value as 'name'.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' :tooltipSettings='tooltipSettings' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, MapsTooltip } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        shapeData: world_map,
        tooltipSettings: {
            visible: true,
            valuePath: 'name'
        }
    }
},
provide: {
    maps: [MapsTooltip]
}
}
</script>
<style>
  .wrapper {
    max-width: 400px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Tooltip template

Any HTML element can be displayed in tooltip using the ‘template’ property.

The following example shows tooltip template.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' :tooltipSettings='tooltipSettings' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, MapsTooltip } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';

let contentVue = Vue.component("contentTemplate", {
  template: '<div>Maps Tooltip Tempalte</div>',
  data() {
    return {
      data: {}
    };
  }
});
let contentTemplate = function() {
  return { template: contentVue };
};
Vue.use(MapsPlugin);
export default {
data () {
    return{
        shapeData: world_map,
        tooltipSettings: {
            visible: true,
            valuePath: 'name',
            template: contentTemplate
        }
    }
},
provide: {
    maps: [MapsTooltip]
}
}
</script>
<style>
  .wrapper {
    max-width: 400px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}