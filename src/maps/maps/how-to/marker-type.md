# Markers

## Add different types of markers

Different marker objects can be added to the Maps component using the marker settings. To update different marker settings in Maps, please follow the given steps:

**Step 1**:

Initialize the Maps control with marker settings. Here, a marker has been added with specified latitude and longitude of California by using the [`dataSource`](../api/maps/markerSettingsModel/#datasource) property. To customize the shape of the marker using the [`shape`](../api/maps/markerSettingsModel/#shape) property and change the border color and width of the marker using the [`border`](../api/maps/markerSettingsModel/#border) property as mentioned in the following example.

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
    return {
        shapeData: world_map,
        markerSettings: [{
        dataSource: [
            { latitude: 40.7424509, longitude: -74.0081468, city: 'New York' }],
        visible:true,
        shape: 'Circle',
        fill: 'white',
        width: 3,
        animationDuration:0,
            border: { width: 2, color: '#333' }
        }]
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

**Step 2**:

Customize the above option for n number of markers as mentioned in the following example.

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
    return {
        shapeData: world_map,
        markerSettings: [{
            dataSource: [
                { latitude: 37.6276571, longitude: -122.4276688, city: 'San Bruno' },
            ],
            visible:true,
            shape:'Circle',
            fill:'white',
            width:3,
            animationDuration:0,
            border:{ width: 2, color: '#333'}
        },
        {
            dataSource: [
                { latitude: 33.5302186, longitude: -117.7418381, city: 'Laguna Niguel' },
            ],
            visible:true,
            shape:'Rectangle',
            fill:'yellow',
            width:15,
            height:4,
            animationDuration:0,
            border: { width: 2, color: '#333' }
        },
        {
            dataSource: [
                { latitude: 40.7424509, longitude: -74.0081468, city: 'New York' }
            ],
            visible:true,
            shape:'Diamond',
            fill:'white',
            width:10,
            height:10,
            animationDuration:0,
            border: { width: 2, color: 'blue' }
        }]
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