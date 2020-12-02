---
title: "Customization"
component: "Maps"
description: "Expalains customization options available in maps"
---

# Customization

he following properties are available in `shapeSettings` property to customize the shapes of the Maps component.

* `fill` - Customizes the shape color.
* `autofill` - Applies the default palette colors to shapes.
* `palette` - Applies own custom palette for shapes.
* `border` - Customizes the maps shape border.
* `dashArray` - Customizes the different dash array border line format.
* `opacity` - Customizes the shape opacity.
{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="map">
        <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapeSettings='shapeSettings' :layerType='layerType' ></e-layer>
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
        layerType: 'Geometry',
        shapeData: world_map,
        shapeSettings: {
            fill: '#33CCFF',
            border: { color: '#FFFFFF', width: 2}
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

## AutoFill

To apply default palette colors for shapes need to enable the `autofill` property.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="map">
        <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapeSettings='shapeSettings' :layerType='layerType' ></e-layer>
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
        layerType: 'Geometry',
        shapeData: world_map,
        shapeSettings: {
            autofill: true
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

## Palette

you can apply own custom palette for shape, you need to provide the palette colors for `palette`.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="map">
        <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapeSettings='shapeSettings' :layerType='layerType' ></e-layer>
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
        layerType: 'Geometry',
        shapeData: world_map,
        shapeSettings: {
            autofill: true,
            palette: ['#33CCFF', '#FF0000', '#800000', '#FFFF00', '#808000']
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

## Projection Type

By default, the maps are rendered by Mercator projection type. In this type, the maps are rendered based on coordinates, so it is not stretched.

The maps control has the following projection types:

* Mercator
* Equirectangular
* Miller
* Eckert3
* Eckert5
* Eckert6
* Winkel3
* AitOff.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="map">
        <div class='wrapper'>
            <ejs-maps projectionType= 'Miller'>
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapeSettings='shapeSettings' :layerType='layerType' ></e-layer>
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
        layerType: 'Geometry',
        shapeData: world_map,
        shapeSettings: {
            autofill: true,
            palette: ['#33CCFF', '#FF0000', '#800000', '#FFFF00', '#808000']
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