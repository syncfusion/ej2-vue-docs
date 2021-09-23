---
title: "Data Labels in Vue Maps control | Syncfusion"

component: "Maps"

description: "Learn here all about Data Labels of Syncfusion Vue Maps control and more."
---

# Data labels in Vue Maps control

Data labels provide information to users about the shapes of the Maps component. It can be enabled by setting the [`visible`](../api/maps/dataLabelSettingsModel/#visible) property of the [`dataLabelSettings`](../api/maps/dataLabelSettingsModel/) to **true**.

## Adding data labels

To display data labels in the Maps, the [`labelPath`](../api/maps/dataLabelSettingsModel/#labelpath) property of [`dataLabelSettings`](../api/maps/dataLabelSettingsModel/) must be used. The value of the [`labelPath`](../api/maps/dataLabelSettingsModel/#labelpath) property can be taken from the field name in the shape data or data source. In the following example, the value of the [`labelPath`](../api/maps/dataLabelSettingsModel/#labelpath) property is the field name in the shape data of the Maps layer.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapeSettings='shapeSettings'
                    :dataLabelSettings='dataLabelSettings'></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, DataLabel } from '@syncfusion/ej2-vue-maps';
import { usMap } from './usa.js';
Vue.use(MapsPlugin);
export default {
data () {
    return {
        shapeData: usMap,
        shapeSettings: {
           autofill:true
        },
        dataLabelSettings: {
            visible: true,
            labelPath: 'name'
        }
    }
},
provide: {
    maps: [DataLabel]
},
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

In the following example, the value of [`labelPath`](../api/maps/dataLabelSettingsModel/#labelpath) property is set from the field name in the data source of the layer settings.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapeSettings='shapeSettings'
                    :dataLabelSettings='dataLabelSettings'></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, DataLabel } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
        shapeData: world_map,
        shapePropertyPath: 'name',
        shapeDataPath: 'name',
        dataLabelSettings: {
            visible: true,
            labelPath: "continent",
            smartLabelMode: 'Trim'
        },
        dataSource: [
            {"name": "Afghanistan", "value": 53, "countryCode": "AF", "population": "29863010", "color": "red", "density": "119", "continent": "Asia"},
            {"name": "Albania", "value": 117, "countryCode": "AL", "population": "3195000", "color": "Blue", "density": "111", "continent": "Europe"},
            {"name": "Algeria", "value": 15, "countryCode": "DZ", "population": "34895000", "color": "Green", "density": "15", "continent": "Africa"}
        ],
        shapeSettings: {
            autofill: true
        }
    }
},
provide: {
    maps: [DataLabel]
},
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

## Customization

The following properties are available in the [`dataLabelSettings`](../api/maps/dataLabelSettingsModel/) to customize the data label of the Maps control.

* [`border`](../api/maps/dataLabelSettingsModel/#border) - To customize the color, width and opacity for the border of the data labels in Maps.
* [`fill`](../api/maps/dataLabelSettingsModel/#fill) - To apply the color of the data labels in Maps.
* [`opacity`](../api/maps/dataLabelSettingsModel/#opacity) - To customize the transparency of the data labels in Maps.
* [`textStyle`](../api/maps/dataLabelSettingsModel/#textstyle) - To customize the text style of the data labels in Maps.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapeSettings='shapeSettings'
                    :dataLabelSettings='dataLabelSettings'></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, DataLabel } from '@syncfusion/ej2-vue-maps';
import { usMap } from './usa.js';
Vue.use(MapsPlugin);
export default {
data () {
    return {
        shapeData: usMap,
        shapeSettings: {
           autofill:true
        },
        dataLabelSettings: {
            visible: true,
            labelPath: 'name',
            border: {
                color: 'green',
                width: 2
            },
            fill: 'red',
            opacity: 0.9,
            textStyle: {
                color: 'blue',
                size: '10px',
                fontStyle: 'Sans-serif',
                fontWeight: 'normal'
            }
        }
    }
},
provide: {
    maps: [DataLabel]
},
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

## Smart labels

The Maps control provides an option to handle the labels when they intersect with the corresponding shape borders using the [`smartLabelMode`](../api/maps/dataLabelSettingsModel/#smartlabelmode) property. The following options are available in the [`smartLabelMode`](../api/maps/dataLabelSettingsModel/#smartlabelmode) property.

* None
* Hide
* Trim

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapeSettings='shapeSettings'
                    :dataLabelSettings='dataLabelSettings'></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, DataLabel } from '@syncfusion/ej2-vue-maps';
import { usMap } from './usa.js';
Vue.use(MapsPlugin);
export default {
data () {
    return {
        shapeData: usMap,
        shapeSettings: {
           autofill:true
        },
        dataLabelSettings: {
            visible: true,
            labelPath: 'name',
            smartLabelMode:'Hide'
        }
    }
},
provide: {
    maps: [DataLabel]
},
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

## Intersect action

The Maps component provides an option to handle the labels when a label intersects with another label using the [`intersectionAction`](../api/maps/dataLabelSettingsModel/#intersectionaction) property. The following options are available in the [`intersectionAction`](../api/maps/dataLabelSettingsModel/#intersectionaction) property.

* None
* Hide
* Trim

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapeSettings='shapeSettings'
                    :dataLabelSettings='dataLabelSettings'></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, DataLabel } from '@syncfusion/ej2-vue-maps';
import { usMap } from './usa.js';
Vue.use(MapsPlugin);
export default {
data () {
    return {
        shapeData: usMap,
        shapeSettings: {
           autofill:true
        },
        dataLabelSettings: {
            visible: true,
            labelPath: 'name',
            intersectionAction:'Trim'
        }
    }
},
provide: {
    maps: [DataLabel]
},
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

## Adding data label as a template

The data label can be added as a template in the Maps component. The [`template`](../api/maps/dataLabelSettingsModel/#template) property of [`dataLabelSettings`](../api/maps/dataLabelSettings/) is used to set the data label as a template. Any text or HTML element can be added as the template in data labels.

>The customization properties of data label, [`smartLabelMode`](../api/maps/dataLabelSettingsModel/#smartlabelmode) and [`intersectionAction`](../api/maps/dataLabelSettingsModel/#intersectionaction) properties are not applicable to [`template`](../api/maps/dataLabelSettingsModel/#template) property. The styles can be applied to the label template using the CSS styles of the template element.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="template">
        <div class='wrapper'>
            <ejs-maps >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapeSettings='shapeSettings'
                    :dataLabelSettings='dataLabelSettings'></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, DataLabel } from '@syncfusion/ej2-vue-maps';
import { usMap } from './usa.js';

Vue.use(MapsPlugin);
let contentVue = Vue.component("contentTemplate", {
    template: '<div>Label</div>',
        data() {
            return {
                data: {}
            };
        }
});
let contentTemplate = function() {
    return { template: contentVue };
};
export default {
data () {
    return {
        shapeData: usMap,
        shapeSettings: {
           autofill:true
        },
        dataLabelSettings: {
            visible: true,
            labelPath: 'name',
            template: contentTemplate
        }
    }
},
provide: {
    maps: [DataLabel]
},
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