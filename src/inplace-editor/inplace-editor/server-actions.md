---
title: "Server actions"
component: "In-place Editor"
description: "Learn how to modify and submit a value to the server, and handle success and failure events in the Essential JS 2 Vue In-place Editor component."
---

# Server actions

By passing In-place Editor component value to the server, the [primaryKey](../api/inplace-editor/#primarykey) property value must require, otherwise action not performed for remote data.

If the [URL](../api/inplace-editor/#url) property value is empty, data passing will handled at local and also the [actionSuccess](../api/inplace-editor/#actionsuccess) event will trigger with `null` as argument value.

> The following arguments are passed to the server when submit actions perform.

| Arguments  | Explanations                                              |
|------------|-----------------------------------------------------------|
| value      | For processing edited value, like DB value updating.      |
| primaryKey | For value mapping to the server, like selecting DB.            |
| name       | For field mapping to the server, like DB column field mapping. |

Find the following sample server codes for defining models and controller functions to configure processing data.

```C#
    public class SubmitModel
        {
            public string Name { get; set; }
            public string PrimaryKey { get; set; }
            public string Value { get; set; }
        }
```

```C#

public IEnumerable<SubmitModel> UpdateData([FromBody]SubmitModel value)
        {
         // User can process data
          return value;
        }

```

* Server actions successfully done, the [actionSuccess](../api/inplace-editor/#actionsuccess) event will be fired with returned server data.

* If the server is not responding, the [actionFailure](../api/inplace-editor/#actionfailure) event will be fired with data, but value not updated in the Editor.

In the following sample, the `actionSuccess` event will trigger once the value submitted successfully into the server. In this sample, both `actionSuccess` and `actionFailure` were configured and resulted value will be converted to chips.

{% tab template="in-place-editor/getting-started", isDefaultActive=true %}

```html
<template>
<div class="app">
    <table class="table-section">
        <tr>
            <td>Select frameworks </td>
            <td>
                <ejs-inplaceeditor ref="tagObj" id="inplace_tag_editor" data-underline='false' mode="Inline" type="MultiSelect" emptyText="Enter your tags" :url="serviceUrl" name='skill'  
                :value="multiValue" :model="selectModel" :actionSuccess= "onActionSuccess" :actionFailure = "onActionFailure" :popupSettings="tagPopupSettings"  adaptor='UrlAdaptor' primaryKey = "FrameWork">
                </ejs-inplaceeditor>
            </td>
        </tr>
    </table>
</div>
</template>

<script>

import Vue from 'vue';
import { InPlaceEditorPlugin, MultiSelect, ActionEventArgs } from "@syncfusion/ej2-vue-inplace-editor";
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(InPlaceEditorPlugin);
Vue.use(DropDownListPlugin);

export default {
  name: 'app',
      data () {
            let multiData = ['Android', 'JavaScript', 'jQuery', 'TypeScript', 'Angular', 'React', 'Vue', 'Ionic'];
        return {
             selectModel: {
            mode: 'Box',
            dataSource: multiData,
            placeholder: 'Enter your tags'
        },
        serviceUrl: 'https://ej2services.syncfusion.com/development/web-services/api/Editor/UpdateData',
            multiValue: ['TypeScript', 'JavaScript'],
    popupSettings: {
          model: { width: 300 }
        },
        tagPopupSettings: {
            model: { width: 'auto' }
        },
        };
    },
    mounted: function() {
   this.tagObj = this.$refs.tagObj.ej2Instances;
      this.chipOnCreate(this.tagObj.value);
    },
    methods: {
        onActionSuccess: function(e) {
            e.value = this.chipCreation(e.value.split(','), true);
        },
        onActionFailure: function(e) {
            e.value = this.chipCreation(e.value.split(','), false);
        },
        chipOnCreate: function() {
            this.tagObj.element.querySelector('.e-editable-value').innerHTML = this.chipCreation(this.tagObj.value);
        },
        chipCreation: function(data) {
            let value = '<div class="e-chip-list">';
            [].slice.call(data).forEach((val) => {
                value += '<div class="e-chip"> <span class="e-chip-text"> ' + val + '</span></div>';
            });
            value += '</div>';
            return value;
        },
    },
    provide: {
        "inplaceeditor": [MultiSelect]
    }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-lists/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-richtexteditor/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-splitbuttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-inplace-editor/styles/material.css";

.table-section {
    margin: 0 auto;
}

tr td:first-child {
    text-align: right;
    padding-right: 20px;
}
</style>
```

{% endtab %}

## See Also

* [Indicate the server actions in the editor](./how-to/custom-indication)