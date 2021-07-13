---
title: " Events in Vue Linear Gauge component | Syncfusion "

component: "Linear Gauge"

description: "Learn here all about Events of Syncfusion Vue Linear Gauge component and more."
---

# Events in Vue Linear Gauge

This section describes the Linear Gauge component's event that gets triggered when corresponding operations are performed.

## animationComplete

When the pointer animation is completed, the [`animationComplete`](../api/linear-gauge#animationcomplete) event will be triggered. To know more about the arguments of this event, refer [here](../api/linear-gauge/iAnimationCompleteEventArgs/).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <ejs-lineargauge :animationComplete='animationComplete'>
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
    animationComplete: function (event) {
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

## annotationRender

Before the annotation is rendered in the Linear Gauge, the [`annotationRender`](../api/linear-gauge#annotationrender) event will be triggered. To know more about the arguments of this event, refer [here](../api/linear-gauge/iAnnotationRenderEventArgs/).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <ejs-lineargauge :annotationRender='annotationRender'>
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
    annotationRender: function (event) {
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

## axisLabelRender

Before each axis label is rendered in the Linear Gauge, the [`axisLabelRender`](../api/linear-gauge#axislabelrender) event is fired. To know more about the arguments of this event, refer [here](../api/linear-gauge/iAxisLabelRenderEventArgs/).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <ejs-lineargauge :axisLabelRender='axisLabelRender'>
        <e-axes>
          <e-axis>
            <e-pointers>
              <e-pointer></e-pointer>
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
    axisLabelRender: function (event) {
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

## beforePrint

The [`beforePrint`](../api/linear-gauge/#beforeprint) event is fired before the print begins. To know more about the arguments of this event, refer [here](../api/linear-gauge/iPrintEventArgs/).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <button v-on:click="print">Print</button>
      <ejs-lineargauge id="container" ref='gauge' :allowPrint='allowPrint' :beforePrint='beforePrint'>
      </ejs-lineargauge>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin, Print } from "@syncfusion/ej2-vue-lineargauge";
Vue.use(LinearGaugePlugin);
export default {
  data () {
    return {
      allowPrint: true
    }
  },
  methods: {
    beforePrint: function (event) {
    },
    print: function (event) {
      this.$refs.gauge.ej2Instances.print();
    }
  },
  provide: {
    lineargauge: [Print]
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

## dragEnd

The [`dragEnd`](../api/linear-gauge#dragend) event will be fired before the pointer drag is completed. To know more about the argument of this event, refer [here](../api/linear-gauge/iPointerDragEventArgs/).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <ejs-lineargauge :dragEnd='dragEnd'>
        <e-axes>
          <e-axis>
            <e-pointers>
              <e-pointer enableDrag=true></e-pointer>
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
    dragEnd: function (event) {
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

## dragMove

The [`dragMove`](../api/linear-gauge#dragmove) event will be fired when the pointer is dragged. To know more about the arguments of this event, refer [here](../api/linear-gauge/iPointerDragEventArgs/).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <ejs-lineargauge :dragMove='dragMove'>
        <e-axes>
          <e-axis>
            <e-pointers>
              <e-pointer enableDrag=true></e-pointer>
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
    dragMove: function (event) {
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

## dragStart

When the pointer drag begins, the [`dragStart`](../api/linear-gauge#dragstart) event is triggered. To know more about the arguments of this event, refer [here](../api/linear-gauge/iPointerDragEventArgs/).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <ejs-lineargauge :dragStart='dragStart'>
        <e-axes>
          <e-axis>
            <e-pointers>
              <e-pointer enableDrag=true></e-pointer>
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
    dragStart: function (event) {
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

## gaugeMouseDown

When mouse is pressed down on the gauge, the [`gaugeMouseDown`](../api/linear-gauge#gaugemousedown) event is triggered. To know more about the arguments of this event, refer [here](../api/linear-gauge/iMouseEventArgs/).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <ejs-lineargauge :gaugeMouseDown='gaugeMouseDown'>
        <e-axes>
          <e-axis>
            <e-pointers>
              <e-pointer></e-pointer>
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
    gaugeMouseDown: function (event) {
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

## gaugeMouseLeave

When mouse pointer moves over the gauge, the [`gaugemouseleave`](../api/linear-gauge#gaugemouseleave) event is triggered. To know more about the arguments of this event, refer [here](../api/linear-gauge/iMouseEventArgs/).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <ejs-lineargauge :gaugeMouseLeave='gaugeMouseLeave'>
        <e-axes>
          <e-axis>
            <e-pointers>
              <e-pointer></e-pointer>
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
    gaugeMouseLeave: function (event) {
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

## gaugeMouseMove

When mouse pointer leaves the gauge, the [`gaugeMouseMove`](../api/linear-gauge#gaugemousemove) event is triggered. To know more about the arguments of this event, refer [here](../api/linear-gauge/iMouseEventArgs/).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <ejs-lineargauge :gaugeMouseMove='gaugeMouseMove'>
        <e-axes>
          <e-axis>
            <e-pointers>
              <e-pointer></e-pointer>
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
    gaugeMouseMove: function (event) {
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

## gaugeMouseUp

When the mouse pointer is released over the Linear Gauge, the [`gaugeMouseUp`](../api/linear-gauge#gaugemouseup) event is triggered. To know more about the arguments of this event, refer [here](../api/linear-gauge/iMouseEventArgs/).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <ejs-lineargauge :gaugeMouseUp='gaugeMouseUp'>
        <e-axes>
          <e-axis>
            <e-pointers>
              <e-pointer></e-pointer>
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
    gaugeMouseUp: function (event) {
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

## load

Before the Linear Gauge is loaded, the [`load`](../api/linear-gauge#load) event is fired. To know more about the arguments of this event, refer [here](../api/linear-gauge/iLoadEventArgs/).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <ejs-lineargauge :load='load'>
        <e-axes>
          <e-axis>
            <e-pointers>
              <e-pointer></e-pointer>
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
    load: function (event) {
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

## loaded

After the Linear Gauge has been loaded, the [`loaded`](../api/linear-gauge#loaded) event will be triggered. To know more about the arguments of this event, refer [here](../api/linear-gauge/iLoadedEventArgs/).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <ejs-lineargauge :loaded='loaded'>
        <e-axes>
          <e-axis>
            <e-pointers>
              <e-pointer></e-pointer>
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
    loaded: function (event) {
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

## resized

After the window resizing, the [`resized`](../api/linear-gauge#resized) event is triggered. To know more about the arguments of this event, refer [here](../api/linear-gauge/iResizeEventArgs/).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <ejs-lineargauge :resized='resized'>
        <e-axes>
          <e-axis>
            <e-pointers>
              <e-pointer></e-pointer>
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
    resized: function (event) {
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

## tooltipRender

The [`tooltipRender`](../api/linear-gauge#tooltiprender) event is fired before the tooltip is rendered. To know more about the arguments of this event, refer [here](../api/linear-gauge/iTooltipRenderEventArgs/).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <ejs-lineargauge :tooltip='tooltip' :tooltipRender='tooltipRender'>
        <e-axes>
          <e-axis>
            <e-pointers>
              <e-pointer></e-pointer>
            </e-pointers>
          </e-axis>
        </e-axes>
      </ejs-lineargauge>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin, GaugeTooltip  } from "@syncfusion/ej2-vue-lineargauge";
Vue.use(LinearGaugePlugin);
export default {
  data:function(){
    return {
      tooltip: {
        enable: true,
      }
    }
  },
  methods: {
    tooltipRender: function (event) {
    }
  },
  provide: {
    lineargauge: [GaugeTooltip]
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

## valueChange

The [`valueChange`](../api/linear-gauge#valuechange) event is triggered when the pointer is dragged from one value to another. To know more about the arguments of this event, refer [here](../api/linear-gauge/iValueChangeEventArgs/).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <ejs-lineargauge :valueChange='valueChange'>
        <e-axes>
          <e-axis>
            <e-pointers enableDrag=true>
              <e-pointer></e-pointer>
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
    valueChange: function (event) {
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
