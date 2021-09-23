---
title: "Bing Maps in Vue Maps control | Syncfusion"

component: "Maps"

description: "Learn here all about Bing Maps of Syncfusion Vue Maps control and more."
---

# Bing Maps in Vue Maps control

Bing Maps is a online Maps provider, owned by Microsoft. As like OSM, it provide Maps tile images based on our requests and combines those images into a single one to display Maps area.

## Adding Bing Maps

The Bing Maps can be rendered by setting the [`layerType`](../api/maps/layerSettingsModel/#layertype) property as **Bing** and the key for the Bing Maps must be set in the [`key`](../api/maps/layerSettingsModel/#key) property. The Bing Maps key can be obtained from [here](https://www.microsoft.com/en-us/maps/create-a-bing-maps-key).

```typescript
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :layers='layers'>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Marker } from '@syncfusion/ej2-vue-maps';
Vue.use(MapsPlugin);
export default {
data () {
    return {
      layers: [
        {
            layerType: 'Bing',
            // Provide your bing map key here
            key: '// ...bingMapKey'
        }
    ]
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

>Specifies Bing Maps key in the `key` property.

## Types of Bing Maps

Bing Maps provides different types of Maps and it is supported in the Maps control.

* **Aerial** - Displays satellite images to highlight roads and major landmarks for easy identification.
* **AerialWithLabel** - Displays aerial Maps with labels for the continent, country, ocean, etc.
* **Road** - Displays the default Maps view of roads, buildings, and geography.
* **CanvasDark** - Displays dark version of the road Maps.
* **CanvasLight** - Displays light version of the road Maps.
* **CanvasGray** - Displays grayscale version of the road Maps.

To render the light version of the road Maps, set the `bingMapType` to `CanvasLight` as demonstrated in the following code sample.

```typescript
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :centerPosition="centerPosition" :layers='layers'>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin} from '@syncfusion/ej2-vue-maps';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        layers: [{
           layerType: 'Bing',
           bingMapType: 'CanvasLight',
           key: '// ...bingMapKey',
        }],
        centerPosition: {
            latitude: 38.8951,
            longitude: -77.0364
        }
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

>Specify Bing Maps key in the `key` property.

## Zooming and Panning

Markers can be added to the layers of Bing Maps by setting the corresponding location's coordinates of latitude and longitude using [`markerSettings`](../api/maps/layerSettingsModel/#markersettings). Navigation lines can be added on top of an Bing Maps layer for highlighting a path among various places by setting the corresponding location's coordinates of latitude and longitude in the [`navigationLineSettings`](../api/maps/layerSettingsModel/#navigationlinesettings).

```typescript
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :zoomSettings='zoomSettings' :layers='layers'>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Zoom } from '@syncfusion/ej2-vue-maps';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        zoomSettings: {
            enable: true,
            toolBars: ["Zoom", "ZoomIn", "ZoomOut", "Pan", "Reset"]
        },
        layers: [{
            layerType: 'Bing',
            bingMapType: 'CanvasLight',
            key: '// ...bingMapKey',
        }]
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

## Adding markers and navigation line

Markers can be added to the layers of Bing Maps by setting the corresponding location's coordinates of latitude and longitude using [`markerSettings`](../api/maps/layerSettingsModel/#markersettings). Navigation lines can be added on top of an Bing Maps layer for highlighting a path among various places by setting the corresponding location's coordinates of latitude and longitude in the [`navigationLineSettings`](../api/maps/layerSettingsModel/#navigationlinesettings).

```typescript
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :layers='layers' :zoomSettings='zoomSettings'>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Zoom, Marker, NavigationLine } from '@syncfusion/ej2-vue-maps';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        zoomSettings: {
            enable: true
        },
        layers: [{
            layerType: 'Bing',
            bingMapType: 'CanvasLight',
            key: '// ...bingMapKey',
            markerSettings: [{
                visible: true,
                height: 25,
                width: 15,
                dataSource: [{
                    latitude: 34.060620,
                    longitude: -118.330491,
                    name: "California"
               }]
            },
           {
                visible: true,
                height: 25,
                width: 15,
                dataSource: [{
                    latitude: 40.724546,
                    longitude: -73.850344,
                     name: "New York"
                }]
            }],
            navigationLineSettings: [{
                visible: true,
                color: "blue",
                angle: 0.1,
                width: 5,
                latitude: [34.060620, 40.724546],
                longitude: [-118.330491,-73.850344]
           }]
       }]
    }
},
provide: {
    maps: [Zoom, Marker, NavigationLine]
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

>Specify Bing Maps key in the `Key` property.

## Sublayer

Any GeoJSON shape can be rendered as a sublayer on top of the Bing Maps layer for highlighting a particular continent or country in Bing Maps by adding another layer and specifying the [`type`](../api/maps/layerSettingsModel/#type) property of Maps layer to **SubLayer**.
