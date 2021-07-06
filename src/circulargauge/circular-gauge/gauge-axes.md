---
title: "Axes"
component: "CircularGauge"
description: "Axes support in circular gauge"
---

# Axes

By default, gauge will be displayed with an axis. Each axis contains its own ranges, pointers and annotation.

<!-- markdownlint-disable MD036 -->

## Axis Customization

You can customize the width and color of an axis line by using [`lineStyle`](../api/circular-gauge/line/) property.
Background for an axis can be customized by using [`background`](../api/circular-gauge/axis/#background-string)
property.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
        <div class='wrapper'>
           <ejs-circulargauge>
              <e-axes>
                  <e-axis  :lineStyle= 'lineStyle' background= 'rgba(0, 128, 128, 0.3)'>
                  </e-axis>
              </e-axes>
           </ejs-circulargauge>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default {
    data: function () {
        return {
            lineStyle: {
            width: 2,
            color: 'red'
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
</style>
```

{% endtab %}

<!-- markdownlint-disable MD036 -->

## Angles and Direction

Circular gauge axis can sweep from 0 to 360 degrees. By default start angle of an axis is 200 degree and
end angle is 160 degree and you can customize this option by using
[`startAngle`](../api/circular-gauge/axis/#startangle-number) and [`endAngle`](../api/circular-gauge/axis/#endangle-number) property.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
        <div class='wrapper'>
            <ejs-circulargauge :axes = 'axes'>
            </ejs-circulargauge>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
    export default {
        data: function () {
            return {
                axes: [{
                    startAngle: 270,
                     endAngle: 90
                }]
            }
        }
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

<!-- markdownlint-disable MD036 -->

### AntiClockWise Direction

The [`direction`](../api/circular-gauge/axis/#direction-string) property enables you to render the gauge axis either in
`ClockWise` or in `AntiClockWise` direction.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
<div id="app">
    <div class='wrapper'>
        <ejs-circulargauge >
            <e-axes>
                <e-axis  direction= 'AntiClockWise'>
                </e-axis>
            </e-axes>
        </ejs-circulargauge>
    </div>
</div>
</template>

<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default { };
</script>
<style>
    .wrapper {
        max-width: 300px;
        margin: 0 auto;
    }
</style>

```

{% endtab %}

<!-- markdownlint-disable MD036 -->

## Axis Radius

By default, radius of an axis is calculated based on the available size.
You can customize this, by using [`radius`](../api/circular-gauge/axis/#radius-string) property.
It takes value either in `percentage` or in `pixel`.

### In Pixel

You can set the radius of the gauge in pixel as demonstrated below,

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
<div id="app">
    <div class='wrapper'>
        <ejs-circulargauge >
            <e-axes>
                <e-axis radius= '150'>
                </e-axis>
            </e-axes>
        </ejs-circulargauge>
    </div>
</div>
</template>

<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default { };
</script>
<style>
    .wrapper {
        max-width: 300px;
        margin: 0 auto;
    }
</style>
```

{% endtab %}

<!-- markdownlint-disable MD036 -->

### In Percentage

By setting value in percentage, gauge gets its dimension with respect to its available size.
For example, when the radius is ‘50%’, gauge renders to half of the available size.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
<div id="app">
    <div class='wrapper'>
        <ejs-circulargauge>
            <e-axes>
                <e-axis radius= '50%'>
                </e-axis>
            </e-axes>
        </ejs-circulargauge>
    </div>
</div>
</template>

<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default { };
</script>
<style>
    .wrapper {
        max-width: 300px;
        margin: 0 auto;
    }
</style>
```

{% endtab %}

<!-- markdownlint-disable MD036 -->

## Ticks

You can customize the [`height`](../api/circular-gauge/tickModel/#color-string),
[`color`](../api/circular-gauge/tickModel/#color-string) and
[`width`](../api/circular-gauge/tickModel/#width-number) of major and minor ticks by
using [`majorTicks`](../api/circular-gauge/axis/#majorticks-tickmodel)
and [`minorTicks`](../api/circular-gauge/axis/#minorticks-tickmodel) property.
By default, [`interval`](../api/circular-gauge/tickModel/#interval-number) for
`majorTicks` will be calculated automatically
and also you can customize the interval for major and minor ticks using
`interval` property.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
        <div class='wrapper'>
            <ejs-circulargauge >
                <e-axes>
                    <e-axis  :majorTicks= 'majorTicks' :minorTicks= 'minorTicks' >
                    </e-axis>
                </e-axes>
            </ejs-circulargauge>
         </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default {
    data: function () {
    return {
        majorTicks: {
            interval: 10,
            color:'red',
            height: 10,
            width: 3
        },
        minorTicks: {
            interval: 5,
            color:'green',
            height: 5,
            width: 2
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
</style>
```

{% endtab %}

### Tick Position

Both minor and major ticks can be moved by using [`offset`](../api/circular-gauge/tickModel/#offset-number) and [`position`](../api/circular-gauge/tickModel/#position-string) property. The [`offset`](../api/circular-gauge/tickModel/#offset-number) defines the distance between the axis and ticks.
By default, offset value is 0. The [`position`](../api/circular-gauge/tickModel/#position-string) will place the ticks either inside or outside of the axis.
By default, ticks will be placed `inside` the axis.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
        <div class='wrapper'>
            <ejs-circulargauge>
                <e-axes>
                    <e-axis  :majorTicks= 'majorTicks' :minorTicks= 'minorTicks'>
                    </e-axis>
                </e-axes>
            </ejs-circulargauge>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default {
    data: function () {
        return {
            majorTicks: {
                interval: 10,
                color:'red',
                height: 10,
                width: 3,
                position: 'Inside',
                offset: 5
            },
            minorTicks: {
                interval: 5,
                color:'green',
                height: 5,
                width: 2,
                position: 'Inside',
                offset: 5
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
</style>
```

{% endtab %}

## Labels

Labels of an axis can be customized by using [`font`](../api/circular-gauge/labelModel/#font-fontmodel) property in [`labelStyle`](../api/circular-gauge/axis/#labelstyle-labelmodel) options.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
        <div class='wrapper'>
            <ejs-circulargauge>
                <e-axes>
                    <e-axis :labelStyle ='labelStyle' >
                    </e-axis>
                </e-axes>
            </ejs-circulargauge>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default {
    data: function () {
        return {
            labelStyle: {
                font: {
                    color: 'red',
                    size: '20px',
                    fontWeight: 'Bold'
                }
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
</style>
```

{% endtab %}

### Label Position

Labels can be moved by using [`offset`](../api/circular-gauge/labelModel/#offset-number) or
[`position`](../api/circular-gauge/labelModel/#position-string) property.
The [`offset`](../api/circular-gauge/labelModel/#offset-number) defines the distance between the labels and ticks.
By default, offset value is 0.
The [`position`](../api/circular-gauge/labelModel/#position-string) will place the labels either inside or outside of the axis.
By default, labels will be placed `inside` the axis.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
        <div class='wrapper'>
            <ejs-circulargauge>
                <e-axes>
                    <e-axis :labelStyle ='labelStyle'>
                    </e-axis>
                </e-axes>
            </ejs-circulargauge>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default {
    data: function () {
        return {
            labelStyle: {
                position: 'Outside',
                offset: 5
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
</style>
```

{% endtab %}

### Display the last label, even if it isn’t in the visible range**

If the last label is not in the visible range, it will be hidden by default. If you want to show the last label, set the `showLastLabel` property to `true` in the `axes` API of circular gauge.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
        <div class='wrapper'>
            <ejs-circulargauge>
                <e-axes>
                    <e-axis showLastLabel="true" minimum= 0 maximum= 170 startAngle= 210 endAngle= 150>
                    </e-axis>
                </e-axes>
            </ejs-circulargauge>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default {
    data: function () {
        return {}
    }
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

### Auto Angle

Labels can be swept along the axis angle by enabling [`autoAngle`](../api/circular-gauge/labelModel/#autoangle-boolean) property.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
     <div id="app">
         <div class='wrapper'>
             <ejs-circulargauge>
                 <e-axes>
                     <e-axis :labelStyle ='labelStyle'>
                     </e-axis>
                 </e-axes>
             </ejs-circulargauge>
         </div>
     </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default {
    data: function () {
    return {
        labelStyle: {
            autoAngle: true
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
</style>
```

{% endtab %}

### Smart Labels

When an axis makes a complete circle, then the first and last label of the axis will get overlap with each other.
In this scenario, you can either hide 1st or last label using [`hiddenLabel`](../api/circular-gauge/labelModel/#hiddenlabel-string) property.
When `hiddenLabel` value is `First`,
then the 1st label will be hidden and when the
`hiddenLabel` value is 'Last',
then the last label will be hidden.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
        <div class='wrapper'>
            <ejs-circulargauge>
                <e-axes>
                    <e-axis  minimum= 0 maximum= 12 startAngle= 0 endAngle= 360 :labelStyle ='labelStyle' :minorTicks= 'minorTicks' :majorTicks= 'majorTicks' >
                    </e-axis>
                </e-axes>
            </ejs-circulargauge>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default {
    data: function () {
        return {
            majorTicks: {
                interval: 1,
                position: 'Inside',
                height: 10
            },
            minorTicks: {
                interval: 0.2,
                position: 'Inside',
                height: 5
            },
            labelStyle: {
                position: 'Inside',
                hiddenLabel: 'First'
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
</style>
```

{% endtab %}

### Label Format

Axis labels can be formatted by using [`format`](../api/circular-gauge/labelModel/#format-string) property in [`labelStyle`](../api/circular-gauge/label/) and its supports all globalize format.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
        <div class='wrapper'>
            <ejs-circulargauge>
                <e-axes>
                    <e-axis :labelStyle ='labelStyle'>
                    </e-axis>
                </e-axes>
            </ejs-circulargauge>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default {
    data: function () {
    return {
        labelStyle: {
            format: 'p1'
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
</style>
```

{% endtab %}

The following table describes the result of applying some commonly used label formats on numeric values.

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Label Value</b></td>
<td><b>Label Format property value</b></td>
<td><b>Result </b></td>
<td><b>Description </b></td>
</tr>
<tr>
<td>1000</td>
<td>n1</td>
<td>1000.0</td>
<td>The Number is rounded to 1 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>n2</td>
<td>1000.00</td>
<td>The Number is rounded to 2 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>n3</td>
<td>1000.000</td>
<td>The Number is rounded to 3 decimal place</td>
</tr>
<tr>
<td>0.01</td>
<td>p1</td>
<td>1.0%</td>
<td>The Number is converted to percentage with 1 decimal place</td>
</tr>
<tr>
<td>0.01</td>
<td>p2</td>
<td>1.00%</td>
<td>The Number is converted to percentage with 2 decimal place</td>
</tr>
<tr>
<td>0.01</td>
<td>p3</td>
<td>1.000%</td>
<td>The Number is converted to percentage with 3 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>c1</td>
<td>$1,000.0</td>
<td>The Currency symbol is appended to number and number is rounded to 1 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>c2</td>
<td>$1,000.00</td>
<td>The Currency symbol is appended to number and number is rounded to 2 decimal place</td>
</tr>
</table>

### Custom Label Format

Axis labels support custom label format using placeholder like {value}°C, in which the value represent the axis label e.g 20°C.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
        <div class='wrapper'>
            <ejs-circulargauge>
                <e-axes>
                    <e-axis :labelStyle ='labelStyle'>
                    </e-axis>
                </e-axes>
            </ejs-circulargauge>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default {
    data: function () {
        return {
            labelStyle: {
                format: '{value}°C'
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
</style>
```

{% endtab %}

### Hide intersecting axis labels

When the axis labels overlap with each other, you can hide the intersected labels by setting the `hideIntersectingLabel` property to true in the axis.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
        <div class='wrapper'>
            <ejs-circulargauge>
                <e-axes>
                    <e-axis :startAngle='startAngle' :hideIntersectingLabel='hideIntersectingLabel' :endAngle='endAngle' :majorTicks='majorTicks' :minorTicks='minorTicks' minimum=0 maximum=200>
                    </e-axis>
                </e-axes>
            </ejs-circulargauge>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default {
    data: function () {
        return {
            startAngle: 270,
            endAngle: 90,
            hideIntersectingLabel: true,
            majorTicks: {
                interval: 4
            },
            minorTicks: {
                interval: 2
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
</style>
```

{% endtab %}

## Minimum and Maximum

The [`minimum`](../api/circular-gauge/axis/#minimum-number) and [`maximum`](../api/circular-gauge/axis/#maximum-number) properties
enables you to customize the start and end values of an axis.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
        <div class='wrapper'>
            <ejs-circulargauge>
                <e-axes>
                    <e-axis minimum= 50 maximum= 250>
                    </e-axis>
                </e-axes>
            </ejs-circulargauge>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default { };
</script>
<style>
    .wrapper {
        max-width: 300px;
        margin: 0 auto;
    }
</style>
```

{% endtab %}

## Multiple Axes

In addition to the default axis, you can add n number of axis to a gauge.
Each axis will have its own ranges, pointers, annotations and customization options.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
        <div class='wrapper'>
            <ejs-circulargauge :axes= 'axes'>
            </ejs-circulargauge>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default {
    data: function () {
    return {
        axes: [{
            majorTicks: {
                interval: 10,
                position: 'Inside',
                height: 10,
            },
            pointers: [],
            minorTicks: {
                interval: 5,
                position: 'Inside',
                height: 5,
            }
        },
        {
            pointers: [],
            majorTicks: {
                interval: 10,
                position: 'Inside',
                height: 10,
                color: '#27d5ff'
            },
            minorTicks: {
                interval: 5,
                position: 'Inside',
                height: 5,
                color: '#27d5ff'
            }
       }]
    }
    }
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