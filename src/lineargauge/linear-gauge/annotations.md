---
title: "Annotations"
component: "LinearGauge"
description: "Annotations support in linear gauge"
---

# Annotations

<!-- markdownlint-disable MD013 -->

Annotations are used to mark the specific area of interest in the gauge area with texts, shapes or images. You can add any number of annotations to the gauge.

## Annotation

By using the [`content`](../api/linear-gauge/annotation/#content-string) property of [`annotation`](../api/linear-gauge/annotation/) object, you can either specify the id of the element or specify the code to create a new element, that needs to be displayed in the gauge area.

<!-- markdownlint-disable MD036 -->

```typescript

<template>
   <div class="control-section">
         <div align='center'>
            <ejs-lineargauge ref='lineargauge' style='display:block' align='center'>
                <e-annotations>
                    <e-annotation :content='contentTemplate' :zIndex='zindex'
                        x=100
                        y=100>
                    </e-annotation>
                </e-annotations>
            </ejs-lineargauge>
         </div>
</div>
</template>
<style>
  #control-container {
        padding: 0px !important;
    }
</style>
<script>
import Vue from "vue";
import { LinearGaugePlugin, Annotations } from "@syncfusion/ej2-vue-lineargauge";
Vue.use(LinearGaugePlugin);
var contentVue = Vue.component("contentTemplate", {
  template: '<div id="first"><h1>Gauge</h1></div>',
  data() {
    return {
      data: {}
    };
  }
});
export default {
    data:function(){
    return{
        zindex: 1,
        contentTemplate : function() {
            return {template: contentVue};
        },
    }
},
 provide: {
    lineargauge: [Annotations]
},
};
</script>


```

## Annotation Customization

You can customize the annotation using following properties.

* [`zIndex`](../api/linear-gauge/annotation/#zindex-string) - When annotation overlaps with another element, you can use this property to bring annotation to the front or back.
* [`horizontalAlignment`](../api/linear-gauge/annotation#horizontalalignment-string) - To move annotation horizontally. Possible values are "Center", "Far", "Near", "None"
* [`verticalAlignment`](../api/linear-gauge/annotation#verticalalignment-string) - To move annotation vertically. Possible values are "Center", "Far", "Near", "None"
* [`x`](../api/linear-gauge/annotation/#x-number) and [`y`](../api/linear-gauge/annotation/#y-number) - To move annotation to the specified location.

### Changing the z-order

You can change the z-order of the annotation element by using the [`zIndex`](../api/linear-gauge/annotation/#zindex-string) property.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
   <div class="control-section">
         <div align='center'>
             <ejs-lineargauge style='display:block' align='center'>
                <e-annotations>
                  <e-annotation :content='contentTemplate' :zIndex='zindex'
                  horizontalAlignment='Center'
                  verticalAlignment='Center'>
                  </e-annotation>
                </e-annotations>
             </ejs-lineargauge>
         </div>
  </div>
</template>
<script>
import Vue from "vue";
import { LinearGaugePlugin, Annotations } from "@syncfusion/ej2-vue-lineargauge";
Vue.use(LinearGaugePlugin);
var contentVue = Vue.component("contentTemplate", {
  template: '<div id="first"><h1>Gauge</h1></div>',
  data() {
    return {
      data: {}
    };
  }
});
export default {
    data:function(){
    return{
        zindex: 1,
        contentTemplate : function() {
          return {template: contentVue};
        },
    }
},
 provide: {
    lineargauge: [Annotations]
},
};
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}

### Positioning the Annotation

You can place the annotation anywhere in gauge area by specifying pixel values to the [`x`](../api/linear-gauge/annotation/#x-number) and [`y`](../api/linear-gauge/annotation/#y-number) properties.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
   <div class="control-section">
         <div align='center'>
             <ejs-lineargauge style='display:block' align='center'>
                <e-annotations>
                  <e-annotation :content='contentTemplate' :zIndex='zindex'
                  x=100 y=100>
                  </e-annotation>
                </e-annotations>
             </ejs-lineargauge>
         </div>
</div>
</template>
<script>
import Vue from "vue";
import { LinearGaugePlugin, Annotations } from "@syncfusion/ej2-vue-lineargauge";
Vue.use(LinearGaugePlugin);
var contentVue = Vue.component("contentTemplate", {
  template: '<div id="first"><h1>Gauge</h1></div>',
  data() {
    return {
      data: {}
    };
  }
});
export default {
    data:function(){
    return{
        zindex: 1,
        contentTemplate : function() {
          return {template: contentVue};
        },
    }
},
 provide: {
    lineargauge: [Annotations]
},
};
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>

```

{% endtab %}

<!-- markdownlint-disable MD036 -->

### Alignment of Annotation

You can align the annotation using [`horizontalAlignment`](../api/linear-gauge/annotation/#horizontalalignment-string) and [`verticalAlignment`](../api/linear-gauge/annotation/#verticalalignment-string) properties.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
   <div class="control-section">
         <div align='center'>
             <ejs-lineargauge style='display:block' align='center'>
                <e-annotations>
                  <e-annotation :content='contentTemplate' :zIndex='zindex'
                  horizontalAlignment='Center'
                  verticalAlignment='Center'>
                  </e-annotation>
                </e-annotations>
             </ejs-lineargauge>
         </div>
</div>
</template>
<script>
import Vue from "vue";
import { LinearGaugePlugin, Annotations } from "@syncfusion/ej2-vue-lineargauge";
Vue.use(LinearGaugePlugin);
var contentVue = Vue.component("contentTemplate", {
  template: '<div id="first"><h1>Gauge</h1></div>',
  data() {
    return {
      data: {}
    };
  }
});
export default {
    data:function(){
    return{
        zindex: 1,
        contentTemplate : function() {
          return {template: contentVue};
        },
    }
},
 provide: {
    lineargauge: [Annotations]
},
};
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>

```

{% endtab %}

## Multiple Annotations

You can add multiple annotations to the gauge as demonstrated below.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div class="control-section">
         <div align='center'>
             <ejs-lineargauge style='display:block' align='center'>
                <e-annotations>
                  <e-annotation :content='contentTemplate' :zIndex='zindex'
                    horizontalAlignment='Near'
                    verticalAlignment='Center' :x='x1' :y='y1'>
                  </e-annotation>
                  <e-annotation :content='contentTemplate1' :zIndex='zindex'
                    horizontalAlignment='Center'
                    verticalAlignment='Center' :x='x2' :y='y2'>
                  </e-annotation>
                </e-annotations>
             </ejs-lineargauge>
         </div>
</div>
</template>
<script>
import Vue from "vue";
import { LinearGaugePlugin, Annotations } from "@syncfusion/ej2-vue-lineargauge";
Vue.use(LinearGaugePlugin);
var contentVue = Vue.component("contentTemplate", {
  template: '<div id="first"><h1 style="color:red;">Speed</h1></div>',
  data() {
    return {
      data: {}
    };
  }
});
var contentVue1 = Vue.component("contentTemplate1", {
  template: '<div id="first"><h1 style="color:blue;">Meter</h1></div>',
  data() {
    return {
      data: {}
    };
  }
});
export default {
    data:function(){
    return{
       zindex: 1,
       x1:100,
       y1:150,
       x2:-100,
       y2:-100,
       contentTemplate : function() {
          return {template: contentVue};
        },
        contentTemplate1 : function() {
          return {template: contentVue1};
        },
    }
},
 provide: {
    lineargauge: [Annotations]
},
};
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>


```

{% endtab %}
