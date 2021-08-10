# Adding multiple layers in the Map

The multilayer support allows loading multiple shape files in a single container and enables Maps to display more information. The shape layer is the main layer of the Maps. Multiple layers can be added in a shape layer as **SubLayer** using the [`type`](../api/maps/type/) property.

{% tab template= "maps/getting-started", isDefaultActive=true %}

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
import { MapsPlugin } from '@syncfusion/ej2-vue-maps';
import { usMap } from './usa.js';
import { texas } from './texas.js';
import { california } from './california.js';
Vue.use(MapsPlugin);
export default {
data () {
    return {
       layers: [{
            shapeData: usa,
            shapeSettings: {
                fill: '#E5E5E5',
                border: {
                    color: 'black',
                    width: 0.1
                }
            }
        },
        {
            shapeData: texas,
            type: 'SubLayer',
            shapeSettings: {
                fill: 'rgba(141, 206, 255, 0.6)',
                border: {
                    color: '#1a9cff',
                    width: 0.25
                }
            }
        },
        {
            shapeData: california,
            type: 'SubLayer',
            shapeSettings: {
                fill: 'rgba(141, 206, 255, 0.6)',
                border: {
                    color: '#1a9cff',
                    width: 0.25
                }
            }
        }
    ]}
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