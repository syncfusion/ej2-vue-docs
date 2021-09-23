# Display geometry shape in bing maps

Usually bing map displays the Maps in satellite view in which you can't make changes as per your requirement. To over come this, you can add maps shape as sublayer over the bing map and you can customize it as per your requirement. Kindly follow the below steps to add geometry shapes as sublayer in bing maps.

**Step 1**:

To render the Maps control as bing map, set the [`layerType`](../api/maps/layerSettingsModel/#layertype) as **Bing** and also provide the key for the bing map.

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :layers='layers'>
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
      layers: [
        {
            layerType: 'Bing',
            // Provide your bing map key here
            key: '// ...bingMapKey'
        }
    ]
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

**Step 2**:

The geometry shape can be added in the bing map using sublayer concept. In the below example, Africa continent can be set as the sublayer in bing map using the [`type`](../api/maps/layerSettingsModel/#type) property.

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :layers='layers'>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin,} from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
import { africa } from './africa.js';
Vue.use(MapsPlugin);
export default {
data () {
    return {
        layers: [{
            layerType: 'Bing',
            key: '// ...bingMapKey'
        },
        {
            layerType: 'Geometry',
            type: 'SubLayer',
            shapeData: africa,
            shapeSettings: {
                fill: 'blue'
            }
        }
    ]
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