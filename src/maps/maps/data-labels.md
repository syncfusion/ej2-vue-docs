---
title: "DataLabels"
component: "Maps"
description: "DataLabel support in maps"
---

# Data labels

Data labels provide information to the user about the shapes.

## Add data labels

You can add label text to the shapes of the Maps component using `dataLabelSettings`. The following sample demonstrates the names of all the states n the United States in data labels.

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
    return{
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

> The `autofill` property is used in `shapeSettings` to apply the default palette colors to the shapes.

Some data labels intersect with other labels in this output. The following options are used to avoid intersecting:

## Smart labels

This provides an option to specify the smart labels when the labels intersect with the corresponding shape border. In `SmartLabelMode` property, you can specify any of the following options.

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
    return{
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

This specifies the intersect action when the labels intersect with another labels. In `IntersectionAction` property, you can specify any of the following options.

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
    return{
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

## Data label Template

The template supports customizing labels of each layers using the [template] property.

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
  template: '<div>DataLabel Tempalte</div>',
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
    return{
        shapeData: usMap,
        shapeSettings: {
           autofill:true
        },
        dataLabelSettings: {
            visible: true,
            labelPath: 'name',
            template:contentTemplate
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