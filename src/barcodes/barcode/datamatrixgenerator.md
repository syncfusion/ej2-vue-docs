---
title: "Data Matrix generator"
component: "BarcodeGenerator"
description: "BarcodeGenerator component is a pure JavaScript library which will convert a string to Barcode and show it to the user. This supports major 1D and 2D barcodes including coda bar, code 128, QR Code."
---

# Data Matrix generator

# Data Matrix

DataMatrix Barcode is a two dimensional barcode that consists of a grid of dark and light dots or blocks forming square or rectangular symbol. The data encoded in the barcode can either be numbers or alphanumeric. They are widely used in printed media such as labels and letters. You can read it easily with the help of a barcode reader and mobile phones.

{% tab template="barcode/datamatrix/datamatrix", isDefaultActive=true %}

```html
<template>
    <div id="app" class="barcodeStyle">
        <ejs-datamatrixgenerator
              id="barcode"
              ref="barcodeControl"
              :width="width"
              :height="height"
              :value="value"
              :mode="mode"
            ></ejs-datamatrixgenerator>
</div>
</template>
<style>
    .barcodeStyle {
            height: 150px;
            width: 200px;
            padding-left: 40%;
            padding-top: 9%;
        }
</style>
<script>
import Vue from 'vue';
import { DataMatrixGeneratorPlugin } from '@syncfusion/ej2-vue-barcode-generator';

Vue.use(DataMatrixGeneratorPlugin);
export default {
    name: 'app'
    data () {
        return {
             width: "200px",
             height: "150px",
             mode: "SVG",
             value: "Syncfusion",
        }
    }
}
</script>
```

{% endtab %}

## Customizing the Barcode color

A page or printed media with barcode often appears colorful in the background and surrounding region with other contents. In such cases the barcode can also be customized to suit the needs. You can achieve this by using the forecolor property .

{% tab template="barcode/datamatrix/color", isDefaultActive=true %}

```html
<template>
    <div id="app" class="barcodeStyle">
        <ejs-datamatrixgenerator
              id="barcode"
              ref="barcodeControl"
              :width="width"
              :height="height"
              :foreColor="foreColor"
              :value="value"
              :mode="mode"
            ></ejs-datamatrixgenerator>



    </div>
</template>
<style>
    .barcodeStyle {
            height: 150px;
            width: 200px;
            padding-left: 40%;
            padding-top: 9%;
        }
</style>
<script>
import Vue from 'vue';
import { DataMatrixGeneratorPlugin } from '@syncfusion/ej2-vue-barcode-generator';

Vue.use(DataMatrixGeneratorPlugin);
export default {
    name: 'app'
    data () {
        return {
             width: "200px",
             height: "150px",
             mode: "SVG",
             foreColor:"red"
             value: "Syncfusion",
        }
    }
}
</script>
```

{% endtab %}

## Customizing the Barcode dimension

The dimension of the barcode can be changed using the height and width property of the barcodegenerator.

{% tab template="barcode/datamatrix/dimension", isDefaultActive=true %}

```html
<template>
    <div id="app" class="barcodeStyle">
        <ejs-datamatrixgenerator
              id="barcode"
              ref="barcodeControl"
              :width="width"
              :height="height"
              :value="value"
              :mode="mode"
            ></ejs-datamatrixgenerator>



    </div>
</template>
<style>
    .barcodeStyle {
            height: 150px;
            width: 200px;
            padding-left: 40%;
            padding-top: 9%;
        }
</style>
<script>
import Vue from 'vue';
import { DataMatrixGeneratorPlugin } from '@syncfusion/ej2-vue-barcode-generator';

Vue.use(DataMatrixGeneratorPlugin);
export default {
    name: 'app'
    data () {
        return {
             width: "300px",
             height: "300px",
             mode: "SVG",
             foreColor:"red"
             value: "Syncfusion",
        }
    }
}
</script>
```

{% endtab %}

## Customizing the text

In barcode generators you can customize the barcode text by using the display text property .

{% tab template="barcode/datamatrix/text", isDefaultActive=true %}

```html
<template>
    <div id="app" class="barcodeStyle">
        <ejs-datamatrixgenerator
              id="barcode"
              ref="barcodeControl"
              :width="width"
              :height="height"
              :displayText="displaytext"
              :value="value"
              :mode="mode"
            ></ejs-datamatrixgenerator>



    </div>
</template>
<style>
    .barcodeStyle {
            height: 150px;
            width: 200px;
            padding-left: 40%;
            padding-top: 9%;
        }
</style>
<script>
import Vue from 'vue';
import { DataMatrixGeneratorPlugin } from '@syncfusion/ej2-vue-barcode-generator';

Vue.use(DataMatrixGeneratorPlugin);
export default {
    name: 'app'
    data () {
        return {
             width: "200px",
             height: "150px",
              displaytext: { text: 'text' },
             mode: "SVG",
             foreColor:"red"
             value: "Syncfusion",
        }
    }
}
</script>
```

{% endtab %}
