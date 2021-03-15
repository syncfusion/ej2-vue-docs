---
title: "Appearance"
component: "LinearGauge"
description: "Explains how to customize the appearance of linear gauge"
---

# Appearance

## Gauge Area Customization

<!-- markdownlint-disable MD036 -->

**Customize the Linear Gauge background**

Using [`background`](../api/linear-gauge/linearGaugeModel/#background-string) and
[`border`](../api/linear-gauge/linearGaugeModel/#border-bordermodel) properties, you can change the background color and border of the linear gauge.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge background= 'skyblue':border ='border' >
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
             border: { color: "#FF0000", width: 2 }
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

### Gauge Margin

You can set margin for the linear gauge through [`margin`](../api/linear-gauge/marginModel/) property.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge :margin ='margin' >
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
             margin: { left: 40, right: 40, top: 40, bottom: 40 }
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

## Gauge Title

You can give the title using [`title`](../api/linear-gauge/linearGaugeModel/#title-string) property to show the information about the linear gauge. Its appearance can be customized by using the [`titleStyle`](../api/linear-gauge/linearGaugeModel/#titlestyle-fontmodel) property.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge :title ='title' :titleStyle ='titleStyle' >
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
        title: 'linear gauge',
        titleStyle: {
            fontFamily: "Arial",
            fontStyle: 'italic',
            fontWeight: 'regular',
            color: "#E27F2D",
            size: '23px'
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

## Gauge Container

The area used to render the ranges and pointers at the center position of the gauge is called [`container`](../api/linear-gauge/containerModel/). It can be customized by using [`type`](../api/linear-gauge/containerModel/#type-string), [`offset`](../api/linear-gauge/containerModel/#offset-number), [`width`](../api/linear-gauge/containerModel/#width-number), [`height`](../api/linear-gauge/containerModel/#height-number) and [`backgroundColor`](../api/linear-gauge/containerModel/#backgroundcolor-string) properties in [`container`](../api/linear-gauge/containerModel/). It is of three types namely,

* Normal
* Rounded Rectangle
* Thermometer

### Normal

The normal type will render the container as rectangle and this is the default container type.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge :container='container' >
    <e-axes>
      <e-axis >
        <e-pointers>
           <e-pointer value= 50 width= 15 type= 'Bar' ></e-pointer>
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
            container: {
               height: 300,
               width: 30
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

### Rounded Rectangle s

The rounded rectangle type will render the container as rectangle with rounded corners.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge :container='container' >
    <e-axes>
      <e-axis >
        <e-pointers>
           <e-pointer value= 50  type= 'Bar' ></e-pointer>
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
            container: {
               height: 300,
               width: 30,
               type: 'RoundedRectangle'
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

### Thermometer

This type is used to render the container similar to the thermometer appearance.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge :container='container' >
    <e-axes>
      <e-axis >
        <e-pointers>
           <e-pointer value= 50  type= 'Bar' ></e-pointer>
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
            container: {
               height: 300,
               width: 30,
               type: 'Thermometer'
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