---
title: "Getting Started"
component: "NumericTextBox"
description: "Rendering numeric textbox using VuejS"
---

# Getting Started

The following section explains the required steps to build the
NumericTextBox component with its basic usage in step by step procedure.

## Installation and configuration

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your vue applications.
To install Vue CLI use the following command.

```bash
npm install -g @vue/cli
```

Start a new project using below Vue CLI command.

```bash
vue init webpack-simple quickstart
cd quickstart
npm install

```

## Adding syncfusion packages

All the available Essential JS 2 packages are published in
[`npmjs.com`](https://www.npmjs.com/~syncfusionorg) public registry.
You can choose the component that you want to install.

To install NumericTextBox component, use the following command

```bash
npm install @syncfusion/ej2-vue-inputs –save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.
* Vue.use()
* Vue.component()

### Using Vue.use()

Import the NumericTextBox Component Plugin from the EJ2 Vue Package and register the same using
Vue.use() with NumericTextBox Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { NumericTextBoxPlugin } from "@syncfusion/ej2-vue-inputs";

Vue.use(NumericTextBoxPlugin);
```

> By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the NumericTextBox Component and NumericTextBox Component Plugin from EJ2 Vue Package,
register the same using the Vue.component() with name of NumericTextBox Component from NumericTextBox Component Plugin
and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { NumericTextBoxComponent, NumericTextBoxPlugin } from '@syncfusion/ej2-vue-inputs';

Vue.component(NumericTextBoxPlugin.name, NumericTextBoxComponent);
```

> By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Adding NumericTextBox component

Add the EJ2 Vue NumericTextBox using `<ejs-numerictextbox>` to the `<template>` section of the `App.vue` file in src directory,
the content attribute of the NumericTextBox component is provided as name in data option in the `<script>` section.

```html
<template>
    <div class="control_wrapper">
        <div class="control-label">Numeric TextBox
        </div>
        <ejs-numerictextbox value="10"></ejs-numerictextbox>
    </div>
</template>
<script>
import Vue from "vue";
import { NumericTextBoxPlugin } from "@syncfusion/ej2-vue-inputs";

Vue.use(NumericTextBoxPlugin);
export default Vue.extend ({});

</script>
```

## Adding CSS Reference

Add Button component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
</style>
```

> If you want to refer the combined component styles, please make use of our [`CRG`](https://ej2crg.azurewebsites.net/) (Custom Resource Generator) in your application.

## Run the application

Now use the `npm run dev` command to run the application in the browser.

```cmd
npm run dev
```

The below example shows the NumericTextBox.

{% tab template="numeric-textbox/getting-started/getting-started", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
    <div class='wrap'>
        <ejs-numerictextbox value="10"></ejs-numerictextbox>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import { NumericTextBoxPlugin } from "@syncfusion/ej2-vue-inputs";

Vue.use(NumericTextBoxPlugin);
export default {
  data () {
    return {
    }
  }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
 .wrap {
    margin: 0 auto;
    width: 240px;
}
</style>
```

{% endtab %}

## Range validation

You can set the minimum and maximum range of values in the NumericTextBox using the [`min`](../api/numerictextbox#min) and
[`max`](../api/numerictextbox#max) properties, so the numeric value should be in the min and max range.

The validation behavior depends on the [`strictMode`](../api/numerictextbox#strictmode) property.

{% tab template="numeric-textbox/getting-started/range-validation", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
    <div class='wrap'>
        <ejs-numerictextbox id="numeric" ref="numeric_instance" :value="value" :step="step" :min="min" :max="max"></ejs-numerictextbox>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import { NumericTextBoxPlugin } from "@syncfusion/ej2-vue-inputs";

Vue.use(NumericTextBoxPlugin);
export default {
  data () {
    return {
        min: 1,
        max: 100,
        value: 30,
        step: 2
    }
  }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
 .wrap {
    margin: 0 auto;
    width: 240px;
}
</style>
```

{% endtab %}

## Formatting the value

User can set the format of the NumericTextBox component using [`format`](../api/numerictextbox#format)
property. The value will be displayed in the specified format, when the component is in focused out state. For more information about
formatting the value, refer to this [link](./formats/).

The below example demonstrates format the value by using currency format value `c2`.

{% tab template="numeric-textbox/getting-started/formating-value", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
    <div class='wrap'>
        <ejs-numerictextbox id="numeric" ref="numeric_instance" :format="format" :value="value"></ejs-numerictextbox>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import { NumericTextBoxPlugin } from "@syncfusion/ej2-vue-inputs";

Vue.use(NumericTextBoxPlugin);
export default {
  data () {
    return {
       format: 'c2',
        // sets value to the NumericTextBox
        value: 10
    }
  }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
 .wrap {
    margin: 0 auto;
    width: 240px;
}
</style>
```

{% endtab %}

## Precision of numbers

You can restrict the number of decimals to be entered in the NumericTextBox by using the [`decimals`](../api/numerictextbox#decimals)
and [`validateDecimalOnType`](../api/numerictextbox#validatedecimalontype) properties.
So, you can't enter the number whose precision is greater than the mentioned decimals.

* If `validateDecimalOnType` is false, number of decimals will not be restricted.
Else, number of decimals will be restricted while typing in the NumericTextBox.

{% tab template="numeric-textbox/getting-started/precision-numbers", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-numerictextbox id="strict" :validateDecimalOnType='true' placeholder="ValidateDecimalOnType enabled" floatLabelType="Auto" format='n3' :value="value" :decimals="decimals"></ejs-numerictextbox>
        </div>
        <div class='wrap'>
           <ejs-numerictextbox id="allow" placeholder="ValidateDecimalOnType disabled" floatLabelType="Auto" format='n3' :value="value" :decimals="decimals"></ejs-numerictextbox>
        </div>
  </div>
</template>
<script>
import Vue from "vue";
import { NumericTextBoxPlugin } from "@syncfusion/ej2-vue-inputs";

Vue.use(NumericTextBoxPlugin);
export default {
  data () {
    return {
        // sets number of decimal places to be allowed by the NumericTextBox
        decimals: 3,
        value: 10,
    }
  }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
 .wrap {
    margin: 35px auto;
    width: 240px;
}
</style>
```

{% endtab %}

## Model binding

In NumericTextBox, the `value` property supports model binding functionality.
The below example demonstrates model binding functionality with the NumericTextBox and HTML input element.

{% tab template="numeric-textbox/getting-started/model", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
  <div class='wrap'>
        <div class='e-input-group' style='margin-bottom:30px'>
        <input class='e-input' type='text' v-model='value' placeholder='Enter a number'  />
        </div>
           <ejs-numerictextbox v-model="value" :value="value"></ejs-numerictextbox>
        </div>
  </div>
  </div>
</template>
<script>
import Vue from "vue";
import { NumericTextBoxPlugin } from "@syncfusion/ej2-vue-inputs";

Vue.use(NumericTextBoxPlugin);
export default {
  data () {
    return {
      value : 10
    }
  }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
 .wrap {
  margin: 35px auto;
  width: 240px;
}
</style>
```

{% endtab %}

## See Also

* [How to perform custom validation using FormValidator](./how-to/perform-custom-validation-using-form-validator/)
* [How to customize the UI appearance of the control](./how-to/customize-the-ui-appearance-of-the-control/)
* [How to customize the spin button’s up and down arrow](./how-to/customize-the-spin-buttons-up-and-down-arrow/)
* [How to customize the step value and hide spin buttons](./how-to/customize-the-step-value-and-hide-spin-buttons/)
* [How to prevent nullable input in NumericTextBox](./how-to/prevent-nullable-input-in-numerictextbox/)
* [How to maintain trailing zeros in NumericTextBox](./how-to/maintain-trailing-zeros-in-numerictextbox/)
