---
title: " Annotations in Vue Linear Gauge component | Syncfusion "

component: "Linear Gauge"

description: "Learn here all about Annotations feature of Syncfusion Vue Linear Gauge component and more."
---

# Annotations in Vue Linear Gauge

<!-- markdownlint-disable MD013 -->

Annotations are used to mark the specific area of interest in the Linear Gauge with text, HTML elements, or images. Any number of annotations can be added to the Linear Gauge component.

## Adding annotation

To render the custom HTML elements in the Linear Gauge component, use the [`content`](../api/linear-gauge/annotation/#content) property in the [`e-annotation`](../api/linear-gauge/annotation/). The annotation can be rendered either by specifying the id of the element or specifying the code to create a new element that needs to be displayed in the gauge area.

<!-- markdownlint-disable MD036 -->

```typescript

<template>
  <div class="control-section">
    <div align='center'>
      <ejs-lineargauge ref='lineargauge' style='display:block' align='center'>
        <e-annotations>
          <e-annotation :content='contentTemplate' :zIndex='zindex' :axisValue=50>
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
export default {
  data:function() {
    return {
      zindex: 1,
      contentTemplate: '<div id="first"><h1>Gauge</h1></div>',
    }
  },
  provide: {
    lineargauge: [Annotations]
  },
};
</script>

```

## Customization

The following properties are used to customize the annotation.

* [`zIndex`](../api/linear-gauge/annotation/#zindex) - This property is used to bring the annotation to the front or back, when annotation overlaps with another element.
* [`axisValue`](../api/linear-gauge/annotation/#axisvalue) - This property is used to place the annotation in the specified axis value with respect to the provided axis index.
* [`axisIndex`](../api/linear-gauge/annotation/#axisindex) - This property is used to place the annotation in the specified axis with respect to the provided axis value.
* [`horizontalAlignment`](../api/linear-gauge/annotation#horizontalalignment) - This property is used to place the annotation horizontally.
* [`verticalAlignment`](../api/linear-gauge/annotation#verticalalignment) - This property is used to place the annotation vertically.
* [`x`](../api/linear-gauge/annotation/#x), [`y`](../api/linear-gauge/annotation/#y) - This property is used to place the annotation in the specified location.

### Changing the z-index

To change the stack order of an annotation element, the [`zIndex`](../api/linear-gauge/annotation/#zindex) property of the [`e-annotation`](../api/linear-gauge/annotation/) can be used.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
  <div class="control-section">
    <div align='center'>
      <ejs-lineargauge style='display:block' align='center'>
        <e-annotations>
          <e-annotation :content='contentTemplate' :zIndex='zindex' horizontalAlignment='Center' verticalAlignment='Center'>
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
export default {
  data:function(){
    return{
      zindex: 1,
      contentTemplate: '<div id="first"><h1>Gauge</h1></div>',
    }
  },
  provide: {
    lineargauge: [Annotations]
  },
};
</script>
```

{% endtab %}

### Positioning an annotation

The annotation can be placed anywhere in the Linear Gauge by setting the pixel value to the [`x`](../api/linear-gauge/annotation/#x) and [`y`](../api/linear-gauge/annotation/#y) properties in the [`e-annotation`](../api/linear-gauge/annotation/).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
  <div class="control-section">
    <div align='center'>
      <ejs-lineargauge style='display:block' align='center'>
        <e-annotations>
          <e-annotation :content='contentTemplate' :zIndex='zindex' x=100 y=100>
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
export default {
  data:function() {
    return{
      zindex: 1,
      contentTemplate: '<div id="first"><h1>Gauge</h1></div>',
    }
  },
  provide: {
    lineargauge: [Annotations]
  },
};
</script>

```

{% endtab %}

<!-- markdownlint-disable MD036 -->

### Alignment of annotation

The annotation can be aligned horizontally and vertically by using the [`horizontalAlignment`](../api/linear-gauge/annotation/#horizontalalignment) and [`verticalAlignment`](../api/linear-gauge/annotation/#verticalalignment) properties respectively. The possible values can be "**Center**", "**Far**", "**Near**", and "**None**". The [`horizontalAlignment`](../api/linear-gauge/annotation/#horizontalalignment) and [`verticalAlignment`](../api/linear-gauge/annotation/#verticalalignment) properties are not applicable when the [`x`](../api/linear-gauge/annotation/#x) and [`y`](../api/linear-gauge/annotation/#y) properties are set in the [`e-annotation`](../api/linear-gauge/annotation/).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
  <div class="control-section">
    <div align='center'>
      <ejs-lineargauge style='display:block' align='center'>
        <e-annotations>
          <e-annotation :content='contentTemplate' :zIndex='zindex' horizontalAlignment='Center' verticalAlignment='Center'>
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
export default {
  data:function() {
    return {
      zindex: 1,
      contentTemplate: '<div id="first"><h1>Gauge</h1></div>',
    }
  },
  provide: {
    lineargauge: [Annotations]
  },
};
</script>
```

{% endtab %}

## Multiple annotations

Multiple annotations can be added to the Linear Gauge component by adding the multiple [`e-annotation`](../api/linear-gauge/annotation/) in the [`e-annotations`](../api/linear-gauge/#annotations) and customization for the annotation can be done with the [`e-annotation`](../api/linear-gauge/annotation/).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="control-section">
    <div align='center'>
      <ejs-lineargauge style='display:block' align='center'>
        <e-annotations>
          <e-annotation :content='contentTemplate' :zIndex='zindex' horizontalAlignment='Near' verticalAlignment='Center' :x='x1' :y='y1'>
          </e-annotation>
          <e-annotation :content='contentTemplate1' :zIndex='zindex' verticalAlignment='Center' :x='x2' :y='y2'>
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
export default {
  data:function() {
    return {
      zindex: 1,
      contentTemplate: '<div><h1 style="color:red;">Speed</h1></div>',
      contentTemplate1: '<div><h1 style="color:blue;">Meter</h1></div>',
      x1:290,
      y1:250,
      x2:10,
      y2:-190,
    }
  },
  provide: {
    lineargauge: [Annotations]
  },
};
</script>

```

{% endtab %}
