---
title: "Axes"
component: "LinearGauge"
description: "Axes support in linear gauge"
---

# Axes

Axes is a collection of linear axis which can be used to indicate the numeric values. Line, ticks, labels, ranges and pointers are the sub elements of an axis.

## Line Customization

The [`line`](../api/linear-gauge/lineModel/) property of an axis provides options to customize the [`height`](../api/linear-gauge/lineModel/#height-number), [`width`](../api/linear-gauge/lineModel/#width-number), [`color`](../api/linear-gauge/lineModel/#color-string) and [`offset`](../api/linear-gauge/lineModel/#offset-number) of the axis line.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge >
    <e-axes>
       <e-axis :line='line'>
    </e-axis>
    </e-axes>
    </ejs-lineargauge>
  </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";
Vue.use(LinearGaugePlugin);
export default {
      data: function () {
        return {
             line: {
            height: 150,
            width: 2,
            color: '#4286f4',
            offset: 2
        }
        }
      }
};
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}

## Ticks Customization

You can customize the [`height`](../api/linear-gauge/tickModel/#height-number), [`color`](../api/linear-gauge/tickModel/#color-string) and [`width`](../api/linear-gauge/tickModel/#width-number) of major and minor ticks, by using [`majorTicks`](../api/linear-gauge/tickModel/) and [`minorTicks`](../api/linear-gauge/tickModel/) property. By default, interval for major ticks will be calculated automatically and also you can customize the interval for major and minor ticks using interval property.

<!-- markdownlint-disable MD036 -->

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge >
    <e-axes>
       <e-axis minimum= 20  maximum= 140 :majorTicks='majorTicks' :minorTicks='minorTicks'>
    </e-axis>
    </e-axes>
    </ejs-lineargauge>
  </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";
Vue.use(LinearGaugePlugin);
export default {
      data: function () {
        return {
        majorTicks: {
            interval: 20
        },
        minorTicks: {
            interval: 5,
            color: 'red'
        }
        }
      }
};
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}

## Labels Customization

The [`labelStyle`](../api/linear-gauge/labelModel/) property of an axis provides options to
customize the [`offset`](../api/linear-gauge/labelModel/#offset-number), [`format`](../api/linear-gauge/labelModel/#format-string), [`color`](../api/linear-gauge/labelModel/#color-string) and [`font`](../api/linear-gauge/labelModel/#font-fontmodel) of the axis labels.

<!-- markdownlint-disable MD036 -->

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge >
    <e-axes>
       <e-axis :labelStyle='labelStyle2'>
    </e-axis>
    </e-axes>
    </ejs-lineargauge>
  </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";

Vue.use(LinearGaugePlugin);
export default {
      data: function () {
        return {
       labelStyle2: {
            font: {
              color: 'red'
            }
        }
        }
      }
};
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}

### Customize the display of the last label

If the last label is not in the visible range, it will be hidden by default. If you want to show the last label, set the [`showLastLabel`](../api/linear-gauge/axis/#showlastlabel) property to **true** in the axes property of linear gauge.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge >
    <e-axes>
       <e-axis showLastLabel= 'true' maximum=115 :line='line'>
       <e-pointers>
           <e-pointer value=20 height=15 width=15 color='#757575' offset=30></e-pointer>
      </e-pointers>
    </e-axis>
    </e-axes>
    </ejs-lineargauge>
  </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";

Vue.use(LinearGaugePlugin);
export default {
  data: function () {
        return {
            line: {
              color: '#9E9E9E'
            }
        }
    }
};
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}

### Label Format

Axis labels can be formatted by using the [`format`](../api/linear-gauge/labelModel/#format-string) property in [`labelStyle`](../api/linear-gauge/axis/#labelstyle-labelmodel) and it supports all the globalize formats.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge >
    <e-axes>
       <e-axis :labelStyle='labelStyle'>
    </e-axis>
    </e-axes>
    </ejs-lineargauge>
  </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";

Vue.use(LinearGaugePlugin);
export default {
      data: function () {
        return {
       labelStyle: {
            format: 'c'
        }
        }
      }
};
</script>
<style>
#content-wrapper {
    padding: 0px !important;
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

<!-- markdownlint-disable MD036 -->

### Custom Label Format

Axis also supports custom label format using placeholder like {value}°C, in which the value represents the axis label e.g. 20°C.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge :axes= 'axes' >
    </ejs-lineargauge>
  </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";

Vue.use(LinearGaugePlugin);
export default {
      data: function () {
        return {
       axes: [{
            minimum: 20,
            maximum: 140,
        labelStyle: {
           format: '{value}°C'
        }
    }]
        }
      }
};
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}

## Orientation

By default, the linear gauge gets rendered vertically. To change its orientation, the [`orientation`](../api/linear-gauge/axis/#orientation) property must be set to **"Horizontal"**

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge :orientation='orientation' :axes= 'axes' >
    </ejs-lineargauge>
  </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";

Vue.use(LinearGaugePlugin);
export default {
      data: function () {
        return {
          orientation: "Horizontal",
       axes: [{
            minimum: 20,
            maximum: 140,
          }]
        }
      }
};
</script>
```

{% endtab %}

## Inverted Axes

[`isInversed`](../api/linear-gauge/axis/#isinversed-boolean) property is used to choose the rendering of axis either bottom to top or top to bottom direction.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge >
    <e-axes>
       <e-axis isInversed= 'true'>
    </e-axis>
    </e-axes>
    </ejs-lineargauge>
  </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";

Vue.use(LinearGaugePlugin);
export default {

};
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}

## Opposed Axes

To place an axis opposite from its original position, set [`opposedPosition`](../api/linear-gauge/axis/#opposedposition-boolean) property as true in the axis.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge >
    <e-axes>
       <e-axis opposedPosition= 'true'>
    </e-axis>
    </e-axes>
    </ejs-lineargauge>
  </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";

Vue.use(LinearGaugePlugin);
export default { };
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}

## Multiple Axes

You can render any number of axis for a linear gauge by using array of axis objects.
Each axis will have its own ranges, pointers, annotations and customization options.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge :axes='axes' >
    </ejs-lineargauge>
  </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";

Vue.use(LinearGaugePlugin);
export default {
      data: function () {
        return {
       axes: [{
        labelStyle: {
           format: '{value}°C'
        }
    },
    {
        opposedPosition: true,
        labelStyle: {
           format: '{value}°F'
        }
    }]
        }
      }
};
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}