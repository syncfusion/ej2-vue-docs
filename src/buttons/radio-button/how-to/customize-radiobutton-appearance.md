---
title: "Customize RadioButton Appearance"
component: "RadioButton"
description: "Vue RadioButton how to section, name and value in form submit, customize RadioButton appearance."
---

# Customize RadioButton Appearance

You can customize the appearance of the RadioButton component by using the CSS rules.
Define own CSS rules according to your requirement and assign the class name to the [`cssClass`](../../api/radio-button#cssclass) property.

The background and border color of the RadioButton is customized through the custom classes to
create the primary, success, info, warning, and danger type of RadioButton.

{% tab template= "radio-button/default" %}

```html
<template>
<ul>
<li> <ejs-radiobutton label="Primary" name="custom" cssClass="e-primary"></ejs-radiobutton></li>
<li> <ejs-radiobutton label="Success" name="custom" cssClass="e-success"></ejs-radiobutton></li>
<li> <ejs-radiobutton label="Info" name="custom" cssClass="e-info"></ejs-radiobutton></li>
<li> <ejs-radiobutton label="Warning" name="custom" cssClass="e-warning"></ejs-radiobutton></li>
<li> <ejs-radiobutton label="Danger" name="custom" cssClass="e-danger"></ejs-radiobutton></li>
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

.e-radio:checked + .e-success::after { /* csslint allow: adjoining-classes */
  background-color: #689f38;
  border-color: #689f38;
}

.e-radio:checked:focus + .e-success::after, .e-radio:checked + .e-success:hover::after { /* csslint allow: adjoining-classes */
  background-color: #449d44;
  border-color: #449d44;
}

.e-radio:checked + .e-success::before {
  border-color: #689f38;
}

.e-radio:checked:focus + .e-success::before, .e-radio:checked + .e-success:hover::before { /* csslint allow: adjoining-classes */
  border-color: #449d44;
}

.e-radio +.e-success:hover::before {
  border-color: #b1afaf
}
.e-radio:checked + .e-info::after { /* csslint allow: adjoining-classes */
  background-color: #2196f3;
  border-color: #2196f3;
}

.e-radio:checked:focus + .e-info::after, .e-radio:checked + .e-info:hover::after { /* csslint allow: adjoining-classes */
  background-color: #0b7dda;
  border-color: #0b7dda;
}

.e-radio:checked + .e-info::before {
  border-color: #2196f3;
}

.e-radio:checked:focus + .e-info::before, .e-radio:checked + .e-info:hover::before {
  border-color: #0b7dda;
}

.e-radio + .e-info:hover::before {
  border-color: #b1afaf
}

.e-radio:checked + .e-warning::after { /* csslint allow: adjoining-classes */
  background-color: #ef6c00;
  border-color: #ef6c00;
}

.e-radio:checked:focus + .e-warning::after, .e-radio:checked + .e-warning:hover::after { /* csslint allow: adjoining-classes */
  background-color: #cc5c00;
}

.e-radio:checked + .e-warning::before {
  border-color: #ef6c00;
}

.e-radio:checked:focus + .e-warning::before, .e-radio:checked + .e-warning:hover::before {
  border-color: #cc5c00;
}

.e-radio + .e-warning:hover::before {
  border-color: #b1afaf
}

.e-radio:checked + .e-danger::after { /* csslint allow: adjoining-classes */
  background-color: #d84315;
  border-color: #d84315;
}
.e-radio:checked:focus + .e-danger::after, .e-radio:checked + .e-danger:hover::after { /* csslint allow: adjoining-classes */
  background-color: #ba330a;
  border-color: #ba330a;
}

.e-radio:checked + .e-danger::before {
  border-color: #d84315;
}

.e-radio:checked:focus + .e-danger::before, .e-radio:checked + .e-danger:hover::before {
  border-color: #ba330a;
}

.e-radio + .e-danger:hover::before {
  border-color: #b1afaf
}
</style>
```

{% endtab %}