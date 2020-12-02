---
title: "Bubble"
component: "Maps"
description: "Bubble support in maps"
---

# Bubble

Bubbles in the Maps control represent the underlying data values of the map. Bubbles are scattered throughout the map shapes that contains bound values.

Bubbles are included when data binding and the `bubbleSettings` is set to the shape layers.

To add bubbles to the map, bind data source to the layer `bubbleSettings` and set the `valuePath` as population. Following example illustrates bubble enable for the World map with **datasource**.
To render bubble in maps need to import `Bubble` module.

```typescript
export let world_map = // paste the world map from worldMap.json Geo json file.
```

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapePropertyPath='shapePropertyPath' :shapeDataPath='shapeDataPath' :bubbleSettings='bubbleSettings' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Bubble } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        shapeData: world_map,
        shapeDataPath: 'name',
        shapePropertyPath: 'name',
       bubbleSettings: [{
            visible: true,
            minRadius: 20,
            dataSource: [
                { name: 'India', population: '38332521' },
                { name: 'New Zealand', population: '19651127' },
                { name: 'Pakistan', population: '3090416' }
            ],
            maxRadius: 40,
            valuePath: 'population'
        }]
    }
},
provide: {
    maps: [Bubble]
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

## Bubble Sizing

Using the `minRadius` and `maxRadius` properties in `bubbleSettings`, you can render the bubbles in different sizes based on the `valuePath` and `dataSource` values

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapePropertyPath='shapePropertyPath' :shapeDataPath='shapeDataPath' :bubbleSettings='bubbleSettings' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Bubble } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        shapeData: world_map,
        shapeDataPath: 'name',
        shapePropertyPath: 'name',
       bubbleSettings: [{
            visible: true,
            minRadius: 5,
            dataSource: [
                { name: 'India', population: '38332521' },
                { name: 'New Zealand', population: '19651127' },
                { name: 'Pakistan', population: '3090416' }
            ],
            maxRadius: 80,
            valuePath: 'population'
        }]
    }
},
provide: {
    maps: [Bubble]
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

## Multiple bubble groups

You can specify multiple types of bubble groups using the `bubbleSettings` property and customize it according to your requirement.

In the following code example, the gender-wise population ratio is demonstrated with two different bubble groups.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapePropertyPath='shapePropertyPath' :shapeDataPath='shapeDataPath' :bubbleSettings='bubbleSettings' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Bubble } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        shapeData: world_map,
        shapeDataPath: 'name',
        shapePropertyPath: 'name',
        bubbleSettings: [{
            visible: true,
            minRadius: 5,
            valuePath: "femaleRatio",
            colorValuePath: "femaleRatioColor",
            dataSource: [
                {
                    country: "United States", femaleRatio: 50.50442726, maleRatio: 49.49557274, femaleRatioColor: "green", maleRatioColor: "blue"
                },
                {
                    country: "India", femaleRatio: 48.18032713, maleRatio: 51.81967287, femaleRatioColor: "blue", maleRatioColor: "#c2d2d6"
                },
                {
                    country: "Oman", femaleRatio: 34.15597234, maleRatio: 65.84402766, femaleRatioColor: "#09156d", maleRatioColor: "orange"
                },
                {
                    country: "United Arab Emirates", femaleRatio: 27.59638942, maleRatio: 72.40361058, femaleRatioColor: "#09156d", maleRatioColor: "orange"
                }
            ],
            maxRadius: 20,
        },
        {
            visible: true,
            bubbleType: 'Circle',
            opacity: 0.4,
            minRadius: 15,
            valuePath: "maleRatio",
            colorValuePath: "maleRatioColor",
            dataSource: [
                {
                    country: "United States", femaleRatio: 50.50442726, maleRatio: 49.49557274, femaleRatioColor: "green", maleRatioColor: "blue"
                },
                {
                    country: "India", femaleRatio: 48.18032713, maleRatio: 51.81967287, femaleRatioColor: "blue", maleRatioColor: "#c2d2d6"
                },
                {
                    country: "Oman", femaleRatio: 34.15597234, maleRatio: 65.84402766, femaleRatioColor: "#09156d", maleRatioColor: "orange"
                },
                {
                    country: "United Arab Emirates", femaleRatio: 27.59638942, maleRatio: 72.40361058, femaleRatioColor: "#09156d", maleRatioColor: "orange"
                }
            ],
            maxRadius: 25,
        }]
    }
},
provide: {
    maps: [Bubble]
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

## Enable Legend for Bubble

To enable the legend for the bubble, need to set `legendSettings.visible` as true and `legendSettings.type` as 'Bubbles'. To render the legend in maps need to Inject Legend module using `provide` option.
Refer the below code snippet to enable the legend for bubbles with each bubble different colors rendering.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :legendSettings='legendSettings' >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapePropertyPath='shapePropertyPath' :shapeDataPath='shapeDataPath' :bubbleSettings='bubbleSettings' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Bubble, Legend } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        legendSettings: {
            visible: true,
            type: 'Bubbles'
        },
         shapeData: world_map,
        shapeDataPath: 'name',
        shapePropertyPath: 'name',
        bubbleSettings: [{
            visible: true,
            minRadius: 20,
            dataSource: [
                {color: 'green', name: 'India', population: '38332521' },
                {color: 'purple', name: 'New Zealand', population: '19651127' },
                {color: 'blue', name: 'Pakistan', population: '3090416' }
            ],
            maxRadius: 40,
            colorValuePath: 'color',
            valuePath: 'population'
        }]
    }
},
provide: {
    maps: [Bubble, Legend]
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