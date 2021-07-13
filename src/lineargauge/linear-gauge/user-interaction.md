---
title: "User Interaction in Vue Linear Gauge component | Syncfusion"

component: "Linear Gauge"

description: "Learn here all about the User Interaction feature of Syncfusion Vue Linear Gauge component and more."
---

# User Interaction in Vue Linear Gauge

## Tooltip

<!-- markdownlint-disable MD036 -->

Linear gauge displays the details about a pointer value through [`tooltip`](../api/linear-gauge/tooltipSettings) object, when the mouse hovers over the pointer. To enable the tooltip, set the [`enable`](../api/linear-gauge/tooltipSettings/#enable) property to "**true**" and inject the **GaugeTooltip**  module in **provide** section.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
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

### Tooltip Format

Tooltip in the Linear Gauge control can be formatted using the [`format`](../api/linear-gauge/tooltipSettings/#format) property in [`tooltip`](../api/linear-gauge/tooltipSettings/) object. It is used to render the tooltip in certain format or to add a user-defined unit in the tooltip. By default, the tooltip shows the pointer value only. In addition to that, more information can be added in the tooltip. For example, the format "**{value}km**" shows pointer value with kilometer unit in the tooltip.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <ejs-lineargauge :tooltip='tooltip'>
        <e-axes>
          <e-axis>
            <e-pointers>
              <e-pointer value=80 ></e-pointer>
            </e-pointers>
          </e-axis>
        </e-axes>
      </ejs-lineargauge>
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
        format: '{value}km'
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

The HTML element can be rendered in the tooltip of the Linear Gauge using the [`template`](../api/linear-gauge/tooltipSettings/#template) property in the [`tooltip`](../api/linear-gauge/tooltipSettings/). The "**${value}**" can be used as placeholders in the HTML element to display the pointer values of the corresponding axis.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <ejs-lineargauge :tooltip='tooltip'>
        <e-axes>
          <e-axis >
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
import { LinearGaugePlugin, GaugeTooltip } from "@syncfusion/ej2-vue-lineargauge";
Vue.use(LinearGaugePlugin);
export default {
  data: function () {
    return{
      tooltip: {
        enable: true,
        template: '<div>Pointer: 80 </div>'
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

### Customize the appearance of the tooltip

The tooltip can be customized using the following properties in [`tooltip`](../api/linear-gauge/tooltipSettings) object.

* [`fill`](../api/linear-gauge/tooltipSettings/#fill) - To fill the color for tooltip.
* [`enableAnimation`](../api/linear-gauge/tooltipSettings/#enableanimation) - To enable or disable the tooltip animation.
* [`border`](../api/linear-gauge/tooltipSettings/#border) - To set the color and width for the border of the tooltip.
* [`textStyle`](../api/linear-gauge/tooltipSettings/#textstyle) - To customize the style of the text in tooltip.
* [`showAtMousePosition`](../api/linear-gauge/tooltipSettings/#showatmouseposition) - To show the tooltip at the mouse position.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <ejs-lineargauge :tooltip='tooltip'>
        <e-axes>
          <e-axis >
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

### Positioning the tooltip

The tooltip is positioned at the "**End**" of the pointer. To change the position of the tooltip at the start, or center of the pointer, set the [`position`](../api/linear-gauge/tooltipSettings/#position) property to "**Start**" or "**Center**".

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
  <div class="content-wrapper">
    <div align='center'>
      <ejs-lineargauge :tooltip='tooltip'>
        <e-axes>
          <e-axis >
            <e-pointers>
              <e-pointer value=80 type="Bar" color="blue"></e-pointer>
            </e-pointers>
          </e-axis>
        </e-axes>
      </ejs-lineargauge>
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
        position: "Center"
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

To drag either marker or bar pointer to the desired axis value, set the [`enableDrag`](../api/linear-gauge/pointer/#enabledrag) property as **true** in the [`e-pointer`](../api/linear-gauge/pointerModel/).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
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