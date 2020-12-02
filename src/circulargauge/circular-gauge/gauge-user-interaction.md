---
title: "User Interaction"
component: "CircularGauge"
description: "Explains about user interactions in circular gauge"
---

# User Interaction

## Tooltip for pointer

Circular gauge will displays the pointer details through [tooltip](../api/circular-gauge/tooltipSettings/),
when the mouse is moved over the pointer.

<!-- markdownlint-disable MD036 -->

## Tooltip for ranges

Circular gauge displays the information about the ranges through tooltip when hovering the mouse over the ranges. You can enable this feature by setting the type property of tooltip to ‘Range’ in the array collection.

**Tooltip customization for ranges**

To customize the range tooltip, use the `rangeSettings` property in tooltip. The following options are available to customize the range tooltip:

* fill - Specifies the range tooltip fill color.

* textStyle - Specifies the range tooltip text style.

* format - Specifies the range content format.

* template - Specifies the custom template for tooltip.

* enableAnimation - Animates as it moves from one point to another.

* border - Specifies the tooltip border.

* showMouseAtPosition - Displays the position of the tooltip on the cursor position.

## Tooltip for annotation

Circular gauge displays the information about the annotations through tooltip when hovering the mouse over the annotation. You can enable this feature by setting the type property of tooltip to ‘Annotation’ in the array collection.

**Tooltip customization for annotation**

To customize the annotation tooltip, use the `annotationSettings` property in tooltip. The following options are available to customize the annotation tooltip:

* fill - Specifies the annotation tooltip fill color.

* textStyle - Specifies the annotation tooltip text style.

* format - Specifies the annotation content format.

* template - Specifies the tooltip content with custom template.

* enableAnimation - Animates as it moves from one point to another.

* border - Specifies the tooltip border.

The following code example shows the tooltip for the pointer, ranges and annotation.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
<div id="app">
      <div class='wrapper'>
        <ejs-circulargauge  style='display:block' align='center' id='tooltip-container'  :enablePointerDrag='enablePointerDrag' :tooltip='tooltip'>
            <e-axes>
                <e-axis :annotations='annotations' :radius='gaugeradius' :startAngle='startAngle' minimum=0 maximum=120 :endAngle='endAngle' :majorTicks='majorTicks' :lineStyle='lineStyle' :minorTicks='minorTicks' :labelStyle='labelStyle' :ranges='ranges'>
                    <e-pointers>
                        <e-pointer :value='value' :cap='cap' :radius='pointerRadius' :color='color' :animation='animation'></e-pointer>
                    </e-pointers>
                </e-axis>
            </e-axes>
        </ejs-circulargauge>
    </div>
</div>
</template>

<script>
import Vue from 'vue';
import {CircularGaugePlugin, GaugeTooltip, Annotations } from "@syncfusion/ej2-vue-circulargauge";
Vue.use(CircularGaugePlugin);
export default {
    data: function () {
        return {
            annotations: [{
                  content: 'CircularGauge', zIndex:'1', angle: 180
            }],
            gaugeradius: '90%',
            startAngle: 240,
            endAngle: 120,
            lineStyle: {
                width: 0
            },
            majorTicks: {
                color: 'white',
                offset: -5,
                height: 12
            },
            minorTicks: {
                width: 0
            },
            labelStyle: {
                useRangeColor: true,
                font: {
                    color: '#424242',
                    size: '13px',
                    fontFamily: 'Roboto'
                }
            },
            value: 70,
            pointerRadius: '60%',
            color: '#33BCBD',
            cap: {
                radius: 10,
                border: {
                    color: '#33BCBD',
                    width: 5
                }
            },
            animation: {
                enable: true,
                duration: 1500
            },
            ranges: [{
                start: 0,
                end: 50,
                startWidth: 10,
                endWidth: 10,
                radius: '102%',
                color: '#3A5DC8',
            }, {
                start: 50,
                end: 120,
                radius: '102%',
                startWidth: 10,
                endWidth: 10,
                color: '#33BCBD',
            }],
            tooltip: {
                type:['Pointer', 'Range', 'Annotation'],
                enable: true,
                enableAnimation: false,
                annotationSettings: { template:'<div>CircularGauge</div>' },
                rangeSettings: { fill:'red' }
            },
            enablePointerDrag: true
        }
    },
    provide: {
        circulargauge: [GaugeTooltip, Annotations]
    },
 };
