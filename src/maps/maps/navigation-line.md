---
title: "Navigation Lines"
component: "Maps"
description: "Navigation lines support in maps"
---

# Navigation Lines

Navigation lines are used to denote the path between the two locations. We can use this feature as flight or train or sea routes.

## Customization

You can customize the following properties in the navigation lines by modifying their default values in `navigationLineSettings`

* Color - Specifies the color of navigation line.
* Dash array - Specifies the type of dash array line.
* Width - Specifies the line width.
* Angle - Specifies the navigation line angle.
* Highlight settings - Customizes the opacity, border, and fill color when the cursor hovers over it.
* Selection settings - Customizes the opacity, border, and fill color when the line is selected.

Following example shows rendering the path between two locations using latitudes and longitudes.

Yon can customize the navigation line color, dashArray, width and angle by modifying their default values in
`navigationLineSettings`.

Refer the below code snippet to navigate line between two cities in world map.
Import world_map geo json data from world-map.ts file.
Import the `NavigationLine` Module and Inject into the Maps using `provide` option.
Provide two locations latitude and longitude values to `navigationLineSettings`.

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
    return{
            latitude: [37.6276571, -14.2350],
            longitude: [-74.0060, -51.9253],
            color: 'black',
            angle: -180,
            width: 2,
            dashArray: '4',
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

## Enabling the arrows

You can enable the arrows in the navigation line using [`arrowSettings.showArrow`](../api/maps/arrow) API, also you can customize following properties in arrow

* color - Specifies the color of the arrow
* offset - Specifies the arrow's offset position
* position - Specifies the arrow position to `start` or `end` line
* size - Specifies the arrow size in pixel

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
    return{
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
            }
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