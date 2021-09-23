# Custom path map

Maps control can be customized as the desired layout using the custom path map feature. Here, the Maps control has been showcased with normal geometry type shapes to represent the bus seat selection layout.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <div class='wrapper'>
        <div style="border: 3px solid darkgray; width: 200; display; 'block'; margin: auto;">
            <ejs-maps :height='height'>
                <e-layers>
                    <e-layer :shapeData='shapeData' :geometryType='geometryType'>
                    </e-layer>
                </e-layers>
            </ejs-maps>
            </div>
      </div>
</div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, MapsComponent } from '@syncfusion/ej2-vue-maps';
import { seat } from './seat.js';
Vue.use(MapsPlugin);
export default {
data () {
    return {
      geometryType: 'Normal',
      shapeData: seat,
      height: '400'
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