---
title: "Date and Time masking"
component: "DateTimePicker"
description: "Miscellaneous aspects of customizing the datetimepicker"
---

# Enable the Masked Input

DateTimePicker has `enableMask` property that provides the option to enable the built-in date masking support. Also, you must inject the MaskedDateTime module to enable the masking support.

{% tab template="datetimepicker/mask-module", isDefaultActive = "true", sourceFiles="app/**/*.ts" %}

```typescript

<template>
<div id="app">
        <div class='wrapper'>
        <ejs-datetimepicker id="datetimepicker" :enableMask="true"></ejs-datetimepicker>
     </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DateTimePickerPlugin, DateTimePicker, MaskedDateTime } from "@syncfusion/ej2-vue-calendars";

DateTimePicker.Inject(MaskedDateTime)
Vue.use(DateTimePickerPlugin);
export default Vue.extend({
  data: function() {
    return {
    };
  },
  provide: {
      datetimepicker: [MaskedDateTime]
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

The mask pattern is defined based on the provided date format to the component. If the format is not specified, the mask pattern is formed based on the default format of the current culture.

| **Keys** | **Actions** |
| --- | --- |
| <kbd>Up / Down arrows</kbd> | To increment and decrement the selected portion of the date and time. |
| <kbd>Left / Right arrows and Tab</kbd> | To navigate the selection from one portion to next portion |

The following example demonstrates default and custom format of DateTimePicker component with mask.

{% tab template="datetimepicker/mask-module", isDefaultActive = "true", sourceFiles="app/**/*.ts,app/**/format.html,styles.css" %}

```typescript

<template>
<div id="app">
      <div class='wrapper1'>
        <!-- Specifies the masked datetimepicker without format property. -->
        <ejs-datetimepicker id="datetimepicker" :enableMask="true" ></ejs-datetimepicker>
     </div>
     <div class='wrapper2'>
        <!-- Specifies the masked datetimepicker with format property. -->
        <ejs-datetimepicker id="datetimepicker" :enableMask="true" :format='dateFormat'></ejs-datetimepicker>
     </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DateTimePickerPlugin, DateTimePicker, MaskedDateTime } from "@syncfusion/ej2-vue-calendars";

DateTimePicker.Inject(MaskedDateTime)
Vue.use(DateTimePickerPlugin);
export default Vue.extend({
  data: function() {
    return {
      dateFormat: 'M/d/yyyy hh:mm a'
    };
  },
  provide: {
      datetimepicker: [MaskedDateTime]
  }  
});
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
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

You can change mask placeholder value through property `maskPlaceholder`. By default , it takes the full name of date and time co-ordinates such as `day`, `month`, `year`, `hour` etc.

While changing to a culture other than `English`, ensure that locale text for the concerned culture is loaded through load method of L10n class for mask placeholder values like below.

```typescript
//Load the L10n from ej2-base
import { L10n } from '@syncfusion/ej2-base';

//load the locale object to set the localized mask placeholder value
L10n.load({
'de': {
    'datetimepicker': { day: 'Tag' , month: 'Monat', year: 'Jahr', hour: 'Stunde' ,minute: 'Minute', second:'Sekunden' }
}
});

```

The following example demonstrates default and customized mask placeholder value.

{% tab template="datetimepicker/mask-module", isDefaultActive = "true", sourceFiles="app/**/*.ts,app/**/maskplaceholder.html,styles.css" %}

```typescript

<template>
<div id="app">
        <div class='wrapper1'>
         <!-- Specifies the masked datetimepicker without mask placeholder. -->
         <ejs-datetimepicker id="datetimepicker" :enableMask="true" ></ejs-datetimepicker>
     </div>
     <div class='wrapper2'>
          <!-- Specifies the masked datetimepicker with mask placeholder. -->
         <ejs-datetimepicker id="placeholder" :enableMask="true" :maskPlaceholder='maskPlaceholderValue'></ejs-datetimepicker>
     </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DateTimePickerPlugin, DateTimePicker, MaskedDateTime } from "@syncfusion/ej2-vue-calendars";

DateTimePicker.Inject(MaskedDateTime)
Vue.use(DateTimePickerPlugin);
export default Vue.extend({
  data: function() {
    return {
      maskPlaceholderValue: {day: 'd', month: 'M', year: 'y', hour: 'h', minute: 'm', second: 's'}
    };
  },
  provide: {
      datetimepicker: [MaskedDateTime]
  }  
});
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
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
