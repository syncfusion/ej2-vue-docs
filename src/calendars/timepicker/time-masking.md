---
title: "Time masking"
component: "TimePicker"
description: "Miscellaneous aspects of customizing the TimePicker"
---

# Enable the Masked Input

The TimePicker has built-in support to masking the time value, when `enableMask` property set as `true`.

To use mask support, inject the MaskedDateTime module in the TimePicker.

{% tab template="timepicker/mask-module", isDefaultActive = "true", sourceFiles="app/**/*.ts" %}

```typescript

<template>
<div id="app">
        <div class='wrapper'>
         <ejs-timepicker id="timepicker" :enableMask="mask"></ejs-timepicker>
     </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DateTimePickerPlugin, MaskedDateTime } from "@syncfusion/ej2-vue-calendars";

Vue.use(DateTimePickerPlugin);
export default Vue.extend({
  data: function() {
    return {
      mask: true
    };
  },
  provide: {
      timepicker: [MaskedDateTime]
  }  
});
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  .wrapper {
    max-width: 250px;
    margin: 0 auto;
  }
</style>

```

{% endtab %}

The mask pattern is defined based on the provided time format to the component. If the format is not specified, the mask pattern is formed based on the default format of the current culture.

The selected portions of date and time co-ordinates  can  be incremented and decremented using the Up/Down arrow keys. You can also use Right/Left arrow keys to navigate from one segment to another.

The following example demonstrates default and custom format of TimePicker component with mask module.

{% tab template="timepicker/mask-module", isDefaultActive = "true", sourceFiles="app/**/*.ts,app/**/format.html,styles.css" %}

```typescript

<template>
<div id="app">
        <div class='wrapper1'>
         // Specifies the masked timepicker without format property.
         <ejs-timepicker id="timepicker" :enableMask="mask" ></ejs-timepicker>
     </div>
     <div class='wrapper2'>
          // Specifies the masked timepicker with format property.
         <ejs-timepicker id="timepicker" :enableMask="mask" :format="dateFormat"></ejs-timepicker>
     </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DateTimePickerPlugin, MaskedDateTime } from "@syncfusion/ej2-vue-calendars";

Vue.use(DateTimePickerPlugin);
export default Vue.extend({
  data: function() {
    return {
      mask: true,
      dateFormat: 'hh:mm a'
    };
  },
  provide: {
      timepicker: [MaskedDateTime]
  }  
});
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
#wrapper1{
  min-width: 250px;
    float: left;
    margin-left: 100px;
}
#wrapper2{
  min-width: 250px;
    float: right;
     margin-right: 100px;
}
</style>
```

{% endtab %}

# Configure Mask Placeholder

You can change mask placeholder value through property `maskPlaceholder`. By default , it takes the full name of  time co-ordinates such as `hour`, `minute` and `second`.

The following example demonstrates default and customized mask placeholder value.

{% tab template="timepicker/mask-module", isDefaultActive = "true", sourceFiles="app/**/*.ts,app/**/maskplaceholder.html,styles.css" %}

```typescript

<template>
<div id="app">
        <div class='wrapper1'>
         // Specifies the masked timepicker without format property.
         <ejs-timepicker id="timepicker" :enableMask="mask" ></ejs-timepicker>
     </div>
     <div class='wrapper2'>
          // Specifies the masked timepicker with format property.
         <ejs-timepicker id="timepicker" :enableMask="mask" :maskPlaceholder="maskPlaceholderValue"></ejs-timepicker>
     </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DateTimePickerPlugin, MaskedDateTime } from "@syncfusion/ej2-vue-calendars";

Vue.use(DateTimePickerPlugin);
export default Vue.extend({
  data: function() {
    return {
      mask: true,
      maskPlaceholderValue: { hour: 'h', minute: 'm', second: 's' }
    };
  },
  provide: {
      timepicker: [MaskedDateTime]
  }  
});
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
#wrapper1{
  min-width: 250px;
    float: left;
    margin-left: 100px;
}
#wrapper2{
  min-width: 250px;
  float: right;
  margin-right: 100px;
}
</style>
```

{% endtab %}
