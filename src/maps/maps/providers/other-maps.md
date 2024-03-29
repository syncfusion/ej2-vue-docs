---
title: "Other Map Providers in Vue Maps control | Syncfusion"

component: "Maps"

description: "Learn here all about Other Map Providers of Syncfusion Vue Maps control and more."
---

# Other Maps providers in Vue Maps control

Apart from the OpenStreetMap and Bing Maps, you can also render the Maps from other map service providers by specifying [`layerType`](../api/maps/layerSettingsModel/#layertype) as **OSM** and the URL generated by map provider in the [`urlTemplate`](../api/maps/layerSettingsModel/#urlTemplate) property. Here, Google Maps is rendered. This provides customizable Maps with your own content and imagery.

>Refer to [Google Maps Licensing](https://developers.google.com/maps/terms#10-license-restrictions).

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :layerType= 'layerType' :urlTemplate= 'urlTemplate'>
                    </e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, MapsComponent, Annotations } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
       layerType: 'OSM',
       urlTemplate: "http://mt1.google.com/vt/lyrs=m@129&hl=en&x=tileX&y=tileY&z=level"
    }
},
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

## Zooming and Panning

Tile Maps layer can be zoomed and panned. Zooming helps to get a closer look at a particular area on a Maps for in-depth analysis. Panning helps to move a Maps around to focus the targeted area.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :zoomSettings= 'zoomSettings'>
                <e-layers>
                    <e-layer :layerType= 'layerType' :urlTemplate= "urlTemplate">
                    </e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, MapsComponent, Zoom } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
       zoomSettings: {
           enable: true,
       },
       layerType: 'OSM',
       urlTemplate: "http://mt1.google.com/vt/lyrs=m@129&hl=en&x=tileX&y=tileY&z=level"
    }
},
provide: {
    maps: [ Zoom ]
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

## Adding markers and navigation line

Markers can be added to the layers of tile Maps by setting the corresponding location's coordinates of latitude and longitude using [`markerSettings`](../api/maps/layerSettingsModel/#markersettings). Navigation lines can be added on top of an tile Maps layer for highlighting a path among various places by setting the corresponding location's coordinates of latitude and longitude in the [`navigationLineSettings`](../api/maps/layerSettingsModel/#navigationlinesettings).

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :zoomSettings= 'zoomSettings' :centerPosition="centerPosition">
                <e-layers>
                    <e-layer :layerType= 'layerType' :urlTemplate= "urlTemplate">
                        <e-markerSettings>
                            <e-markerSetting visible= true height=25 width=15 :dataSource ="dataSource" ></e-markerSetting>
                            <e-markerSetting visible= true height=25 width=15 :dataSource ="dataSource1"></e-markerSetting>
                        </e-markerSettings>
                        <e-navigationLineSettings>
                            <e-navigationLineSetting visible = true :latitude ='latitude' :longitude ='longitude' :color ='color' :angle ='angle' :width="width">
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
import { MapsPlugin, MapsComponent, NavigationLine, Marker, Zoom } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
       zoomSettings: {
           zoomFactor: 4
       },
       centerPosition: {
            latitude: 29.394708,
            longitude: -94.954653
        },
       layerType: 'OSM',
       urlTemplate: "http://mt1.google.com/vt/lyrs=m@129&hl=en&x=tileX&y=tileY&z=level",
       dataSource: [
            {
                latitude: 34.060620,
                longitude: -118.330491,
                name: "California"
        }],
        dataSource1: [
            {
                latitude: 40.724546,
                longitude: -73.850344,
                name: "New York"
        }],
        color: "blue",
        width: 5,
        angle: 0.1,
        latitude: [34.060620, 40.724546],
        longitude: [-118.330491,-73.850344]
    }
},
provide: {
    maps: [ Zoom, NavigationLine, Marker ]
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

## Sublayer

Any GeoJSON shape can be rendered as a sublayer on top of the tile Maps layer for highlighting a particular continent or country in tile Maps by adding another layer and specifying the [`type`](../api/maps/layerSettingsModel/#type) property of Maps layer to **SubLayer**.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :layerType= 'layerType' :urlTemplate="urlTemplate"></e-layer>
                    <e-layer :shapeData='shapeData1' :type = 'type' :shapeSettings='shapeSettings1' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, MapsComponent, NavigationLine, Marker, Zoom } from '@syncfusion/ej2-vue-maps';
import { usMap } from './usa.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
       layerType: 'OSM',
       urlTemplate: "http://mt1.google.com/vt/lyrs=m@129&hl=en&x=tileX&y=tileY&z=level",
       shapeData1: usMap,
       type: 'SubLayer',
       shapeSettings1: {
           fill: 'blue'
       }
    }
},
provide: {
    maps: [ NavigationLine, Marker, Zoom ]
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