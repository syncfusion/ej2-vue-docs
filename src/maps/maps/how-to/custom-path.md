# Custom path map

Maps control can be customized as the desired layout using the custom path map feature. Here, the Maps control has been showcased with normal geometry type shapes to represent the bus seat selection layout. Please refer to the following example to render the bus seat selection.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <div class='wrapper'>
            <ejs-maps :height='height'>
                <e-layers>
                    <e-layer :shapeData='shapeData' :geometryType='geometryType'>
                    </e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    <div class="col-lg-9 control-section">
        <div style="width:200px;margin:auto;padding-bottom:20px">
          <img src="src//bus-icon.png" style="width:25px;height:25px;float:left">
          <div style="padding-left:30px;font-size:20px;font-weight:400;">Bus seat selection</div>
        </div>
    <div style="border: 3px solid darkgray;width:200px;display:block;margin:auto;border-radius:5px">
          <img src="src/wheel.png" style="width:30px;height:30px;margin-left:18%;margin-top:10px">
          <div id="maps"></div>
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