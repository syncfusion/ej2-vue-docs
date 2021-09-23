---
title: " Maps providers in Vue Maps control | Syncfusion "

component: "Maps"

description: "Learn here all about Maps providers of Syncfusion Vue Maps control and more."
---

# Map Providers in Vue Maps control

Maps control support map providers such as OpenStreetMap that can be added to any layers in maps.

## Open Street Map

OpenStreetMap(OSM) is a online map provider. The OpenStreetMap allows you to view, edit and use geographical data in a collaborative way from any place on the Earth. One of the most important features in Maps control is the built-in online map provider support. By using this feature, you can render OpenStreetMap in the maps component. This provides the ability to visualize street map tiles without using any external shape files.

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :layerType='layerType' :urlTemplate='urlTemplate' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin } from '@syncfusion/ej2-vue-maps';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        layerType: 'OSM',
        urlTemplate: 'http://a.tile.openstreetmap.org/level/tileX/tileY.png'
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

## Bing Maps

Bing Maps is a online map provider for accessing the external geospatial imagery services for deep-zoom satellite view which is supported in the Maps control. This provides the ability to visualize satellite, aerial, and street maps without using any external shape files.

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :layerType='layerType' :bingMapType='bingMapType' :key='key' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin } from '@syncfusion/ej2-vue-maps';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        layerType: 'Bing',
        bingMapType: 'AerialWithLabel',
        key: '// …bingMapKey'
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