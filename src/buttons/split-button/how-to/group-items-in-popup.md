---
title: "Group items in Popup"
component: "SplitButton"
description: "Vue SplitButton how to section, group popup items using list view component, dialog open on popup item click."
---

# Group items in Popup

Grouped items are possible in SplitButton by templating entire popup with ListView. Check ListView [`grouping`](../../listview/grouping#grouping) and create such items. Create ListView with id `listview` and provide element of the ListView as target of SplitButton to render it in popup area.

Install Syncfusion `List` packages using below command.

```bash
npm install @syncfusion/ej2-vue-list --save
```

In this following example, ListView is created and its element is set as [`target`](../../api/split-button#target) for SplitButton.

{% tab template="split-button/default" %}

```html
<template>
<div>
    <ejs-splitbutton target='#listview'>ClipBoard</ejs-splitbutton>
    <ejs-listview id='listview' :dataSource='items' :fields='fields' sortOrder='Descending'>
    </ejs-listview>
</div>
</template>

<script>
import Vue from 'vue';
import { SplitButtonPlugin } from "@syncfusion/ej2-vue-splitbuttons";
import { ListViewPlugin } from '@syncfusion/ej2-vue-lists';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(SplitButtonPlugin);
Vue.use(ListViewPlugin);

export default {
    data () {
        return {
            items:[
            {
                'text': 'Cut',
                'category': 'Basic'
            },
            {
                'text': 'Copy',
                'category': 'Basic'
            },
            {
                'text': 'Paste',
                'category': 'Basic'
            },
            {
                'text': 'Paste as Formula',
                'category': 'Advanced'
            },
            {
                'text': 'Paste as Hyperlink',
                'category': 'Advanced'
            }],
            fields: { groupBy: 'category' }
        };
    }
}
</script>

<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-lists/styles/material.css';
  .e-split-btn-wrapper{
   margin: 20px 20px 5px 5px;
  }
</style>
```

{% endtab %}