---
title: "Getting Started"
component: "Maps"
description: "Getting started in maps component"
---

# Getting Started

This section explains you the steps required to create a map and demonstrate the basic usage of the maps control.

You can explore some useful features in the Maps component using the following video.

`youtube:kwE6ikF7QYQ`

## Dependencies

Below is the list of minimum dependencies required to use the Maps.

```javascript
|-- @syncfusion/ej2-vue-maps
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-popups
       |-- @syncfusion/ej2-splitbuttons
       |-- @syncfusion/ej2-vue-base
    |-- @syncfusion/ej2-svg-base
    |-- @syncfusion/ej2-maps
```

## Get Started with Vue CLI

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your Vue applications.
To install Vue CLI use the following command.

```bash
npm install -g @vue/cli
npm install -g @vue/cli-init
```

Start a new project using below Vue CLI command.

```bash
vue init webpack-simple quickstart

cd quickstart
npm install

```

## Adding Syncfusion packages

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.
You can choose the component that you want to install. For this application, we are going to use Maps component.

To install Maps component, use the following command

```bash
npm install @syncfusion/ej2-vue-maps –save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.
* Vue.use()
* Vue.component()

### Using Vue.use()

Import the Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { MapsPlugin } from '@syncfuion/ej2-vue-maps';

Vue.use(MapsPlugin);
```

> By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the Component and Component Plugin from EJ2 Vue Package,
register the same using the Vue.component() with name of Component from ComponentPlugin
and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { MapsComponent, MapsPlugin } from '@syncfusion/ej2-vue-maps';

Vue.component(MapsPlugin.name, MapsComponent);
```

Note: By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Add Map to the Project

Add the EJ2 Vue Maps using `<ejs-maps>` to the `<template>` section of the `App.vue` file in src directory,
the content attribute of the Maps component is provided as name in data option in the `<script>` section.

```html
<template>
    <div class="wrapper">
        <ejs-maps id='maps'></ejs-maps>
    </div>
</template>
<script>
import Vue from 'vue';
import { MapsPlugin } from "@syncfusion/ej2-vue-maps";
Vue.use(MapsPlugin);

export default Vue.extend({
  data: function() {
    return {

    };
  }
});

</script>
```

Now use the `npm run dev` command to run the application in the browser.

```cmd
npm run dev
```

## Module Injection

Maps component are segregated into individual feature-wise modules. In order to use a particular feature,
you need to inject its feature module using `provide` option.  Find the modules available in maps and its description as follows.

* Annotations - Inject this provider to use annotations feature.
* Bubble - Inject this provider to use bubble feature.
* DataLabel - Inject this provider to use data label feature.
* Highlight - Inject this provider to use highlight feature.
* Legend - Inject this provider to use legend feature.
* Marker - Inject this provider to use marker feature.
* MapsTooltip - Inject this provider to use tooltip series.
* NavigationLine - Inject this provider to use navigation lines feature.
* Selection - Inject this provider to use selection feature.
* Zoom - Inject this provider to use zooming and panning feature.

In the current application, we are going to modify the above basic maps to visualize 2016 USA president election results.

For this application we are going to use tooltip, data label and legend features of the maps.
Now import the MapsTooltip, DataLabel and Legend modules from maps package and inject it into the Maps component using
`provide` option.

```html
<template>
   <div class="wrapper">
        <ejs-maps id='maps'></ejs-maps>
    </div>
</template>
<script>
import { MapsPlugin, Legend, DataLabel, MapsTooltip } from '@syncfusion/ej2-vue-maps';
Vue.use(MapsPlugin);
export default Vue.extend({
data:function(){
    return{ };
},
provide: {
    maps: [Legend, DataLabel, MapsTooltip]
}
});
</script>
```

## Render shapes from GeoJSON data

This section explains how to bind GeoJSON data to the map.

```javascript

let usMap: Object =
{
    "type": "FeatureCollection",
    "crs": { "type": "name", "properties": { "name": "urn:ogc:def:crs:OGC:1.3:CRS84" } },
    "features": [
        { "type": "Feature", "properties": { "iso_3166_2": "MA", "name": "Massachusetts", "admin": "United States of America" }, "geometry": { "type": "MultiPolygon", "coordinates": [ [ [ [ -70.801756294617277, 41.248076234530558 ]] ] ] }
        }
    ]
    //..
};

