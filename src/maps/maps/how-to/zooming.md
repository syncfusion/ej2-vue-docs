# Center position zooming

The center position zooming can be achieved by using the [`centerPosition`](../api/maps#centerposition) and [`zoomFactor`](../api/maps/zoomSettingsModel/#zoomfactor) properties as mentioned in the following example. The center position is used to configure the zoom level of Maps, and the zoom factor is used to specify the center position where the Maps should be displayed.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :zoomSettings='zoomSettings' :centerPosition='centerPosition'>
                <e-layers>
                    <e-layer :shapeData='shapeData'></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Zoom } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return {
        zoomSettings: {
            enable: true,
            zoomFactor: 13
        },
        centerPosition: {
            latitude: 25.54244147012483,
            longitude: -89.62646484375
        },
        shapeData: world_map,
    }
},
provide: {
    maps: [Zoom]
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