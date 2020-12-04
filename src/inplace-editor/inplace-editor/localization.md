---
title: "Globalization"
component: "In-place Editor"
description: "Learn how to apply localization (l10n), internationalization (i18n), and right-to-left (RTL) format in the Essential JS 2 Vue In-place Editor component."
---

# Globalization

## Localization

Localization library allows you to localize the default text content of the In-place Editor to different cultures using the [locale](../api/inplace-editor/#locale) property. In-place Editor following keys will be localize based on culture.

| Locale key | en-US (default) |
|------|------|
| save | Close |
| cancel | Cancel |
| loadingText | Loading... |
| editIcon | Click to edit |
| editAreaClick | Click to edit |
| editAreaDoubleClick | Double click to edit |

To load translation object in an application use `load` function of `L10n` class. In the following sample, `French` culture is set to In-place Editor and change the tooltip text.

{% tab template="in-place-editor/getting-started", isDefaultActive=true %}

```html
     <template>
    <div id="app">
        <table class="table-section">
            <tr>
                <td>EditableOn:</td>
                <td>
                    <ejs-dropdownlist ref="editableOn" id="editableon" width='90%' :dataSource='editableData' :change='onEditableOn' :value='editableValue' :fields='editableFields'>
                    </ejs-dropdownlist>
                </td>
            </tr>
            <tr>
                <td class="sample-td">Enter your name:</td>
                <td class="sample-td">
                    <ejs-inplaceeditor ref="editObj" id="inplace_editor" mode="Inline" type="Text" value="Andrew" submitOnEnter= "true" :model="textModel" locale='fr-BE'>
                    </ejs-inplaceeditor>
                </td>
            </tr>
        </table>
    </div>
</template>

<script>
import Vue from 'vue';
import { InPlaceEditorPlugin } from '@syncfusion/ej2-vue-inplace-editor';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
import { L10n } from '@syncfusion/ej2-base';

Vue.use(InPlaceEditorPlugin);
Vue.use(DropDownListPlugin);

L10n.load({
    'fr-BE': {
        'inplace-editor': {
            'save': 'enregistrer',
            'cancel': 'Annuler',
            'loadingText': 'Chargement...',
            'editIcon': 'Cliquez pour éditer',
            'editAreaClick': 'Cliquez pour éditer',
            'editAreaDoubleClick': 'Double-cliquez pour éditer'
        }
    }
});

export default {
  name: 'app',
      data () {
        return {
            textModel: {
            placeholder: 'Enter employee name'
            },
            editableFields: { text: 'editable', value: 'id' },
            editableData: [{ id: 'Click', editable: 'Click' }, { id: 'DblClick', editable: 'Double Click' }, { id: 'EditIconClick', editable: 'Edit Icon Click' }],
            editableValue: 'Click',
        };
    },
    mounted: function(){
        this.editObj = this.$refs.editObj.ej2Instances;
    },
    methods: {
        onEditableOn: function(args) {
           var editableOn = this.$refs.editableOn.ej2Instances.value;
           this.editObj.editableOn = editableOn;
           this.editObj.dataBind();
        },
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

.sample-td {
    padding-top: 10px;
    min-width: 230px;
    height: 100px;
}
</style>
```

{% endtab %}

## Right to left

Specifies the direction of the In-place Editor component using the [enableRtl](../api/inplace-editor/#enablertl) property. For writing systems that require it like Arabic, Hebrew, etc., the direction can be switched to right-to-left.

> It will not change based on the locale property.

{% tab template="in-place-editor/getting-started", isDefaultActive=true %}

```html
     <template>
    <div id="app">
        <table class="table-section">
            <tr>
                <td>Enter your name:</td>
                <td>
                    <ejs-inplaceeditor ref="editObj" id="editor" mode="Inline" value= 'Andrew' enableRtl=true>
                    </ejs-inplaceeditor>
                </td>
            </tr>
        </table>
    </div>
</template>

<script>
import Vue from 'vue';
import { InPlaceEditorPlugin } from '@syncfusion/ej2-vue-inplace-editor';

Vue.use(InPlaceEditorPlugin);

export default {
  name: 'app',
      data () {
        return {};
    },
    mounted: function(){
        this.editObj = this.$refs.editObj.ej2Instances;
    },
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

## Format

Formatting is a way of representing the value in different format. You can format the following mentioned components with its `format` property, when it passed through the In-place Editor [model](../api/inplace-editor/#model) property.

* [DatePicker](../datepicker/date-format/)
* [DateRangePicker](../daterangepicker/globalization/#customize-the-date-format)
* [DateTimePicker](../api/datetimepicker/#format)
* [NumericTextBox](../numerictextbox/formats/#custom-formats)
* [Slider](../slider/format/)
* [TimePicker](../api/timepicker#format)

{% tab template="in-place-editor/getting-started", isDefaultActive=true %}

```html

     <template>
    <div id="app">
        <table class="table-section">
            <tr>
                <td>select date: </td>
                <td>
                    <ejs-inplaceeditor ref="dateObj" id="datePickerEle" mode="Inline" type="Date" :value="datePickerValue" :model="datePickerModel">
                    </ejs-inplaceeditor>
                </td>
            </tr>
        </table>
    </div>
</template>

<script>
import Vue from 'vue';
import { InPlaceEditorPlugin } from '@syncfusion/ej2-vue-inplace-editor';

Vue.use(InPlaceEditorPlugin);

export default {
  name: 'app',
      data () {
        return {
            datePickerModel: {
                placeholder: 'Select date',
                format: 'yyyy-MM-dd'
            },
           datePickerValue: new Date('11/23/2018'),
        };
    },
    mounted: function(){
        this.dateObj = this.$refs.dateObj.ej2Instances;
    },
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