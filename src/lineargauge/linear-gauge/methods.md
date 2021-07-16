---
title: " Methods in Vue Linear Gauge component | Syncfusion "

component: "Linear Gauge"

description: "Learn here all about the Methods of Syncfusion Vue Linear Gauge component and more."
---
# Methods in Vue Linear Gauge

The following methods are available in the Linear Gauge component.

## setPointerValue

To change the pointer value dynamically, use the [`setPointerValue`](../api/linear-gauge#setpointervalue) method in the Linear Gauge component. The following are the arguments for this method.

|   Argument name      |   Description                            |
|----------------------| -----------------------------------------|
|     axisIndex        |    Specifies the index of the axis in which the pointer value is to be updated.|
|     pointerIndex     |    Specifies the index of the pointer to be updated.           |
|     pointerValue     |    Specifies the value of the pointer to be updated.           |

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <button v-on:click="clicked">Click</button>
      <ejs-lineargauge ref='gauge'>
        <e-axes>
          <e-axis>
            <e-pointers>
              <e-pointer value=80></e-pointer>
            </e-pointers>
          </e-axis>
        </e-axes>
      </ejs-lineargauge>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";
Vue.use(LinearGaugePlugin);
export default {
  methods: {
    clicked: function (event) {
      this.$refs.gauge.ej2Instances.setPointerValue(0, 0, 30);
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

## setAnnotationValue

To change the annotation content dynamically, use the [`setAnnotationValue`](../api/linear-gauge#setannotationvalue) method in the Linear Gauge component. The following are the arguments for this method.

|   Argument name      |   Description                            |
|----------------------| -----------------------------------------|
|     annotationIndex  |    Specifies the index number of the annotation to be updated. |
|     content          |    Specifies the text for the annotation to be updated.        |
|     axisValue        |    Specifies the value of the axis where the annotation is to be placed.|

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <button v-on:click="clicked">Click</button>
      <ejs-lineargauge ref='gauge'>
        <e-annotations>
            <e-annotation :content='contentTemplate' :zIndex='zindex' :axisValue='axisValue'>
            </e-annotation>
        </e-annotations>
        <e-axes>
          <e-axis>
            <e-pointers>
              <e-pointer value=10></e-pointer>
            </e-pointers>
          </e-axis>
        </e-axes>
      </ejs-lineargauge>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin, Annotations } from "@syncfusion/ej2-vue-lineargauge";
Vue.use(LinearGaugePlugin);
export default {
  data:function(){
    return{
        zindex: 1,
        contentTemplate : '10',
        axisValue: 0
    }
  },
  methods: {
    clicked: function (event) {
      this.$refs.gauge.ej2Instances.setAnnotationValue(0, '50', 50);
    }
  },
  provide: {
    lineargauge: [Annotations]
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

## refresh

The [`refresh`](../api/linear-gauge#refresh) method can be used to change the state of the component and render it again. In the following example, the gauge is rendered again using the [`refresh`](../api/linear-gauge#refresh) method.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <button v-on:click="clicked">Click</button>
      <ejs-lineargauge ref='gauge'>
        <e-axes>
          <e-axis>
            <e-pointers>
              <e-pointer value=10></e-pointer>
            </e-pointers>
          </e-axis>
        </e-axes>
      </ejs-lineargauge>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";
Vue.use(LinearGaugePlugin);
export default {
  methods: {
    clicked: function (event) {
      this.$refs.gauge.ej2Instances.refresh();
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