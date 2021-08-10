---
title: " Layers in Vue Maps control | Syncfusion "

component: "Maps"

description: "Learn here all about Layers feature of Syncfusion Vue Maps control and more."
---

# Layers in Vue Maps control

The Maps control is rendered through [`layers`](../api/maps/#layers) and any number of layers can be added to the Maps.

## Multilayer

The Multilayer support allows loading multiple shape files and map providers in a single container, enabling Maps to display more information. The shape layer or map providers are the main layers of the Maps. Multiple layers can be added as **SubLayer** over the main layers using the [`type`](../api/maps/layerSettingsModel/#type) property of [`layers`](../api/maps/#layers) property.

## Sublayer

Sublayer is a type of shape file layer. It allows loading multiple shape files in a single map view. For example, a sublayer can be added over the main layer to view geographic features such as rivers, valleys and cities in a map of a country. Similar to the main layer, elements in the Maps such as markers, bubbles, color mapping and legends can be added to the sub-layer.

In this example, the United States map shape is used as shape data by utilizing "**usa.ts**" file, and "**texas.ts**" and "**california.ts**" files are used as sub-layers in the United States map.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapeSettings='shapeSettings' ></e-layer>
                     <e-layer :shapeData='shapeData1' :type = 'type' :shapeSettings='shapeSettings1' ></e-layer>
                     <e-layer :shapeData='shapeData2' :type = 'type' :shapeSettings='shapeSettings2' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin } from '@syncfusion/ej2-vue-maps';
import { usMap } from './usa.js';
import { california } from './california.js';
import { texas } from './texas.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        shapeData: usMap,
        shapeSettings: {
            fill: '#E5E5E5',
            border: {
                color: 'black',
                width: 0.1
            }
        },
        shapeData1: texas,
        type: 'SubLayer',
        shapeSettings1: {
            fill: 'rgba(141, 206, 255, 0.6)',
            border: {
                color: '#1a9cff',
                width: 0.25
            }
        },
        shapeData2: california,
        shapeSettings2: {
            fill: 'rgba(141, 206, 255, 0.6)',
            border: {
                color: '#1a9cff',
                width: 0.25
            }
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

{% endtab %}

## Displaying different layer in the view

Multiple shape files and map providers can be loaded simultaneously in Maps. The [`baseLayerIndex`](../api/maps/mapsModel/#baselayerindex) property is used to determine which layer on the user interface should be displayed. This property is used for the Maps drill-down feature, so when the [`baseLayerIndex`](../api/maps/mapsModel/#baselayerindex) value is changed, the corresponding shape is loaded. In this example, two layers can be loaded with the World map and the United States map. Based on the given [`baseLayerIndex`](../api/maps/mapsModel/#baselayerindex) value the corresponding shape will be loaded in the user interface. If the [`baseLayerIndex`](../api/maps/mapsModel/#baselayerindex) value is set to 0, then the world map will be loaded.

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
