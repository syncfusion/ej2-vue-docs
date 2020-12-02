---
title: "Bullet Chart Axis Customization | Vue "

component: "Bullet Chart"

description: "Bullet Chart axis includes different customizations such as majortick and minortick, axis label, axis range."
---

# Axis Customization

## MajorTickLines and MinorTickLines Customization

You can customize the `width`, `color`, and `size` of minor and major tick lines using the
[`majorTickLines`](../api/bullet-chart/majorTickLinesSettings/) and
[`minorTickLines`](../api/bullet-chart/minorTickLinesSettings/) properties of the bullet-chart.

{% tab template="bullet-chart/axis/custom" %}

```html
<template>
  <div>
      <ejs-bulletchart id="bulletChart"
        :dataSource="data"
        valueField="value"
        targetField="target"
        :minimum="minimum"
        :maximum="maximum"
        :interval="interval"
        title="Revenue"
        :majorTickLines="majorTickLines"
        :minorTickLines="minorTickLines"
      >
      <e-bullet-range-collection>
          <e-bullet-range end="100" color="red"></e-bullet-range>
          <e-bullet-range end="200" color="blue"></e-bullet-range>
          <e-bullet-range end="300" color="green"></e-bullet-range>
        </e-bullet-range-collection>
      </ejs-bulletchart>
  </div>
</template>
<script>
import Vue from 'vue';
import { BulletChartPlugin } from '@syncfusion/ej2-vue-charts';
Vue.use(BulletChartPlugin);

export default {
  data () {
    return {
      data: [{ value: 270, target: 250 }],
      minimum: 0, maximum: 300, interval: 50,
      majorTickLines: { color: 'blue', width: 5 },
      minorTickLines: { color: 'red', width: 5 }
    }
  }
}
</script>
```

{% endtab %}

## Tick Placement

