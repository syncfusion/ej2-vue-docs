---
title: "Getting Started"
component: "BarcodeGenerator"
description: "BarcodeGenerator component is a pure JavaScript library which will convert a string to Barcode and show it to the user. This supports major 1D and 2D barcodes including coda bar, code 128, QR Code."
---

# Getting started

This section explains the steps required to create a simple barcode and demonstrates the basic usage of the barcode generator control.

## Dependencies

The following list of dependencies are required to use the `Barcode Generator` component in your application.

```javascript
|-- @syncfusion/ej2-vue-barcode-generator
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-navigations
    |-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-popups
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-lists
    |-- @syncfusion/ej2-splitbuttons
    |-- @syncfusion/ej2-barcode-generator
    |-- @syncfusion/ej2-vue-base
```

## Get Started with Vue CLI

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your vue applications.
To install Vue CLI use the following command.

```bash
npm install -g @vue/cli
npm install -g @vue/cli-init
```

Start a new project using below Vue CLI command.

```bash
vue init webpack-simple quickstart

cd quickstart
npm install

```

## Adding Syncfusion packages

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.
You can choose the component that you want to install. For this application, we are going to use Barcode Generator component.

To install Barcode Generator component, use the following command

```bash
npm install @syncfusion/ej2-vue-barcode-generator –save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.
* Vue.use()
* Vue.component()

### Using Vue.use()

Import the Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { BarcodeGeneratorPlugin } from '@syncfuion/ej2-vue-barcode-generator';

Vue.use(BarcodeGeneratorPlugin);
```

Note : By Registering Component Plugin in Vue, all child directives are also globally registered.

## Adding Barcode Generator control

You can add the QR code in our barcode generator component.

{% tab template="barcode/getting-started/initialize", isDefaultActive=true %}

```html
<template>
    <div id="app" class="barcodeStyle">
        <ejs-barcodegenerator
              id="barcode"
              ref="barcodeControl"
              :width="width"
              :height="height"
              :type="type"
              :value="value"
              :mode="mode"
            ></ejs-barcodegenerator>

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
import { BarcodeGeneratorPlugin } from '@syncfusion/ej2-vue-barcode-generator';

Vue.use(BarcodeGeneratorPlugin);
export default {
    name: 'app'
    data () {
        return {
            width: "200px",
            height: "150px",
            type: "Codabar",
            value: "123456789",
            mode: "SVG",
        }
    }
}
</script>
```

{% endtab %}

## Adding QR Generator control

You can add the QR code in our barcode generator component.

{% tab template="barcode/getting-started/qrcode", isDefaultActive=true %}

```html
<template>
    <div id="app" class="barcodeStyle">
        <ejs-qrcodegenerator
              id="barcode"
              ref="barcodeControl"
              :width="width"
              :height="height"
              :value="value"
              :mode="mode"
            ></ejs-qrcodegenerator>


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
import { QRCodeGeneratorPlugin } from '@syncfusion/ej2-vue-barcode-generator';

Vue.use(QRCodeGeneratorPlugin);
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

## Adding Datamatrix Generator control

You can add the datamatrix code in our barcode generator component.

{% tab template="barcode/getting-started/datamatrix", isDefaultActive=true %}

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