---
title: "Customize icon and width"
component: "DropDownButton"
description: "Vue DropDownButton how to section, hide drop down arrow, group popup items using list view component, dialog open on popup item click."
---

# Customize icon and width

Width of the DropDownButton can be customized by setting required width to the dropdown element.

The following UI can be achieved by setting [`iconPosition`](https://ej2.syncfusion.com/vue/documentation/api/drop-down-button/dropDownButtonModel/#iconposition) as `Top`, width as `85px` and size of the
font icon as `40px` by adding `e-custom` class.

{% tab template="drop-down-button/default", isDefaultActive=true %}

```html
<template>
<ejs-dropdownbutton :items='items' iconCss='e-icons e-search' cssClass='e-custom' iconPosition='Top'      content='Find & Select'></ejs-dropdownbutton>
</template>

<script>
import Vue from 'vue';
import { DropDownButtonPlugin } from "@syncfusion/ej2-vue-splitbuttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(DropDownButtonPlugin);

export default {
    data () {
        return {
            items:[
            {
                text: 'Find'
            },
            {
                text: 'Replace'
            },
            {
                text: 'Go To'
            },
            {
                text: 'Go To Special'
            }]
        };
    }
}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
    .e-search::before {
    content: '\e993';
    }

    .e-dropdown-btn.e-custom {
    width: 85px;
    }

    .e-dropdown-btn.e-custom .e-search::before {
    font-size: 40px;
    }
</style>
```

{% endtab %}