You can place major and minor ticks `inside` or `outside` the ranges using the [`tickPosition`](../api/bullet-chart/bulletChartModel/#tickposition) property of bullet-chart.

{% tab template="bullet-chart/axis/custom" %}

```html
<template>
  <div>
      <ejs-bulletchart id="bulletChart"
        :dataSource="data"
        valueField="value"
        targetField="target"
        :minimum="minimum"
        :maximum="maximum"
        :interval="interval"
        title="Revenue"
        tickPosition="Inside"
      >
      <e-bullet-range-collection>
          <e-bullet-range end="20" color="red"></e-bullet-range>
          <e-bullet-range end="25" color="blue"></e-bullet-range>
          <e-bullet-range end="30" color="green"></e-bullet-range>
        </e-bullet-range-collection>
      </ejs-bulletchart>
  </div>
</template>
<script>
import Vue from 'vue';
import { BulletChartPlugin } from '@syncfusion/ej2-vue-charts';
Vue.use(BulletChartPlugin);

export default {
  data () {
    return {
      data: [{ value: 23, target: 22 }],
      minimum: 0, maximum: 30, interval: 5
    }
  }
}
</script>
```

{% endtab %}

## Label Format

***Axis Label Format***

Axis numeric labels can be formatted by using the [`labelFormat`](../api/bullet-chart/bulletChartModel/#labelformat)property. Axis labels support all globalize formats. The following table describes the result of applying some commonly used label formats on numeric axis values.

{% tab template="bullet-chart/axis/custom" %}

```html
<template>
  <div>
      <ejs-bulletchart id="bulletChart"
        :dataSource="data"
        valueField="value"
        targetField="target"
        :minimum="minimum"
        :maximum="maximum"
        :interval="interval"
        title="Revenue"
        labelFormat="c"
      >
      <e-bullet-range-collection>
          <e-bullet-range end="500" color="red"></e-bullet-range>
          <e-bullet-range end="1000" color="blue"></e-bullet-range>
          <e-bullet-range end="1500" color="green"></e-bullet-range>
        </e-bullet-range-collection>
      </ejs-bulletchart>
  </div>
</template>
<script>
import Vue from 'vue';
import { BulletChartPlugin } from '@syncfusion/ej2-vue-charts';
Vue.use(BulletChartPlugin);

export default {
  data () {
    return {
      data: [{ value: 1100, target: 950 }],
      minimum: 0, maximum: 1500, interval: 500
    }
  }
}
</script>
```

{% endtab %}

The following 'Table' describes the result of applying some commonly used 'Label' formats on Numeric axis values.

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
<td>$1000.0</td>
<td>The Currency symbol is appended to number and number is rounded to 1 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>c2</td>
<td>$1000.00</td>
<td>The Currency symbol is appended to number and number is rounded to 2 decimal place</td>
</tr>
</table>

## GroupingSeparator

To separate groups of thousands, use the [`enableGroupSeparator`](../api/bullet-chart/bulletChartModel/#enablegroupseparator) property of bullet-chart.

{% tab template="bullet-chart/axis/custom" %}

```html
<template>
  <div>
      <ejs-bulletchart id="bulletChart"
        :dataSource="data"
        valueField="value"
        targetField="target"
        :minimum="minimum"
        :maximum="maximum"
        :interval="interval"
        title="Revenue"
        enableGroupSeparator=true
      >
      <e-bullet-range-collection>
          <e-bullet-range end="500" color="red"></e-bullet-range>
          <e-bullet-range end="1000" color="blue"></e-bullet-range>
          <e-bullet-range end="1500" color="green"></e-bullet-range>
        </e-bullet-range-collection>
      </ejs-bulletchart>
  </div>
</template>
<script>
import Vue from 'vue';
import { BulletChartPlugin } from '@syncfusion/ej2-vue-charts';
Vue.use(BulletChartPlugin);

export default {
  data () {
    return {
      data: [{ value: 1100, target: 950 }],
      minimum: 0, maximum: 1500, interval: 500
    }
  }
}
</script>
```

{% endtab %}

## Custom Label Format

You can also customize the axis label format using a placeholder like ${value}K, in which the value represents the axis label, e.g. $20K.

{% tab template="bullet-chart/axis/custom" %}

```html
<template>
  <div>
      <ejs-bulletchart id="bulletChart"
        :dataSource="data"
        valueField="value"
        targetField="target"
        :minimum="minimum"
        :maximum="maximum"
        :interval="interval"
        title="Revenue"
        labelFormat="${value}K"
      >
      <e-bullet-range-collection>
          <e-bullet-range end="100" color="red"></e-bullet-range>
          <e-bullet-range end="200" color="blue"></e-bullet-range>
          <e-bullet-range end="300" color="green"></e-bullet-range>
        </e-bullet-range-collection>
      </ejs-bulletchart>
  </div>
</template>
<script>
import Vue from 'vue';
import { BulletChartPlugin } from '@syncfusion/ej2-vue-charts';
Vue.use(BulletChartPlugin);

export default {
  data () {
    return {
      data: [{ value: 270, target: 250 }],
      minimum: 0, maximum: 300, interval: 50
    }
  }
}
</script>
```

{% endtab %}

## Label Placement

You can customize the axis labels `inside` or `outside` the bullet-chart using the [`labelPosition`](../api/bullet-chart/bulletChartModel/#labelposition) property.

{% tab template="bullet-chart/axis/custom" %}

```html
<template>
  <div>
      <ejs-bulletchart id="bulletChart"
        :dataSource="data"
        valueField="value"
        targetField="target"
        :minimum="minimum"
        :maximum="maximum"
        :interval="interval"
        title="Revenue"
        labelPosition="Inside"
      >
      <e-bullet-range-collection>
          <e-bullet-range end="100" color="red"></e-bullet-range>
          <e-bullet-range end="200" color="blue"></e-bullet-range>
          <e-bullet-range end="300" color="green"></e-bullet-range>
        </e-bullet-range-collection>
      </ejs-bulletchart>
  </div>
</template>
<script>
import Vue from 'vue';
import { BulletChartPlugin } from '@syncfusion/ej2-vue-charts';
Vue.use(BulletChartPlugin);

export default {
  data () {
    return {
      data: [{ value: 270, target: 250 }],
      minimum: 0, maximum: 300, interval: 50
    }
  }
}
</script>
```

{% endtab %}

## Opposed Position

To place an axis opposite to its original position,
set the [`opposedPosition`](../api/bullet-chart/bulletChartModel/#opposedposition) property to true.

{% tab template="bullet-chart/axis/custom" %}

```html
<template>
  <div>
      <ejs-bulletchart id="bulletChart"
        :dataSource="data"
        valueField="value"
        targetField="target"
        :minimum="minimum"
        :maximum="maximum"
        :interval="interval"
        title="Revenue"
        opposedPosition=true
      >
      <e-bullet-range-collection>
          <e-bullet-range end="100" color="red"></e-bullet-range>
          <e-bullet-range end="200" color="blue"></e-bullet-range>
          <e-bullet-range end="300" color="green"></e-bullet-range>
        </e-bullet-range-collection>
      </ejs-bulletchart>
  </div>
</template>
<script>
import Vue from 'vue';
import { BulletChartPlugin } from '@syncfusion/ej2-vue-charts';
Vue.use(BulletChartPlugin);

export default {
  data () {
    return {
      data: [{ value: 270, target: 250 }],
      minimum: 0, maximum: 300, interval: 50
    }
  }
}
</script>
```

{% endtab %}

## Category Label

You can display the x axis label by mapping the `categoryField` from dataSource of a bullet-chart. It is a more efficient way to understand data.

{% tab template="bullet-chart/axis/custom" %}

```html
<template>
  <div>
      <ejs-bulletchart id="bulletChart"
        :dataSource="data"
        valueField="value"
        targetField="target"
        :minimum="minimum"
        :maximum="maximum"
        :interval="interval"
        title="Revenue"
        categoryField="category"
      >
      <e-bullet-range-collection>
          <e-bullet-range end="100" color="red"></e-bullet-range>
          <e-bullet-range end="200" color="blue"></e-bullet-range>
          <e-bullet-range end="300" color="green"></e-bullet-range>
        </e-bullet-range-collection>
      </ejs-bulletchart>
  </div>
</template>
<script>
import Vue from 'vue';
import { BulletChartPlugin } from '@syncfusion/ej2-vue-charts';
Vue.use(BulletChartPlugin);

export default {
  data () {
    return {
      data: [{ value: 270, target: 250, category: "Product A" }],
      minimum: 0, maximum: 300, interval: 50
    }
  }
}
</script>
```

{% endtab %}

## Category Label Customization

You can customize the category label by using the `categoryLabelStyle` property of the bullet-chart.

{% tab template="bullet-chart/axis/custom" %}

```html
<template>
  <div>
      <ejs-bulletchart id="bulletChart"
        :dataSource="data"
        valueField="value"
        targetField="target"
        :minimum="minimum"
        :maximum="maximum"
        :interval="interval"
        title="Revenue"
        categoryField="category"
        :categoryLabelStyle="categoryStyle"
      >
      <e-bullet-range-collection>
          <e-bullet-range end="100" color="red"></e-bullet-range>
          <e-bullet-range end="200" color="blue"></e-bullet-range>
          <e-bullet-range end="300" color="green"></e-bullet-range>
        </e-bullet-range-collection>
      </ejs-bulletchart>
  </div>
</template>
<script>
import Vue from 'vue';
import { BulletChartPlugin } from '@syncfusion/ej2-vue-charts';
Vue.use(BulletChartPlugin);

export default {
  data () {
    return {
      data: [{ value: 270, target: 250, category: "Product A" }],
      minimum: 0, maximum: 300, interval: 50,
      categoryStyle: { color: "Orange" }
    }
  }
}
</script>
```

{% endtab %}