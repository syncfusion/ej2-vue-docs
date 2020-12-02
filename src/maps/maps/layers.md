---
title: "Layers"
component: "Maps"
description: "Layers support in maps"
---

# Layers

Map is maintained through `layers` and it can accommodate one or more layers.

## Multilayer

The Multilayer support allows you to load multiple shape files in a single container, enabling maps to display more information.

### Adding Multiple Layers in the Map

The shape layers is the core layer of the map. The multiple layers can be added in the shape layers as `subLayers` within the shape layers.

## SubLayer

The SubLayer is the collection of shape layers.

In this example, USA Map shape is used as shape data by utilizing the `USA.json”` file in the following folder structure obtained from downloaded Maps_GeoJSON folder.

..\ Maps_GeoJSON\

You can assign the complete contents in `WorldMap.json` file to new JSON object. For better understanding, a TS file `WorldMap.ts` is already created to store JSON data in JSON object “world_map” and also copy the California.json file data, bind value to usa like “world_map”.

`[world_map.ts]`

```typescript
export let world_map = //Paste all the content copied from the world_map.JSON file//
```

`[California.ts]`

```typescript
export let world_map = //Paste all the content copied from the world_map.JSON file//
```

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapeSettings='shapeSettings' ></e-layer>
                     <e-layer :shapeData='shapeData1' :type = 'type' :shapeSettings='shapeSettings1' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin } from '@syncfusion/ej2-vue-maps';
import { usMap } from './usa.js';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        shapeData: world_map,
        shapeSettings: {
            fill: '#9CBF4E',
            border: { width: 0.5, color: 'White' },
        },
        shapeData1: usMap,
        type: 'SubLayer',
        shapeSettings1: {
            fill: 'orange',
            border: { width: 1, color: 'White' },
        },
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

## Displaying layer in the view

In Maps, you can load multiple shape files. Using the `baseLayerIndex` property, you can select a layer to display on user interface.

In this example, we have loaded two layers with the World map and the United States map shape data and selected a layer using the `baseLayerIndex` property to show that layer on the web page.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :baseLayerIndex= "baseLayerIndex">
                <e-layers>
                    <e-layer :shapeData='shapeData'></e-layer>
                    <e-layer :shapeData='shapeData1'></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin } from '@syncfusion/ej2-vue-maps';
import { usMap } from './usa.js';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        baseLayerIndex: 1,
        shapeData: world_map,
        shapeData1: usMap,
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
