---
title: "Autocomplete autofill"
component: "AutoComplete"
description: "This section explains how to acheive autofill functionality in autocomplete control."
---

# Autofill supported with AutoComplete

The AutoComplete supports the autofill behavior with the help of [`autofill`](../../api/auto-complete/#autofill) property.
Whenever you change the input value, the AutoComplete will autocomplete your data by
matching the typed character. Suppose, if no matches found then, AutoComplete doesn't
suggest any item.

In the below sample, showcase that how to work autofill with AutoComplete.

{% tab template="auto-complete/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <ejs-autocomplete :autofill='autofill' :dataSource='searchData' :fields='fields' :placeholder="waterMark" ></ejs-autocomplete>
  </div>
</template>
<script>
import Vue from 'vue';
import { AutoCompletePlugin } from '@syncfusion/ej2-vue-dropdowns';

Vue.use(AutoCompletePlugin);
export default {
  name: 'app',
   data () {
    return {
      waterMark : 'Find a country',
      searchData: [
           { Name: 'Australia', Code: 'AU' },
    { Name: 'Bermuda', Code: 'BM' },
    { Name: 'Canada', Code: 'CA' },
    { Name: 'Cameroon', Code: 'CM' },
    { Name: 'Denmark', Code: 'DK' },
    { Name: 'France', Code: 'FR' },
    { Name: 'Finland', Code: 'FI' },
    { Name: 'Germany', Code: 'DE' },
    { Name: 'Greenland', Code: 'GL' },
    { Name: 'Hong Kong', Code: 'HK' },
    { Name: 'India', Code: 'IN' },
    { Name: 'Italy', Code: 'IT' },
    { Name: 'Japan', Code: 'JP' },
    { Name: 'Mexico', Code: 'MX' },
    { Name: 'Norway', Code: 'NO' },
    { Name: 'Poland', Code: 'PL' },
    { Name: 'Switzerland', Code: 'CH' },
    { Name: 'United Kingdom', Code: 'GB' },
    { Name: 'United States', Code: 'US' }
            ],
            fields: { value: 'Name' },
            autofill: true
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  #app {
    color: #008cff;
    height: 40px;
    left: 35%;
    position: absolute;
    top: 15%;
    width: 30%;
  }
</style>
```

{% endtab %}