</script>

<style>
  .wrapper {
    max-width: 300px;
    margin: 0 auto;
  }
#templateWrap img {
    border-radius: 30px;
    width: 30px;
    height: 30px;
    margin: 0 auto;
}

#templateWrap .des {
    float: right;
    padding-left: 10px;
    line-height: 30px;
}
</style>

```

{% endtab %}

<!-- markdownlint-disable MD036 -->

### Template

Any HTML elements can be displayed in the tooltip by using the
[`template`](../api/circular-gauge/tooltipSettings/#template-string) property of the tooltip.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div id="app">
      <div class='wrapper'>
    <ejs-circulargauge   :tooltip='tooltip' >
    <e-axes>
      <e-axis >
        <e-pointers>
           <e-pointer value=70 ></e-pointer>
    </e-pointers>
    </e-axis>
    </e-axes>
    </ejs-circulargauge>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin, GaugeTooltip } from "@syncfusion/ej2-vue-circulargauge";

let contentVue = Vue.component("contentTemplate", {
  template: '<div>Pointer: 70 </div>',
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
      data: function () {
          return{
            tooltip: {
               enable: true,
               template: contentTemplate
            }
          }
    },
     provide: {
       circulargauge: [ GaugeTooltip]
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

## Pointer Drag

Pointers can be dragged over the axis value. This can be achieved by clicking and dragging the pointer. To enable or disable the pointer drag, you can use
[`enablePointerDrag`](../api/circular-gauge/#enablepointerdrag-boolean) property.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div id="app">
      <div class='wrapper'>
    <ejs-circulargauge id='tooltip-container' enablePointerDrag= 'enablePointerDrag' :tooltipRender='tooltipRender' :tooltip='tooltip' >
    <e-axes>
      <e-axis >
        <e-pointers>
           <e-pointer value=70 ></e-pointer>
    </e-pointers>
    </e-axis>
    </e-axes>
    </ejs-circulargauge>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin, GaugeTooltip } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default {
      data: function () {
          return{
              enablePointerDrag: true
            tooltip: {
               enable: true,
               template: '<div id='templateWrap'><div class='des'>pointer <span>${Math.round(value)} </span></div></div>'
            }
          }
    },
     provide: {
       circulargauge: [ GaugeTooltip]
     },
        methods:{
         tooltipRender: function (args) {
            let cotainerObj = document.getElementById('tooltip-container');
            let value = args.pointer.currentValue;
            debugger;
            cotainerObj.ej2_instances[0].setPointerValue(0, 0, value);
            }
        }
};
</script>
<style>
  .wrapper {
    max-width: 300px;
    margin: 0 auto;
  }
#templateWrap .des {
    float: right;
    padding-left: 10px;
    line-height: 30px;
}
</style>
```

{% endtab %}

## changes

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
<div id="app">
      <div class='wrapper'>
        <ejs-circulargauge style='display:block' align='center' id='tooltip-container' :title='title' :titleStyle='titleStyle' :enablePointerDrag='enablePointerDrag' :tooltipRender='tooltipRender' :tooltip='tooltip'>
            <e-axes>
                <e-axis :radius='gaugeradius' :startAngle='startAngle' minimum=0 maximum=120 :endAngle='endAngle' :majorTicks='majorTicks' :lineStyle='lineStyle' :minorTicks='minorTicks' :labelStyle='labelStyle' :ranges='ranges'>
                    <e-pointers>
                        <e-pointer :value='value' :cap='cap' :radius='pointerRadius' :color='color' :animation='animation'></e-pointer>
                    </e-pointers>
                </e-axis>
            </e-axes>
        </ejs-circulargauge>
    </div>
