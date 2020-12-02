---
title: "Annototation"
component: "Maps"
description: "Annotation support in maps"
---

# Annotations

Annotations are used to mark the specific area of interest in the map area with texts, shapes, or images. You can add any number of annotations to the maps.

## Annotation

By using the `content` property of `annotation` object, you can either specify the id of an element or specify the code to create a new element that needs to be displayed in the gauge area.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-maps-annotations>
                  <e-maps-annotation :content='contentTemplate' :x='x1' :y='y1' :zIndex='zindex'>
                  </e-maps-annotation>
                </e-maps-annotations>
                <e-layers>
                    <e-layer :shapeData='shapeData' >
                    </e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, MapsComponent, Annotations } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
       shapeData: world_map,
       zindex:1,
       x1:'0%',
       y1:'50%',
       contentTemplate: function () {
          return {
          template: Vue.component('MapsComponent', {
            template: '<div id="first"><h1>Maps</h1></div>',
            data() { return {  }; }
          })
        }
      },
    }
},
provide: {
    maps: [ Annotations ]
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

## Annotation Customization

### Changing the z-order

You can change the z-order of an annotation element using the `zIndex` property.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-maps-annotations>
                  <e-maps-annotation :content='contentTemplate' :x='x1' :y='y1' :zIndex='zindex'>
                  </e-maps-annotation>
                </e-maps-annotations>
                <e-layers>
                    <e-layer :shapeData='shapeData' >
                    </e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, MapsComponent, Annotations } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
       shapeData: world_map,
       zindex:1,
       x1:'0%',
       y1:'50%',
       contentTemplate: function () {
          return {
          template: Vue.component('MapsComponent', {
            template: '<div id="first"><h1>Maps</h1></div>',
            data() { return {  }; }
          })
        }
      },
    }
},
provide: {
    maps: [ Annotations ]
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

### Positioning of Annotation

You can place an annotation anywhere in gauge area by specifying pixel values to the `x` and `y` properties.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-maps-annotations>
                  <e-maps-annotation :content='contentTemplate' :x='x1' :y='y1' :zIndex='zindex'>
                  </e-maps-annotation>
                </e-maps-annotations>
                <e-layers>
                    <e-layer :shapeData='shapeData' >
                    </e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, MapsComponent, Annotations } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
       shapeData: world_map,
       zindex:1,
       x1:'20%',
       y1:'50%',
       contentTemplate: function () {
          return {
          template: Vue.component('MapsComponent', {
            template: '<div id="first"><h1>Maps</h1></div>',
            data() { return {  }; }
          })
        }
      },
    }
},
provide: {
    maps: [ Annotations ]
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

### Alignment of Annotation

You can align annotations using the `horizontalAlignment` and `verticalAlignment` properties.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-maps-annotations>
                  <e-maps-annotation :content='contentTemplate' :x='x1' :y='y1' :zIndex='zindex'
                  horizontalAlignment='Center' verticalAlignment='Center'>
                  </e-maps-annotation>
                </e-maps-annotations>
                <e-layers>
                    <e-layer :shapeData='shapeData' >
                    </e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, MapsComponent, Annotations } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use(MapsPlugin);
export default {
data () {
    return{
       shapeData: world_map,
       zindex:1,
       x1:'20%',
       y1:'50%',
       contentTemplate: function () {
          return {
          template: Vue.component('MapsComponent', {
            template: '<div id="first"><h1>Maps</h1></div>',
            data() { return {  }; }
          })
        }
      },
    }
},
provide: {
    maps: [ Annotations ]
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
