---
title: "Group popup items with ListView component"
component: "DropDownButton"
description: "Vue DropDownButton how to section, hide drop down arrow, group popup items using list view component, dialog open on popup item click."
---

# Group popup items with ListView component

Header in popup items is possible in DropdownButton by templating entire popup with ListView. Create ListView
with id `#listview` and provide it as a [`target`](../../api/drop-down-button#target) for DropDownButton.

Install Syncfusion `List` packages using below command.

```bash
npm install @syncfusion/ej2-vue-list --save
```

In the following example, ListView element is given as `target` to DropDownButton and header can be achieved
by [`groupBy`](https://ej2.syncfusion.com/vue/documentation/api/list-view/fieldSettingsModel/#groupby) property.

{% tab template="drop-down-button/default", isDefaultActive=true %}

```html
<template>
<div>
    <ejs-dropdownbutton target= '#listview' iconCss= 'e-icons e-down' cssClass= 'e-caret-hide'></ejs-dropdownbutton>
    <ejs-listview id='listview' :dataSource='dataSource' :fields='fields' showCheckBox= 'true'
    ></ejs-listview>
</div>
</template>

<script>
import Vue from 'vue';
import { DropDownButtonPlugin } from "@syncfusion/ej2-vue-splitbuttons";
import { ListViewPlugin } from '@syncfusion/ej2-vue-lists';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(DropDownButtonPlugin);
Vue.use(ListViewPlugin);

export default {
    data () {
        return {
            dataSource :[
                { class: 'data', text: 'Print', id: 'data1', category: 'Customize Quick Access Toolbar' },
                { class: 'data', text: 'Save As', id: 'data2', category: 'Customize Quick Access Toolbar' },
                { class: 'data', text: 'Update Folder', id: 'data3', category: 'Customize Quick Access Toolbar' },
                { class: 'data', text: 'Reply', id: 'data4', category: 'Customize Quick Access Toolbar' }
            ],
            fields: { text: 'text', groupBy: 'category' }
        }
    }
}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-lists/styles/material.css';
  .e-down::before {
    content: '\e969';
  }
</style>
```

{% endtab %}