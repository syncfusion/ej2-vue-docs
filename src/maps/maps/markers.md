---
title: "Markers"
component: "Maps"
description: "Markers support in maps"
---

# Markers

Markers are notes that are used to leave a message on the map. It indicates or marks a specific location with desired symbols on the maps.

The `dataSource` property has a list of objects that contains data for markers. By default, it displays the bound data at the specified latitude and longitude. Using the `visible` API, you can enable or disable the markers.

There are two ways to set marker for map.

* Marker and marker template

* Adding marker objects to map.

## Marker and marker template

The `markerSettings.dataSource` property has a list of objects that contains the data for Annotation. By default, it displays the bound data at the specified latitude and longitude. The `markerSettings.template` property is used for customizing the template for markers.

**Note:** markerSettings is an Array property.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' >
                        <e-markerSettings>
                            <e-markerSetting visible= true :template='contentTemplate' :dataSource ="dataSource" animationDuration = 0 ></e-markerSetting>
                            <e-markerSetting visible= true :template='contentTemplate1' :dataSource ="dataSource1" animationDuration = 0 ></e-markerSetting>
                            <e-markerSetting visible= true :template='contentTemplate2' :dataSource ="dataSource2" animationDuration = 0 ></e-markerSetting>
                        </e-markerSettings>
                    </e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Marker } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        shapeData: world_map,
        dataSource: [
          { latitude: 49.95121990866204, longitude: 18.468749999999998 }
       ],
      dataSource1: [
          { latitude: 59.88893689676585, longitude: -109.3359375 }
      ],
       dataSource2: [
         { latitude: -6.64607562172573, longitude: -55.54687499999999 }
       ],
       contentTemplate: function () {
          return {
          template: Vue.component('MapsComponent', {
            template: '<div id="marker4" style="color:red" class="markerTemplate">Europe</div>',
            data() { return {  }; }
          })
        }
      },
      contentTemplate1: function () {
          return {
          template: Vue.component('MapsComponent', {
            template: '<div id="marker5" class="markerTemplate" style="width:50px;color:blue">NorthAmerica</div>',
            data() { return {  }; }
          })
        }
      },
      contentTemplate2: function () {
          return {
          template: Vue.component('MapsComponent', {
            template: '<div id="marker6" class="markerTemplate" style="width:50px;color:green">South America </div>',
            data() { return {  }; }
          })
        }
      },
    }
},
provide: {
    maps: [ Marker]
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

## Adding marker objects to map

The n number of markers can be added to shape layers with `markerSettings.dataSource` property. Each dataSource object contains the following list of properties.

* label - Text that displays some information about the annotation in text format.
* latitude - Latitude point determine the Y-axis position of annotation.
* longitude - Longitude point determine the X-axis position of annotation.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData'>
                        <e-markerSettings>
                            <e-markerSetting visible=true :dataSource="dataSource"
                            shape="Circle">
                            <e-markerSetting visible= true :template='contentTemplate' :dataSource ="dataSource1" animationDuration = 0 ></e-markerSetting>
                            <e-markerSetting visible= true :template='contentTemplate1' :dataSource ="dataSource2" animationDuration = 0 ></e-markerSetting>
                            <e-markerSetting visible= true :template='contentTemplate2' :dataSource ="dataSource3" animationDuration = 0 ></e-markerSetting>
                        </e-markerSettings>
                    </e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Marker } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
      shapeData: world_map,
        dataSource: [
        { latitude: 37.6276571, longitude: -122.4276688, name: 'San Bruno' },
        { latitude: 33.5302186, longitude: -117.7418381, name: 'Laguna Niguel' },
        { latitude: 40.7424509, longitude: -74.0081468, name: 'New York' }
       ],
       dataSource1: [
          { latitude: 49.95121990866204, longitude: 18.468749999999998 }
       ],
      dataSource2: [
          { latitude: 59.88893689676585, longitude: -109.3359375 }
      ],
       dataSource3: [
         { latitude: -6.64607562172573, longitude: -55.54687499999999 }
       ],

       contentTemplate: function () {
          return {
          template: Vue.component('MapsComponent', {
            template: '<div id="marker4" class="markerTemplate">Europe</div>',
            data() { return {  }; }
          })
        }
      },
      contentTemplate1: function () {
          return {
          template: Vue.component('MapsComponent', {
            template: '<div id="marker5" class="markerTemplate" style="width:50px">NorthAmerica</div>',
            data() { return {  }; }
          })
        }
      },
      contentTemplate2: function () {
          return {
          template: Vue.component('MapsComponent', {
            template: '<div id="marker6" class="markerTemplate" style="width:50px">South America </div>',
            data() { return {  }; }
          })
        }
      },
    }
},
provide: {
    maps: [ Marker]
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

## Marker shapes

The Maps component contains the following marker shapes. You can select any shape using the `shape` property in `markerSettings`.

* Balloon
* Circle
* Cross
* Diamond
* Image
* Rectangle
* Start
* Triangle
* VerticalLine
* HorizontalLine

## Customize marker shapes from data source

### Bind different colors and shapes to the marker from data source

The location on the map is marked by different marker shapes using `shapeValuePath` property in `markerSettings`. Based on the field name in the data source bind the value to the `shapeValuePath` property. Also, you can customize the marker shape color by binding the color value field name in the data source to the `colorValuePath` property in `markerSettings`.

A default marker object is represented by `balloon` shape. You can set various shapes to the marker object by using `shape` property in `markerSettings`. Also, you can change the shapes of the marker from the datasource.

The following shapes are used for the marker object.
* Circle
* Rectangle
* Balloon
* Cross
* Polyline
* Diamond
* Star
* Triangle
* HorizontalLine
* VerticalLine
* pentagon

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' :markerSettings='markerSettings'></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Marker, } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
      shapeData: world_map,
        markerSettings: [
            {
                dataSource: [
                  { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe', color:'red', shape:'Triangle' },
                  { latitude: 59.88893689676585, longitude: -109.3359375, name:'North America',
                  color:'blue', shape:'Pentagon' },
                  { latitude: -6.64607562172573, longitude: -55.54687499999999, name:'South America',
                color:'green', shape:'InvertedTriangle' }
                ],
                visible: true,
                shapeValuePath:'shape',
                colorValuePath:'color',
            },
        ]
    }
},
provide: {
    maps: [Marker]
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

## Marker Zooming

The map is initially scaled to the center value based on the marker distance. This can be achieved by setting `shouldZoomInitially` property in `zoomSettings` as `true`.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :zoomSettings='zoomSettings' >
                <e-layers>
                    <e-layer :shapeData='shapeData'  :markerSettings='markerSettings'></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Marker, Zoom, MapsTooltip } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        zoomSettings: {
          enable: true,
          horizontalAlignment:'Near',
          shouldZoomInitially: true
        },
        shapeData: world_map,
        markerSettings: [
            {
                dataSource:  [
                  { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                  { latitude: 59.88893689676585, longitude: -109.3359375, name:'North America' },
                  { latitude: -6.64607562172573, longitude: -55.54687499999999, name:'South America'}
                ],
                visible: true
            },
        ]
    }
},
provide: {
    maps: [Marker, Zoom]
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

## Marker Cluster Expand

The cluster is formed by grouping an identical and non-identical marker from the surrounding area. By clicking on the cluster and setting `allowClusterExpand` property in `markerClusterSettings` as `true` to expand the identical markers. If you zoom in any of the locations of the cluster, the number on the cluster will decrease and the overlapping marker will be split into an individual marker on the map. When you zoom out, it will increase the marker count and then cluster it again.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps  :zoomSettings='zoomSettings' >
                <e-layers>
                    <e-layer :shapeData='shapeData' :markerClusterSettings='markerClusterSettings' :markerSettings='markerSettings'></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Marker, Zoom } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        zoomSettings: {
            enable: true,
            mouseWheelZoom : true,
        },
        shapeData: world_map,
        markerClusterSettings: {
            allowClustering: true,
            allowClusterExpand: true,
            shape: 'Circle',
            height: 40,
            width: 40,
            labelStyle : { color: 'white'},
        },
        markerSettings: [
            {
                dataSource:[
                  { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                  { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                  { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                  { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                  { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                  { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                  { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' }
                  { latitude: 59.88893689676585, longitude: -109.3359375, name:'North America' },
                  { latitude: -6.64607562172573, longitude: -55.54687499999999, name:'South America'}
                ] ,
                visible: true
            },
        ]
    }
},
provide: {
    maps: [Marker, Zoom ]
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

## Enable the Legend for map markers

Legend can be enabled for marker using `legendSettings.type` as **Markers** and legend visible as true, need to inject Legend module to Maps using the `provide` option. Refer the code snippet to enable the legend for the markers.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :legendSettings='legendSettings' >
                <e-layers>
                    <e-layer :shapeData='shapeData' :markerSettings='markerSettings' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Marker, Legend } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        legendSettings: {
            visible: true,
            type: 'Markers'
        },
        shapeData: world_map,
          markerSettings: [
                    {
                        visible: true,
                        legendText: 'name',
                        dataSource: [
                            { latitude: 37.6276571, longitude: -122.4276688, name: 'San Bruno' },
                            { latitude: 33.5302186, longitude: -117.7418381, name: 'Laguna Niguel' },
                            { latitude: 40.7424509, longitude: -74.0081468, name: 'New York' }
                        ],
                        shape: 'Circle'
                    },
        ]
    }
},
provide: {
    maps: [Legend, Marker]
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

## Marker Clustering

Maps provides support to hide and cluster marker when they overlap each other. The number on a cluster indicates how many overlapped markers it contains. If you zoom any of the cluster locations, the number on the cluster will decrease and you will begin to see the individual markers on the map. When zooming out, the overlapping marker will increase so that you can cluster it again and increase the count over the cluster.

Using the `markerClusterSettings.allowClustering` API, you can enable or disable this cluster support. The `markerClusterSettings` API also helps to customize clusters.

The `MarkerClusterRendering` event occurs when each cluster is rendered. You can also use this to customize the cluster. The `markerClusterClick` and `markerClusterMouseMove` events on mouse move and on clicking the cluster.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps  :titleSettings='titleSettings' :zoomSettings='zoomSettings'  :useGroupingSeparator='useGroupingSeparator' format='n'>
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapeSettings='shapeSettings' :markerClusterSettings='markerClusterSettings' :markerSettings='markerSettings'></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Marker, Zoom, MapsTooltip } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
import { cluster } from './marker-cluster.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        useGroupingSeparator: true,
        zoomSettings: {
            enable: true,
        },
        shapeData: world_map,
        shapeSettings: {
            fill: '#C1DFF5'
        },
        titleSettings: {
            text: 'Top 13 largest cities in the World',
            textStyle: {
                size: '16px'
            }
        },
        markerClusterSettings: {
             allowClustering: true,
             shape: 'Circle',
             height: 40,
             width: 40,
             labelStyle : { color: 'white'},
        },
        markerSettings: [
            {
                dataSource: cluster,
                visible: true,
                shape: 'Balloon',
                height:20,
                width:20,
                animationDuration:0,
                tooltipSettings: {
                    visible: true,
                    valuePath: 'area',
                }
            },
        ]
    }
},
provide: {
    maps: [Marker, Zoom, MapsTooltip]
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
