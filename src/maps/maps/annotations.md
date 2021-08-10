---
title: " Annotations in Vue Maps control | Syncfusion "

component: "Maps"

description: "Learn here all about Annotations feature of Syncfusion Vue Maps control and more."
---

# Annotations in Vue Maps

Annotations are used to mark the specific area of interest in the Maps with texts, shapes, or images. Any number of annotations can be added to the Maps control.

## Annotation

By using the [`content`](../api/maps/annotationModel/#content) property of [`e-maps-annotation`](../api/maps/annotationModel/), text content or id of an element or an HTML string can be specified to render a new HTML element in Maps.

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

## Annotation customization

### Changing the z-index

The stack order of an annotation element can be changed using the [`zIndex`](../api/maps/annotationModel/#zindex) property in the [`e-maps-annotation`](../api/maps/annotationModel/) property.

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

### Positioning an annotation

Annotations can be placed anywhere in the Maps by specifying pixel or percentage values to the [`x`](../api/maps/annotationModel/#x) and [`y`](../api/maps/annotationModel/#y) properties in the [`e-maps-annotation`](../api/maps/annotationModel/) property.

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

### Alignment of an annotation

Annotations can be aligned using the [`horizontalAlignment`](../api/maps/annotationModel/#horizontalalignment) and [`verticalAlignment`](../api/maps/annotationModel/#verticalalignment) properties in the [`e-maps-annotation`](../api/maps/annotationModel/) property. The possible values can be "**Center**", "**Far**", "**Near**" and "**None**".

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

## Multiple Annotation

Multiple annotations can be added to the Maps by adding multiple [`e-maps-annotation`](../api/maps/annotationModel/) in the [`e-maps-annotation`](../api/maps/#annotations) and customization for the annotations can be done with the [`e-maps-annotation`](../api/maps/annotationModel/).

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps >
                <e-maps-annotations>
                  <e-maps-annotation :content='contentTemplate' :x='x1' :y='y1' :zIndex='zindex'>
                  </e-maps-annotation>
                   <e-maps-annotation :content='contentTemplate1' :x='x2' :y='y2' :zIndex='zindex1'>
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
       x1:'50%',
       y1:'0%',
       zindex1:1,
       x2: '20%',
       y2: '50%',
       contentTemplate: function () {
          return {
          template: Vue.component('MapsComponent', {
            template: '<div id="first"><h1>Maps</h1></div>',
            data() { return {  }; }
          })
        }
      },
      contentTemplate1: function () {
          return {
          template: Vue.component('MapsComponent', {
            template: '<div id="first"><h1>Multiple-annotation</h1></div>',
            data() { return {  }; }
          })
        }
      }
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