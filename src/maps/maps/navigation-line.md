---
title: " Navigation Lines in Vue Maps control | Syncfusion "

component: "Maps"

description: "Learn here all about Navigation Lines feature of Syncfusion Vue Maps control and more."
---

# Navigation Lines in Vue Maps control

The navigation lines are used to denote the path between two locations. This feature can be used to draw flight or sea routes. Navigation lines are enabled by setting the [`visible`](../api/maps/navigationLineSettingsModel/#visible) property of the [`navigationLineSettings`](../api/maps/navigationLineSettingsModel) property to "**true**".

## Customization

The following properties are available in [`navigationLineSettings`](../api/maps/navigationLineSettingsModel/) property to customize the navigation line of the Maps component.

* [`color`](../api/maps/navigationLineSettingsModel/#color) - To apply the color for navigation lines in Maps.
* [`dashArray`](../api/maps/navigationLineSettingsModel/#dasharray) - To define the pattern of dashes and gaps that is applied to the outline of the navigation lines.
* [`width`](../api/maps/navigationLineSettingsModel/#width) - To customize the width of the navigation lines.
* [`angle`](../api/maps/navigationLineSettingsModel/#angle) - To customize the angle of the navigation lines.
* [`highlightSettings`](../api/maps/navigationLineSettingsModel/#highlightsettings) - To customize the highlight settings of the navigation line.
* [`selectionSettings`](../api/maps/navigationLineSettingsModel/#selectionsettings) - To customize the selection settings of the navigation line.

To navigate the line between two cities on the world map, use the code snippet below. The [`latitude`](../api/maps/navigationLineSettingsModel/#latitude) and [`longitude`](../api/maps/navigationLineSettingsModel/#longitude) values are used to indicate the start and end points of navigation lines drawn on Maps.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' >
                    <e-navigationLineSettings>
                    <e-navigationLineSetting visible = true :latitude ='latitude' :longitude ='longitude' :color ='color' :angle ='angle' :width="width" :dashArray='dashArray' >
                    </e-navigationLineSetting>
                    </e-navigationLineSettings>
                    </e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, NavigationLine } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return {
        shapeData: world_map,
        latitude: [40.7128, 36.7783],
        longitude: [-74.0060, -119.4179],
        color: 'black',
        angle: 90,
        width: 2,
        dashArray: '4'
    }
},
provide: {
    maps: [NavigationLine]
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

## Enabling the arrows

To enable the arrow in the navigation line, set the [`showArrow`](../api/maps/arrowModel/#showarrow) property of [`arrowSettings`](../api/maps/navigationLineSettingsModel/#arrowsettings) property to "**true**". The following properties are available in [`arrowSettings`](../api/maps/navigationLineSettingsModel/#arrowsettings) property to customize the arrow of the navigation lines.

* [`color`](../api/maps/arrowModel/#color) - To apply the color for arrow of the navigation line.
* [`offset`](../api/maps/arrowModel/#offset) - To customize the offset position of the arrow of the navigation line.
* [`position`](../api/maps/arrowModel/#position) - To customize the position of the arrow in navigation line. The possible values can be "**Start**" and "**End**".
* [`size`](../api/maps/arrowModel/#size) - To customize the size of the arrow in pixels.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' >
                    <e-navigationLineSettings>
                    <e-navigationLineSetting visible = true :latitude ='latitude' :longitude ='longitude' :color ='color' :angle ='angle' :width="width" :dashArray='dashArray' :arrowSettings = 'arrowSettings' >
                    </e-navigationLineSetting>
                    </e-navigationLineSettings>
                    </e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, NavigationLine } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return {
        latitude: [37.6276571, -14.2350],
        longitude: [-74.0060, -51.9253],
        color: 'black',
        angle: -180,
        width: 2,
        dashArray: '4',
        arrowSettings: {
            showArrow: true,
            size: 10,
            position: 'Start'
        },
        shapeData: world_map,
    }
},
provide: {
    maps: [NavigationLine]
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