</div>
</template>

<script>
import Vue from 'vue';
import {CircularGaugePlugin, GaugeTooltip } from "@syncfusion/ej2-vue-circulargauge";
Vue.use(CircularGaugePlugin);
export default {
    data: function () {
        return {
            title: 'Tooltip Customization',
            titleStyle: {
                size: '15px',
                color: 'grey'
            },
            gaugeradius: '90%',
            startAngle: 240,
            endAngle: 120,
            lineStyle: {
                width: 0
            },
            majorTicks: {
                color: 'white',
                offset: -5,
                height: 12
            },
            minorTicks: {
                width: 0
            },
            labelStyle: {
                useRangeColor: true,
                font: {
                    color: '#424242',
                    size: '13px',
                    fontFamily: 'Roboto'
                }
            },
            value: 70,
            pointerRadius: '60%',
            color: '#33BCBD',
            cap: {
                radius: 10,
                border: {
                    color: '#33BCBD',
                    width: 5
                }
            },
            animation: {
                enable: true,
                duration: 1500
            },
            ranges: [{
                start: 0,
                end: 50,
                startWidth: 10,
                endWidth: 10,
                radius: '102%',
                color: '#3A5DC8',
            }, {
                start: 50,
                end: 120,
                radius: '102%',
                startWidth: 10,
                endWidth: 10,
                color: '#33BCBD',
            }],
            tooltip: {
                enable: true,
                fill: 'transparent',
                template: "<div id='templateWrap'><img src='src/circulargauge/images/range1.png'/><img src='src/circulargauge/images/range3.png'/><div class='des'><span>${Math.round(pointers[0].value)} MPH</span></div></div>",
                border: {
                    color: '#33BCBD',
                    width: 2
                }
            },
            enablePointerDrag: true
        }
    },
    provide: {
        circulargauge: [GaugeTooltip]
    },
    methods: {
        load: function (args) {
            let selectedTheme = location.hash.split("/")[1];
            selectedTheme = selectedTheme ? selectedTheme : "Material";
            args.gauge.theme =
                selectedTheme.charAt(0).toUpperCase() + selectedTheme.slice(1);
        },
        tooltipRender: function (args) {
            let color;
            let cotainerObj = document.getElementById('tooltip-container');
            let value = args.pointer.currentValue;
            debugger;
            let content = args.content;
            if (value >= 0 && value <= 50) {
                let color = '#3A5DC8';
                content.children[1].remove();
                args.textStyle.color = color;
                args.border.color = color;
                cotainerObj.ej2_instances[0].axes[0].pointers[0].animation.enable = false;
                cotainerObj.ej2_instances[0].axes[0].pointers[0].color = color;
                cotainerObj.ej2_instances[0].axes[0].pointers[0].cap.border.color = color;
                cotainerObj.ej2_instances[0].setPointerValue(0, 0, value);
            } else {
                let color = '#33BCBD';
                content.children[0].remove();
                args.textStyle.color = color;
                args.border.color = color;
                cotainerObj.ej2_instances[0].axes[0].pointers[0].animation.enable = false;
                cotainerObj.ej2_instances[0].axes[0].pointers[0].color = color;
                cotainerObj.ej2_instances[0].axes[0].pointers[0].cap.border.color = color;
                cotainerObj.ej2_instances[0].setPointerValue(0, 0, value);
            }
        }
    }
};
</script>

<style>
  .wrapper {
    max-width: 300px;
    margin: 0 auto;
  }
#templateWrap img {
    border-radius: 30px;
    width: 30px;
    height: 30px;
    margin: 0 auto;
}

#templateWrap .des {
    float: right;
    padding-left: 10px;
    line-height: 30px;
}
</style>

```

{% endtab %}