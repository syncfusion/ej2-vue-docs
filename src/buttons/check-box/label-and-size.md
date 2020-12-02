---
title: "CheckBox Label and Size"
component: "CheckBox"
description: "Vue CheckBox component supports different sizes and label."
---

# Label and Size

This section explains the different sizes and labels.

## Label

The CheckBox caption can be defined by using the [`label`](../api/check-box#label) property.
This reduces the manual addition of label for CheckBox. You can customize the label position before or after the CheckBox
through the [`labelPosition`](../api/check-box#labelposition) property.

{% tab template= "check-box/default", isDefaultActive=true %}

```html
<template>
<ul>
<li><ejs-checkbox label='Left Side Label' labelPosition='Before'></ejs-checkbox></li>
<li><ejs-checkbox label='Right Side Label' checked=true></ejs-checkbox></li>
</ul>
</template>

<script>
import Vue from 'vue';
import { CheckBoxPlugin } from '@syncfusion/ej2-vue-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(CheckBoxPlugin);

export default {}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';

.e-checkbox-wrapper {
  margin-top: 18px;
}

li {
  list-style: none;
}
</style>
```

{% endtab %}

## Size

The different CheckBox sizes available are default and small. To reduce the size of default CheckBox to small,
set the [`cssClass`](../api/check-box#cssclass) property to `e-small`.

{% tab template= "check-box/default" %}

```html
<template>
<ul>
<li><ejs-checkbox label='Small' cssClass='e-small'></ejs-checkbox></li>
<li><ejs-checkbox label='Default'></ejs-checkbox></li>
</ul>
</template>

<script>
import Vue from 'vue';
import { CheckBoxPlugin } from '@syncfusion/ej2-vue-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(CheckBoxPlugin);

export default {}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';

.e-checkbox-wrapper {
  margin-top: 18px;
}

li {
  list-style: none;
}
</style>
```

{% endtab %}

## See Also

* [CheckBox customization](./how-to/customized-checkbox)