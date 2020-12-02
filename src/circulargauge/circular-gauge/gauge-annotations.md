---
title: "Annotations"
component: "CircularGauge"
description: "Annotations support in circular gauge"
---

# Annotations

Annotations are used to mark a specific area of interest in the gauge with texts, shapes or images.

## Content

You can place any custom element on the axis area by assigning the id of the element to
[`content`](../api/circular-gauge/annotation/#content-string) property of [`annotation`](../api/circular-gauge/annotation/) object.

>Note: To use annotation feature, we need to inject `Annotations` module using `CircularGauge.Inject(Annotations)` method.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
      <div class='wrapper'>
             <ejs-circulargauge>
                <e-axes>
                    <e-axis :annotations='annotations'>  
                        <e-pointers>
                            <e-pointer value=50 ></e-pointer>
                        </e-pointers>
                    </e-axis>
                </e-axes>
             </ejs-circulargauge>
         </div>
</div>
</template>
<script>
import Vue from "vue";
import { CircularGaugePlugin, Annotations } from "@syncfusion/ej2-vue-circulargauge";

let contentVue = Vue.component("contentTemplate", {
  template: '<div><span style="font-size:10px; color:#424242; font-family:Regular">pointer Value: 50</span></div>',
  data() {
    return {
      data: {}
    };
  }
});
let contentTemplate = function() {
  return { template: contentVue };
};
Vue.use(CircularGaugePlugin);
export default {
    data:function(){
    return {
        annotations:[{
            content:contentTemplate,
            zIndex: '1'
        }]
    }
},
 provide: {
    circulargauge: [Annotations]
},
};
</script>
<style>
  .wrapper {
    max-width: 300px;
    margin: 0 auto;
  }
</style>

```

{% endtab %}

## Position

Annotation can be placed around the axis by using [`radius`](../api/circular-gauge/annotation/#radius-string)
and [`angle`](../api/circular-gauge/annotation/#angle-number) property.
For example, if the angle is 90 degree and the radius is 110%, then the annotation, will be placed at the right side of the axis.

Radius of the annotation takes value either in pixel or percentage. By setting value in percentage, annotation gets its position with respect to its axis radius.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
   <div id="app">
      <div class='wrapper'>
             <ejs-circulargauge>
                 <e-axes>
                    <e-axis :annotations='annotations'>  
                        <e-pointers>
                            <e-pointer value=50 ></e-pointer>
                        </e-pointers>
                    </e-axis>
                </e-axes>
             </ejs-circulargauge>
         </div>
</div>
</template>
<script>
import Vue from "vue";
import { CircularGaugePlugin, Annotations } from "@syncfusion/ej2-vue-circulargauge";
Vue.use(CircularGaugePlugin);

let contentVue = Vue.component("contentTemplate", {
  template: '<div><span style="font-size:10px; color:#424242; font-family:Regular">pointer Value: 50</span></div>',
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
    data:function(){
    return {
        annotations: [{
            content: contentTemplate,
            angle: 90,
            radius: '150%',
            zIndex: '1'
        }
        ]
    }
},
 provide: {
    circulargauge: [Annotations]
},
};
</script>
<style>
  .wrapper {
    max-width: 300px;
    margin: 0 auto;
  }
</style>

```

{% endtab %}

## Sub Gauge

As the annotation allows you to place any custom element, we can initialize a gauge to the element and can
be used to place that in another gauge.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
      <div class='wrapper'>
             <ejs-circulargauge :axes ='axes'>
             </ejs-circulargauge>

         </div>
</div>
</template>
<script>
import Vue from "vue";
import { CircularGaugePlugin, Annotations } from "@syncfusion/ej2-vue-circulargauge";
Vue.use(CircularGaugePlugin);
export default {
    data:function(){
    return {
          axes: [{
        minimum: 0,
        maximum: 12,
        startAngle: 0,
        endAngle: 360,
        lineStyle: { width: 0 },
        ranges: [
            {
                start: 0, end: 3,
                color: 'rgba(29,29,29,0.7)'
            }, {
                start: 3, end: 12,
                color: 'rgba(168,145,102,0.1)'
            }
        ],
        annotations: [{
            angle: 270,
            radius: '40%',
            content: '<div id="subGauge" style="width:90px;height:90px;"></div>'
        },{
            angle: 90,
            radius: '40%',
            content: '<div id="time"><span>6:30 PM</span></div>',
            zIndex: '1'
        }],
        labelStyle: {
            hiddenLabel: 'First'
        },
        pointers: [{
            pointerWidth: 5,
            radius: '40%',
            value: 6.5,
            color: 'rgb(29,29,29)',
            border: { width: 1, color: 'rgb(29,29,29)' },
            cap: {
                color: 'rgb(29,29,29)',
                radius: 0,
                border: {
                    width: 0.2,
                    color: 'red'
                }
            },
            needleTail: {
                length: '0%'
            }, animation: {
                enable: false
            }
        }, {
            radius: '60%',
            pointerWidth: 5,
            color: 'rgb(29,29,29)',
            border: {
                width: 1,
                color: 'rgb(29,29,29)'
            },
            value: 6,
            cap: {
                color: 'rgb(29,29,29)',
                radius: 0,
                border: {
                    width: 0.2,
                    color: 'red'
                }
            },
            needleTail: {
                length: '0%'
            }, animation: {
                enable: false
            }
        }, {
            radius: '70%',
            pointerWidth: 4,
            value: 9.8,
            color: 'rgba(168,145,102,1)',
            cap: {
                color: 'rgba(168,145,102,1)',
                radius: 4,
                border: {
                    width: 0.2,
                    color: 'rgba(168,145,102,1)'
                }
            },
            needleTail: {
                color: 'rgba(168,145,102,1)',
                length: '20%'
            }, animation: {
                enable: false,
                duration: 500
            }
        }]
    }]
    }
},
 provide: {
    circulargauge: [Annotations]
},
};

</script>
<style>
  .wrapper {
    max-width: 300px;
    margin: 0 auto;
  }
</style>

```

{% endtab %}

## See also

* [Tooltip for Annotation](https://ej2.syncfusion.com/documentation/circular-gauge/gauge-user-interaction/tooltip-for-ranges-and-annotations/)
