---
title: "Name and Value in form submit"
component: "CheckBox"
description: "Vue CheckBox how to section, name and value in form submit, and customization of CheckBox appearance, frame & check icon."
---

# Name and Value in form submit

The [`name`](../../api/check-box#name) attribute of the CheckBox is used to group Checkboxes. When the Checkboxes are grouped in form, the checked items [`value`](../../api/check-box#value) attribute
will post to the server on form submit that can be retrieved through the name. The disabled and unchecked CheckBox
value will not be sent to the server on form submit.

In the following code snippet, Cricket and Hockey are in the [`checked`](../../api/check-box#checked) state, Tennis is in [`disabled`](../../api/check-box#disabled) state and Basketball is in unchecked state.
Now, the value that is in checked state only be sent on form submit.

{% tab template= "check-box/default", isDefaultActive=true %}

```html
<template>
<form>
<ul>
<li><ejs-checkbox name='Sport' value='Cricket' label='Cricket' checked=true></ejs-checkbox></li>
<li><ejs-checkbox name='Sport' value='Hockey' label='Hockey' checked=true></ejs-checkbox></li>
<li><ejs-checkbox name='Sport' value='Tennis' label='Tennis' disabled=true></ejs-checkbox></li>
<li><ejs-checkbox name='Sport' value='Basketball' label='Basketball'></ejs-checkbox></li>
<li><ejs-button isPrimary=true>Submit</ejs-button></li>
</ul>
</form>
</template>

<script>
import Vue from 'vue';
import { CheckBoxPlugin, ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(CheckBoxPlugin);
Vue.use(ButtonPlugin);

export default {}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';

.e-checkbox-wrapper {
  margin-top: 18px;
}

button {
  margin: 20px 0 0 5px;
}

li {
  list-style: none;
}
</style>
```

{% endtab %}