```

Elements in the maps will get rendered in the layers. So add a layer collection to the maps by using [`layers`](../api/maps/#layers) property. Now bind the GeoJSON data to the [`shapeData`](../api/maps/layerSettingsModel/#shapedata) property.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="map">
        <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { MapsPlugin } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data (){
    return{
        shapeData: world_map
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

{% endtab %}

> Note: Refer the data values for [`world_map`](https://www.syncfusion.com/downloads/support/directtrac/321036/ze/world_map1633413751.zip) here.

## Bind data source to map

The following properties in layers are used for binding data source to map.

* [`dataSource`]
* [`shapeDataPath`]
* [`shapePropertyPath`]

The [`dataSource`](../api/maps/layerSettingsModel/#datasource) property takes collection value as input. For example, the list of objects can be provided as input. This data is further used in tooltip, data label, bubble, legend and in color mapping.

The [`shapeDataPath`](../api/maps/layerSettingsModel/#shapedatapath) property used to refer the data ID in dataSource. Where as, the [`shapePropertyPath`](../api/maps/layerSettingsModel/#shapepropertypath) property is used to refer the column name in shapeData to identify the shape. Both the properties are related to each other. When the values of the shapeDataPath property in the dataSource property and the value of shapePropertyPath in the shapeData property match, then the associated object from the dataSource is bound to the corresponding shape.

The JSON object "permanent and non-permanent countries in the UN security council" is used as data source below.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="map">
        <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapePropertyPath='shapePropertyPath' :shapeDataPath='shapeDataPath' :dataSource='dataSource' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { MapsPlugin } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data (){
    return{
        shapeData: world_map,
        dataSource: [{  "Country": "China", "Membership": "Permanent"},
            {"Country": "France","Membership": "Permanent" },
            { "Country": "Russia","Membership": "Permanent"},
            {"Country": "Kazakhstan","Membership": "Non-Permanent"},
            { "Country": "Poland","Membership": "Non-Permanent"},
            {"Country": "Sweden","Membership": "Non-Permanent"}],
        shapePropertyPath: 'name',
        shapeDataPath: 'Country'
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

{% endtab %}

> Note: Refer the data values for [`world_map`](https://www.syncfusion.com/downloads/support/directtrac/321036/ze/world_map1633413751.zip) here.

## Apply Color Mapping

The Color Mapping feature supports customization of shape colors based on the underlying value of shape received from bounded data. Specify the field name from which the values have to be compared for the shapes in [`colorValuePath`] property in [`shapeSettings`].

Specify color and value in [`colorValuePath`](../api/maps/shapeSettingsModel/#colorvaluepath) property. Here '#D84444' is specified for 'Permanent' and '#316DB5' is specified for 'Non-Permanent'.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="map">
        <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapePropertyPath='shapePropertyPath' :shapeDataPath='shapeDataPath' :dataSource='dataSource' :shapeSettings='shapeSettings' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { MapsPlugin } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data (){
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
        }
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

{% endtab %}

## Add Title for Maps

You can add a title using [`titleSettings`](../api/maps/titleSettingsModel/) property to the map to provide quick
information to the user about the shapes rendered in the map.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="map">
        <div class='wrapper'>
            <ejs-maps  :titleSettings='titleSettings' >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapePropertyPath='shapePropertyPath' :shapeDataPath='shapeDataPath' :dataSource='dataSource' :shapeSettings='shapeSettings' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { MapsPlugin } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data (){
    return{
        titleSettings: {
            text: 'UN security council countries'
        },
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
        }
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

{% endtab %}

## Enable Legend

You can show legend for the maps by setting true to the [`visible`](../api/maps/legendSettingsModel/#visible) property in [`legendSettings`](../api/maps/legendSettingsModel/) object and by injecting the `Legend`
module using `provide` option.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="map">
        <div class='wrapper'>
            <ejs-maps :legendSettings='legendSettings' >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapePropertyPath='shapePropertyPath' :shapeDataPath='shapeDataPath' :dataSource='dataSource' :shapeSettings='shapeSettings' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { MapsPlugin, Legend } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
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

## Add Data Label

You can add data labels to show additional information of the shapes in map. This can be achieved by setting [`visible`](../api/maps/dataLabelSettingsModel/#visible) property to true in the [`dataLabelSettings`](../api/maps/dataLabelSettingsModel/) object and by injecting `DataLabel` module using `provide` option.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <div class='wrapper'>
            <ejs-maps :legendSettings='legendSettings' >
                <e-layers>
                    <e-layer :shapeData='shapeData':shapeSettings='shapeSettings' :dataLabelSettings='dataLabelSettings'></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Legend, DataLabel } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        shapeData: world_map,
        shapeSettings:{
            autofill: true
        },
        dataLabelSettings: {
            visible: true,
                labelPath: 'name',
                smartLabelMode: 'Trim'
        },
        legendSettings: {
            visible: true
        }
    }
},
provide: {
    maps: [Legend, DataLabel]
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

## Enable Tooltip

The tooltip is useful when you cannot display information by using the data labels due to space constraints.
You can enable tooltip by setting the [`visible`](../api/maps/tooltipSettingsModel/#visible) property as true
in [`tooltipSettings`](../api/maps/tooltipSettingsModel/) object and by injecting `MapsTooltip` module using
`provide` option.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps  :titleSettings='titleSettings' :legendSettings='legendSettings' >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapePropertyPath='shapePropertyPath' :shapeDataPath='shapeDataPath' :dataSource='dataSource' :shapeSettings='shapeSettings' :tooltipSettings='tooltipSettings' :dataLabelSettings='dataLabelSettings'></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Legend, DataLabel, MapsTooltip } from '@syncfusion/ej2-vue-maps';
import { usMap } from './usa.js';
import { electionData } from './election-data.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        titleSettings: {
            text: 'USA Election Results - 2016'
        },
        shapeData: usMap,
        dataSource: electionData,
        shapePropertyPath: 'name',
        shapeDataPath: 'State',
        shapeSettings: {
            colorValuePath: 'Candidate',
            colorMapping: [
            {
                value: 'Trump', color: '#D84444'
            },
            {
                value: 'Clinton', color: '#316DB5'
            }]
        },
        dataLabelSettings: {
            visible: true,
            labelPath: 'State',
            smartLabelMode: 'Trim'
        },
        tooltipSettings: {
            visible: true,
            valuePath: 'State'
        },
        legendSettings: {
            visible: true
        }
    }
},
provide: {
    maps: [Legend, DataLabel, MapsTooltip]
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