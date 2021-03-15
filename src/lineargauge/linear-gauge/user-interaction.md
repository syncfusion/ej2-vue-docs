---
title: "User Interaction"
component: "LinearGauge"
description: "Explains user interaction supports available in linear gauge"
---

# User Interaction

## Tooltip

<!-- markdownlint-disable MD036 -->

Linear gauge will display the details about the pointer value through [tooltip](../api/linear-gauge/tooltipSettings/), when the mouse is moved over the pointer. By default, tooltip will not be visible and you can enable the tooltip by setting [`enable`](../api/linear-gauge/tooltipSettings/#enable-boolean) property to true and by injecting `GaugeTooltip` module using `LinearGauge.Inject(GaugeTooltip)`.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge   :tooltip='tooltip' >
    <e-axes>
      <e-axis >
        <e-pointers>
           <e-pointer value=80 ></e-pointer>
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
import { LinearGaugePlugin, GaugeTooltip } from "@syncfusion/ej2-vue-lineargauge";

Vue.use(LinearGaugePlugin);
export default {
      data: function () {
          return{
            tooltip: {
               enable: true
            }
          }
    },
     provide: {
       lineargauge: [ GaugeTooltip]
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

<!-- markdownlint-disable MD013 -->

**Format the Tooltip**

<!-- markdownlint-disable MD013 -->

By default, tooltip will show the pointer value only. In addition to that, you can show more information in tooltip. For example, the format `${value}` shows pointer value with currency symbol.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge   :tooltip='tooltip' >
    <e-axes>
      <e-axis >
        <e-pointers>
           <e-pointer value=80 ></e-pointer>
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
import { LinearGaugePlugin, GaugeTooltip } from "@syncfusion/ej2-vue-lineargauge";

Vue.use(LinearGaugePlugin);
export default {
      data: function () {
          return{
            tooltip: {
               enable: true,
                format: '${value}'
            }
          }
    },
     provide: {
       lineargauge: [ GaugeTooltip]
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

### Tooltip Template

Any HTML elements can be displayed in the tooltip by using the [`template`](../api/linear-gauge/tooltipSettings/#template-string) property of the tooltip. You can use the {value} as placeholders in the HTML element to display the pointer values of the corresponding axis.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge   :tooltip='tooltip' >
    <e-axes>
      <e-axis >
        <e-pointers>
           <e-pointer value=80 ></e-pointer>
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
import { LinearGaugePlugin, GaugeTooltip } from "@syncfusion/ej2-vue-lineargauge";
Vue.use(LinearGaugePlugin);

var contentVue = Vue.component("contentTemplate", {
  template: '<div>Pointer: 80 </div>',
  data() {
    return {
      data: {}
    };
  }
});

var contentTemplate = function() {
  return { template: contentVue };
};

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
       lineargauge: [GaugeTooltip]
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

**Customize the Appearance of Tooltip**

* [`fill`](../api/linear-gauge/tooltipSettings/#fill-string) - Specifies fill color for tooltip
* [`border`](../api/linear-gauge/tooltipSettings/#border-bordermodel) - Specifies tooltip border width and color
* [`textStyle`](../api/linear-gauge/tooltipSettings/#textstyle-fontmodel) - Specifies the tooltip text style, such as color, font family, font style and font weight

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge   :tooltip='tooltip' >
    <e-axes>
      <e-axis >
        <e-pointers>
           <e-pointer value=80 ></e-pointer>
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
import { LinearGaugePlugin, GaugeTooltip } from "@syncfusion/ej2-vue-lineargauge";

Vue.use(LinearGaugePlugin);
export default {
      data: function () {
          return{
            tooltip: {
               enable: true,
            fill: '#e5bcbc',
            border: {
                color: '#d80000',
                width: 2
            }
            }
          }
    },
     provide: {
       lineargauge: [ GaugeTooltip]
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

## Pointer Drag

You can drag and drop either marker or bar pointer over the desired axis value using [`enableDrag`](../api/linear-gauge/pointer/#enabledrag-boolean) property in the [`pointer`](../api/linear-gauge/pointer/#pointer-pointermodel).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge >
    <e-axes>
      <e-axis >
        <e-pointers>
           <e-pointer value=80  enableDrag= 'true' ></e-pointer>
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
export default { };
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}