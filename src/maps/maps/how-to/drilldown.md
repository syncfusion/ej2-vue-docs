# Drill-down

By clicking a continent, all the countries available in that continent can be viewed using the drill-down feature. For example, the countries in the `Africa` continent have been showcased here. To showcase all the countries in `Africa` continent by clicking the [`shapeSelected`](../api/maps#shapeselected) event as mentioned in the following example.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <div class='wrapper'>
            <ejs-maps  ref="maps" :layers='layers' :shapeSelected='shapeSelected'>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Marker } from '@syncfusion/ej2-vue-maps';
import { default_data } from './default-data.js';
import { world_map } from './world-map.js';
import { africa } from './africa.js';
Vue.use(MapsPlugin);
export default {
data () {
    return {
        layers: [
        {
            layerType: 'Geometry',
            shapeData: world_map,
            shapePropertyPath: 'continent',
            shapeDataPath: 'continent',
            dataSource:default_data,
            shapeSettings: {
                colorValuePath: 'drillColor'
            },
            markerSettings: [{
                visible: true,
                template: '<div id="marker3" class="markerTemplate">Africa' +
                    '</div>',
                dataSource: [
                    { latitude: 10.97274101999902, longitude: 16.390625 }
                ],
                animationDuration: 0
            }]
        },
        {
            layerType: 'Geometry',
            shapeData: africa,
            shapeSettings: {
                fill: '#80306A'
            },
            highlightSettings: {
                enable: true,
                fill: '#80306A'
            }
        }]
    }
},
provide: {
    maps: [Marker]
},
methods: {
    shapeSelected: function(args){
        let shape = (args.shapeData).continent;
        if (shape === 'Africa') {
            this.$refs.maps.ej2Instances.baseLayerIndex = 1;
            this.$refs.maps.ej2Instances.refresh();
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