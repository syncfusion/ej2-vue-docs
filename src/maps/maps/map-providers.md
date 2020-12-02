---
title: "Map Providers"
component: "Maps"
description: "Map Providers support in maps"
---

# Map Providers

Map control support map providers such as OpenStreetMap that can be added to any layers in maps.

## Open Street Map

`OpenStreetMap` is a map of the entire world. The OpenStreetMap allows you to view, edit and use geographical data in a collaborative way from any place on the Earth.

### Enable OSM

You can enable this feature by setting the layerType property value as “OSM”.

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

#### URL Template

The `urlTemplate` property determines the format of tile map. You can specify the template for the tile layer.

## Bing Map

Bing Map is a key feature in accessing the external geospatial imagery services for deep-zoom satellite view.

### Enable Bing Maps

You can enable this feature by defining the layerType as “bing”. To get the type of bing map as aerial, aerial with label and road.

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

#### Key

The bing Map key is provided as input to this key property. The Bing Map key can be obtained from [http://www.microsoft.com/maps/create-a-bing-maps-key.aspx](http://www.microsoft.com/maps/create-a-bing-maps-key.aspx).
