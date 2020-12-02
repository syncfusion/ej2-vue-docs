# State Persistence

## State Persistence

State persistence allows the Maps to retain the current modal value in the browser cookies for state maintenance. This action is handled through the `enablePersistence` property which is set to false by default. When it is set to true, some of the Maps component model values will be retained even after refreshing the page.

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :zoomSettings='zoomSettings' enablePersistence='enablePersistence' >
                <e-layers>
                    <e-layer :shapeData='shapeData' ></e-layer>
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
    return{
        enablePersistence: true,
        zoomSettings: {
            enable: true,
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