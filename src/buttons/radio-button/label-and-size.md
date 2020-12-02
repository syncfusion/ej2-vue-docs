---
title: "RadioButton Label and Size"
component: "RadioButton"
description: "Vue RadioButton component supports different sizes and label."
---

# Label and Size

This section explains the different sizes and labels.

## Label

RadioButton caption can be defined by using the [`label`](../api/radio-button#label) property.
This reduces the manual addition of label for RadioButton. You can customize the label position before or after the RadioButton through the
[`labelPosition`](../api/radio-button#labelposition) property.

{% tab template= "radio-button/default", isDefaultActive=true %}

```html
<template>
<ul>
<li> <ejs-radiobutton label="Left Side Label" name="position" labelPosition="Before"></ejs-radiobutton></li>
<li> <ejs-radiobutton label="Right Side Label" name="position" checked="true"></ejs-radiobutton></li>
</ul>
</template>

<script>
import Vue from 'vue';
import { RadioButtonPlugin } from '@syncfusion/ej2-vue-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(RadioButtonPlugin);

export default {}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';

.e-radio-wrapper {
  margin-top: 18px;
}

li {
  list-style: none;
}
</style>
```

{% endtab %}

## Size

The different RadioButton sizes available are default and small. To reduce the size of default RadioButton to small, set the [`cssClass`](../api/radio-button#cssclass)
property to `e-small`.

{% tab template= "radio-button/default" %}

```html
<template>
<ul>
<li> <ejs-radiobutton label="Small" name="size" checked="true" cssClass="e-small"></ejs-radiobutton></li>
<li> <ejs-radiobutton label="Default" name="size"></ejs-radiobutton></li>
</ul>
</template>

<script>
import Vue from 'vue';
import { RadioButtonPlugin } from '@syncfusion/ej2-vue-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(RadioButtonPlugin);

export default {}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';

.e-radio-wrapper {
  margin-top: 18px;
}

li {
  list-style: none;
}
</style>
```

{% endtab %}

## See Also

* [How to customize the RadioButton appearance](./how-to/customize-radiobutton-appearance)