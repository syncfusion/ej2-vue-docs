---
title: "Populate Data"
component: "Maps"
description: "Explains how to populate data in maps component"
---

# Populate Data

In this section you can learn how to populate shape data for providing Data input to Map control and usage of DataSource property.

## Shape Data

The Shape Data collection describing geographical shape information can be obtained from
[GEOJSON format shapes](http://files2.syncfusion.com/dtsupport/uploads/user/uploads/Maps_GeoJSON.zip).

.\ Maps_GeoJSON\All Countries with States

You can assign the complete contents in `“WorldMap.json”` file to new JSON object. For better understanding, a TS file `“world-map.js”` is already created to store JSON data in JSON object “worldMap”.

`[world-map.ts]`

```typescript
export let worldMap = //Paste all the content copied from the JSON file//
```

## Data Binding

The Maps control supports data binding with the `dataSource` property in the shape layers.

### Properties

The following properties in shape layers is be used for binding data in Maps control,

    * dataSource
    * shapeDataPath
    * shapePropertyPath

## Data Source

The dataSource property accepts the collection values as input. For example, you can provide the list of objects as input.

## Shape Data Path

The `shapeDataPath` property is used to refer the data ID in DataSource. For example, population MapData contains data ids ‘Name’ and ‘Population’. The `shapeDataPath` and the `shapePropertyPath` properties are related to each other (refer to `shapePropertyPath` for more details).

## Shape Property Path

The `shapePropertyPath` property is similar to the `shapeDataPath` that refers to the column name in the `data` property of shape layers to identify the shape. When the values of the `shapeDataPath` property in the `dataSource` property and the value of `shapePropertyPath` in the data property match, then the associated object from the `dataSource` is bound to the corresponding shape.

The datasource is populated with JSON data relative to shape data and stored in JSON object. The world countries population as datasource is used for better understanding.

The “populationData.ts” file is used to store JSON data in JSON object “populationData”.

Refer both shape data and datasource as illustrated in the following code example.

`[populationData.ts]`

```typescript
export let populationData: object[] = [{  "Country": "China", "Membership": "Permanent"},
            {"Country": "France","Membership": "Permanent" },
            { "Country": "Russia","Membership": "Permanent"},
            {"Country": "Kazakhstan","Membership": "Non-Permanent"},
            { "Country": "Poland","Membership": "Non-Permanent"},
            {"Country": "Sweden","Membership": "Non-Permanent"}],
```

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :legendSettings='legendSettings'>
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapePropertyPath='shapePropertyPath' :shapeDataPath='shapeDataPath' :dataSource='dataSource' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Legend } from '@syncfusion/ej2-vue-maps';
import { world_map} from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        shapeData: world_map,
        dataSource: [{  "Country": "China", "Membership": "Permanent"},
            {"Country": "France","Membership": "Permanent" },
            { "Country": "Russia","Membership": "Permanent"},
            {"Country": "Kazakhstan","Membership": "Non-Permanent"},
            { "Country": "Poland","Membership": "Non-Permanent"},
            {"Country": "Sweden","Membership": "Non-Permanent"}],
        shapePropertyPath: 'name',
        shapeDataPath: 'Country',
        shapeSettings: {
            colorValuePath: 'Membership',
                colorMapping: [
                {
                    value: 'Permanent', color: '#D84444'
                },
                {
                    value: 'Non-Permanent', color: '#316DB5'
                }]
        },
        legendSettings: {
            visible: true
        }
    }
},
provide: {
    maps: [Legend]
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

## Binding complex data source

You can bind the data field from data source to the maps in two different ways.

1. Bind the field name directly to the properties as [`shapeDataPath`](../api/maps/layerSettings/#shapedatapath), [`colorValuePath`](../api/maps/markerSettings/#colorvaluepath),
[`valuePath`](../api/maps/tooltipSettings/#valuepath) and [`shapeValuePath`](../api/maps/markerSettings/#shapevaluepath).

2. Bind the field name as `data.field` to the properties as [`shapeDataPath`](../api/maps/layerSettings/#shapedatapath), [`colorValuePath`](../api/maps/markerSettings/#colorvaluepath),
[`valuePath`](../api/maps/tooltipSettings/#valuepath) and [`shapeValuePath`](../api/maps/markerSettings/#shapevaluepath).

The complex data source binding can be done as illustrated in the following code example.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps>
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapePropertyPath='shapePropertyPath' :shapeDataPath='shapeDataPath' :dataSource='dataSource' :tooltipSettings='tooltipSettings' :bubbleSettings='bubbleSettings'
                    :markerSettings='markerSettings'></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, MapsTooltip, Marker, Bubble } from '@syncfusion/ej2-vue-maps';
import { world_map} from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        shapeData: world_map,
        dataSource: [{ "Continent": "North America", 'color': '#71B081',
            data: { "continent": "North America", 'color': '#71B081' }
            },
            { "Continent": "South America", 'color': '#5A9A77',
            data: { "continent": "South America", 'color': '#5A9A77' }
            },
            { "Continent": "Africa", 'color': '#498770',
            data: { "continent": "Africa", 'color': '#498770' }
            },
            { "Continent": "Europe", 'color': '#39776C',
            data: { "continent": "Europe", 'color': '#39776C' }
            },
            { "Continent": "Asia", 'color': '#266665',
            data: { "continent": "Asia", 'color': '#266665' }
            },
            { "Continent": "Australia", 'color': '#124F5E',
            data: { "continent": "Australia", 'color': '#124F5E' }
            }],
        shapePropertyPath: 'continent',
        shapeDataPath: 'data.continent',
        shapeSettings: {
            colorValuePath: 'data.color',
        },
        tooltipSettings: {
            visible: true,
            valuePath: 'data.continent'
        },
         bubbleSettings: [
            {
                visible: true,
                valuePath: 'data.value',
                colorValuePath: 'data.color',
                animationDuration: 0,
                minRadius: 20,
                maxRadius: 90,
                opacity: 0.8,
                dataSource: [
                    { 'name': 'India', 'value': 18.89685398845257, 'population': 391292635,
                    data: { 'color': 'red', 'population': 391292635, 'value': 189685398845257 }
                    }
                ],
                tooltipSettings: {
                    visible: true,
                    valuePath: 'data.population',
                    template:"<div>${data.population}</div>"
                },
            },
        ],
        markerSettings: [
            {
                visible: true,
                dataSource: [
                    { latitude: 37.6276571, longitude: -122.4276688, name: 'San Bruno',
                    data: { x: 37.6276571, y: -122.4276688, name: 'San Bruno', shape: 'Pentagon',
                    color: 'red', imageUrl: 'images/ballon.png' }
                    },
                    { latitude: 33.5302186, longitude: -117.7418381, name: 'Laguna Niguel',
                    data: { x: 33.5302186, y: -117.7418381, name: 'Laguna Niguel', color: 'blue',
                    shape: 'Pentagon', imageUrl: 'images/ballon.png' }
                    }
                ],
                shapeValuePath: "data.shape",
                colorValuePath: "data.color",
                height: 20,
                width: 20,
                offset: {
                    y: -10,
                    x: 0
                },
                longitudeValuePath: "data.y",
                latitudeValuePath: "data.x",
                tooltipSettings: {
                    visible: true,
                    valuePath: 'data.name',
                    format: "${data.name}: ${data.x} : ${data.y}"
                },
                animationDuration: 0
            },
        ]
    }
},
provide: {
    maps: [Marker, Bubble, MapsTooltip]
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
