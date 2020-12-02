---
title: "Legend"
component: "Maps"
description: "Legend support in maps"
---

# Legend

A legend is a key used on a map that contains swatches of symbols with descriptions. It provides valuable information for interpreting what the map is displaying and can be represented in various colors, shapes or other identifiers based on the data. It gives a breakdown of what each symbol represents throughout the map.

## Visibility

The Legends can be made visible by setting the visible property of legendSettings to true.

## Positioning of the Legend

The legend can be positioned in two ways.

* Absolute Position.

* Dock Position.

### Absolute Position

Based on the margin values of X and Y-axes, the Map legends can be positioned with the support of `location.x` and `location.y` properties available in legendSettings. For positioning the legend based on margins corresponding to a map, position value is set as ‘Float’.

### Dock Position

The map legends can be positioned in following locations within the container.
You can set this option by using `position` property in legendSettings.

    1 Top

    2 Left

    3 Bottom

    4 Right

above four positions can be aligned combination of 'Near', 'Center' and 'Far' using `alignment` in `legendSettings`. So legend can be aligned 12 positions.

## Legend Mode

Legend had two type of mode. `Default` mode and `Interactive` mode.

### Default Mode

Default mode legends having symbols with legend labels, used to identify the shape or bubble or marker color.

### Interactive Mode

The legends can be made interactive with an arrow mark indicating the exact range color in the legend when the mouse hovers over the corresponding shapes. You can enable this option by setting `mode` property in legendSettings value as “Interactive” and default value of `mode` property is “Default” to enable the normal legend.

## Legend Size

The map legend size can be modified by using the `height` and `width` properties in `legendSettings`.

## Legend for Shapes

The Layer shape type legends can be generated for each color mappings in shape settings.
**Note:** Below code snippet demonstrate the equal color mapping legends for the shapes.

Provide the `shapePropertyPath` value as 'name' and `shapeDataPath` value as 'Country'.

To enable the equal color mapping refer the `shapeSettings.colorMapping` code snippet.

Finally set `legendSettings.visible` as true and Inject the Legend Module into Maps using
`provide` option.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :legendSettings='legendSettings' >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapePropertyPath='shapePropertyPath' :shapeDataPath='shapeDataPath' :dataSource='dataSource' :shapeSettings='shapeSettings' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Legend } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        legendSettings: {
            visible: true
        },
        shapeData: world_map,
            dataSource: [{  "Country": "China", "Membership": "Permanent"},
            {"Country": "France","Membership": "Permanent" },
            { "Country": "Russia","Membership": "Permanent"},
            {"Country": "Kazakhstan","Membership": "Non-Permanent"},
            { "Country": "Poland","Membership": "Non-Permanent"},
            {"Country": "Sweden","Membership": "Non-Permanent"}],
            shapePropertyPath: 'name',
            shapeDataPath: 'Country'
            shapeSettings: {
                colorValuePath: 'Membership',
                colorMapping: [
                {
                    value: 'Permanent', color: '#D84444'
                },
                {
                    value: 'Non-Permanent', color: '#316DB5'
                }]
            }
    }
},
provide: {
    maps: [Legend]
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

## Legend Shape

To get the legend shape value for `legendSettings` by using `shape` property. You can customize the shape by using the `shapeWidth` and `shapeHeight` property.

## Legend for items excluded from color mapping

Based on the ranges in data source, get the excluded ranges from color mapping, and then show the legend with excluded range values are bound to the specific legend.

The following code example shows legends for the items excluded from color mapping.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :legendSettings='legendSettings'>
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapePropertyPath='shapePropertyPath' :shapeDataPath='shapeDataPath' :dataSource='dataSource' :shapeSettings='shapeSettings' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Legend } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
import { population_density } from './population-density.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        shapeData: world_map,
        legendSettings: {
            visible: true
        },
        shapeDataPath: 'name',
        shapePropertyPath: 'name',
        dataSource: population_density,
        shapeSettings: {
            colorValuePath: 'density',
            colorMapping: [
                {
                    from: 0, to: 100, color: ['red','blue']
                },
                {
                    from: 101, to: 200, color: ['green','yellow']
                },
                {
                    color: 'green'
                }
            ]
        }
    }
},
provide: {
    maps: [Legend]
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

## Hide desired legend items

To enable or disable the desired legend for each color mapping, set the `showLegend` property to `true` in `colorMapping`.

{% tab template= "maps/color-mapping", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :legendSettings='legendSettings'>
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapePropertyPath='shapePropertyPath' :shapeDataPath='shapeDataPath' :dataSource='dataSource' :shapeSettings='shapeSettings' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Legend } from '@syncfusion/ej2-vue-maps';
import { World_Map } from './worldmap.js';
import { default_data } from './legenddata.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        shapeData: World_Map,
        legendSettings: {
            visible: true
        },
        shapeDataPath: 'continent',
        shapePropertyPath: 'continent',
        dataSource: default_data,
        shapeSettings: {
            colorValuePath: 'color',
        }
    }
},
provide: {
    maps: [Legend]
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

## Hide legend items based data source value

To enable or disable the legend visibility for each item, bind the field name in the data source to the `showLegendPath` property in `legendSettings`.

The following code example shows how to hide the legend items based data source value.

{% tab template= "maps/color-mapping", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :legendSettings='legendSettings'>
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapePropertyPath='shapePropertyPath' :shapeDataPath='shapeDataPath' :dataSource='dataSource' :shapeSettings='shapeSettings' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Legend } from '@syncfusion/ej2-vue-maps';
import { World_Map } from './worldmap.js';
import { default_data } from './legenddata.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        shapeData: World_Map,
        legendSettings: {
            visible: true,
            showLegendPath:'visibility'
        },
        shapeDataPath: 'continent',
        shapePropertyPath: 'continent',
        dataSource: default_data,
        shapeSettings: {
            colorValuePath: 'color',
        }
    }
},
provide: {
    maps: [Legend]
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

## Bind legend item text from data source

To show the legend text based on binding, the field name in the datasource should be set to the `valuePath` property in `legendSettings`.

{% tab template= "maps/color-mapping", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :legendSettings='legendSettings'>
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapePropertyPath='shapePropertyPath' :shapeDataPath='shapeDataPath' :dataSource='dataSource' :shapeSettings='shapeSettings' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Legend } from '@syncfusion/ej2-vue-maps';
import { World_Map } from './worldmap.js';
import { default_data } from './legenddata.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        shapeData: World_Map,
        legendSettings: {
            visible: true,
            valuePath:'continent'
        },
        shapeDataPath: 'continent',
        shapePropertyPath: 'continent',
        dataSource: default_data,
        shapeSettings: {
            colorValuePath: 'color',
        }
    }
},
provide: {
    maps: [Legend]
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

## Hide duplicate legend items

To enable or disable the duplicate legend items, set the property `removeDuplicateLegend` property to `true` in `legendSettings`.

{% tab template= "maps/color-mapping", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :legendSettings='legendSettings'>
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapePropertyPath='shapePropertyPath' :shapeDataPath='shapeDataPath' :dataSource='dataSource' :shapeSettings='shapeSettings' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Legend } from '@syncfusion/ej2-vue-maps';
import { World_Map } from './worldmap.js';
import { default_data } from './legenddata.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        shapeData: World_Map,
        legendSettings: {
            visible: true,
            valuePath:'continent',
            removeDuplicateLegend: true
        },
        shapeDataPath: 'continent',
        shapePropertyPath: 'continent',
        dataSource: default_data,
        shapeSettings: {
            colorValuePath: 'color',
        }
    }
},
provide: {
    maps: [Legend]
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

## Toggle option in legend

The toggle option has been provided for legend. So, if you toggle a legend, the given color will be changed to the corresponding maps shape item. You can enable the toggle options using the `toggleLegendSettings` property.

The following options are available to customize the shape of the map:

* applyShapeSettings – Applies the fill property value in `shapeSettings` to a shape of the maps if it                         is true and a legend item is clicked.

* fill- Specifies the color to the shape of the maps.

* opacity – Specifies the transparency of the legend.

* border – Specifies the border color and width.

{% tab template= "maps/color-mapping", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps :legendSettings='legendSettings'>
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapePropertyPath='shapePropertyPath' :shapeDataPath='shapeDataPath' :dataSource='dataSource' :shapeSettings='shapeSettings' ></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Legend } from '@syncfusion/ej2-vue-maps';
import { World_Map } from './worldmap.js';
import { Population_Density } from './populationdensity.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        shapeData: World_Map,
        legendSettings: {
            visible: true,
            toggleLegendSettings: {
                enable: true,
                applyShapeSettings: false,
                border: {
                    color: "green",
                    width: 2
                }
            }
        },
        shapeDataPath: 'name',
        shapePropertyPath: 'name',
        dataSource: Population_Density,
        shapeSettings: {
            colorValuePath: 'density',
             colorMapping: [
                {
                    from: 0, to: 100, color: 'rgb(153,174,214)',
                },
                {
                    from: 101, to: 200, color: 'rgb(115,143,199)',
                },
                {
                    color: 'rgb(77,112,184)'
                },
            ]
        }
    }
},
provide: {
    maps: [Legend]
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

Refer the [`API`](../api/maps/legendSettingsModel/) for Legend feature.