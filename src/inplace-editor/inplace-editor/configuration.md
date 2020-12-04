---
title: "Configuration"
component: "In-place Editor"
description: "Learn how to configure various renders, display modes, and configure the focus out actions in the Essential JS 2 Vue In-place Editor component."
---

# Configuration

## Rendering modes

This section explains the supported rendering modes of the In-place Editor. Possible Rendering modes are as follows.

    * Popup
    * Inline

> By default, `Popup` mode will be rendered, when opening an editor.

* For `Popup` mode, editable container displays as like tooltip or popover above the element.

* For `Inline` mode, editable container displays as instead of the element. To render `Inline` mode while opening the editor, specify `mode` as `Inline`.

In the following sample, the In-place Editor renders with `Inline` mode. You can dynamically switch into another mode by changing the drop-down item value.

{% tab template="in-place-editor/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
       <table class="table-section">
            <tr>
                <td>Mode</td>
                <td>
                    <ejs-dropdownlist ref="editorMode" id="editorMode" :dataSource='dataPlace' :change='changeEditorMode' :value='dataValue' :fields='placeFields'>
                    </ejs-dropdownlist>
                </td>
            </tr>
            <tr>
                <td class="sample-td">Enter your Name</td>
                <td class="sample-td">
                <ejs-inplaceeditor ref="editObj" id="inplace_editor" mode="Inline" type="Text" value="Andrew" submitOnEnter= "true" :model="textModel">
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

Vue.use(InPlaceEditorPlugin);
Vue.use(DropDownListPlugin);

export default {
  name: 'app',
    data () {
        return {
            textModel: {
                placeholder: 'Enter Some Name'
            },
            dataValue: 'inline',
            placeFields: { text: 'mode', value: 'id' },
            dataPlace: [{ id: 'inline', mode: 'Inline' }, { id: 'popup', mode: 'Popup' }],
        }
    },
    mounted: function(){
        this.editObj = this.$refs.editObj.ej2Instances;
    },
    methods: {
        changeEditorMode: function(args) {
           var editMode = this.$refs.editorMode.$el.value;
           this.editObj.mode = editMode;
           this.editObj.dataBind();
        }
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

### Pop-up customization

In-place Editor popup mode can be customized by using the [title](../api/inplace-editor/popupSettings/#title) and [model](../api/inplace-editor/popupSettings/#model) properties in [popupSettings](../api/inplace-editor/popupSettings/) API.

Popup mode rendered by using the Essential JS 2 Tooltip component, so you can use tooltip properties and events to customize the behavior of popup via the [model](../api/inplace-editor/popupSettings/#model) property of [popupSettings](../api/inplace-editor/popupSettings/) API.

> For more details, refer the tooltip documentation [section](../tooltip/).

In the following sample, popup [title](../api/inplace-editor/popupSettings/#title) and [position](../api/tooltip/#position) customized using the [popupSettings](../api/inplace-editor/popupSettings/) property. All possible tooltip position data configured in the drop-down, if we change drop down item, selected value bound to [model](../api/inplace-editor/popupSettings/#model) property and applied it to [Tooltip](../tooltip/) component. `Tooltip` have following position options.

* TopLeft
* TopCenter
* TopRight
* BottomLeft
* BottomCenter
* BottomRight
* LeftTop
* LeftCenter
* LeftBottom
* RightTop
* RightCenter
* RightBottom

{% tab template="in-place-editor/getting-started", isDefaultActive=true %}

```html
<template>
<div id="app">
         <table class="table-section">
            <tr>
                <td>Position</td>
                <td>
                    <ejs-dropdownlist ref="editorMode" id="editorMode" :dataSource='dataPlace' :change='changeEditorMode' :value='dataValue' :fields='placeFields'>
                    </ejs-dropdownlist>
                </td>
            </tr>
            <tr>
                <td class="edit-heading sample-td">Enter your Name</td>
                <td class="sample-td">
                <ejs-inplaceeditor ref="editObj" id="inplace_editor" mode="Popup" type="Text" value="Andrew" submitOnEnter= "true" :model="textModel" :popupSettings="textpopupsettings">
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

Vue.use(InPlaceEditorPlugin);
Vue.use(DropDownListPlugin);

export default {
  name: 'app',
    data () {
        return {
            textModel: {
                placeholder: 'Enter Some Name',
            },
            textpopupsettings: {
                model: {
                position: 'BottomCenter'
                }
            },
            dataValue: 'BottomCenter',
            placeFields: { text: 'mode', value: 'id' },
            dataPlace: [{ id: 'TopLeft', mode: 'TopLeft' }, { id: 'TopCenter', mode: 'TopCenter' },{ id: 'TopRight', mode: 'TopRight' }, { id: 'BottomLeft', mode: 'BottomLeft' }, { id: 'BottomCenter', mode: 'BottomCenter' }, { id: 'BottomRight', mode: 'BottomRight' }, { id: 'LeftTop', mode: 'LeftTop' },{ id: 'LeftCenter', mode: 'LeftCenter' }, { id: 'LeftBottom', mode: 'LeftBottom' }, { id: 'RightTop', mode: 'RightTop' }, { id: 'RightCenter', mode: 'RightCenter' }, { id: 'RightBottom', mode: 'RightBottom' }],
        }
    },
    mounted: function(){
        this.editObj = this.$refs.editObj.ej2Instances;
    },
    methods: {
        changeEditorMode: function(args) {
           var positions = this.$refs.editorMode.$el.value;
           this.$refs.editObj.ej2Instances.popupSettings.model.position = positions;
           this.editObj.dataBind();
        }
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
.sample-td {
    padding-top: 150px;
}
.edit-heading {
    padding-right: 20px;
}
</style>
```

{% endtab %}

## Event actions for editing

The event action of the editor that enable in the edit mode based on the [editableOn](../api/inplace-editor/#editableon) property, by default `Click` is assigned, the following options are also supported.

* **[Click](../api/inplace-editor/editableType/)**:  The editor will be opened as single click actions.
* **[DblClick](../api/inplace-editor/editableType/)**: The editor will be opened as double-click actions and it is not applicable for edit icon.
* **[EditIconClick](../api/inplace-editor/editableType/)**: Disables the editing of event action of input and allows user to edit only through edit icon.

> In-place Editor get focus by pressing the `tab` key from previous focusable DOM element and then by pressing `enter` key, the editor will be opened.

In the following sample, when switching drop-down item, the selected value assigned to the `editableOn` property. If you changed to `DblClick`, the editor will open when making a double click on the input.

{% tab template="in-place-editor/getting-started", isDefaultActive=true  %}

```html
<template>
<div  id="app">
        <table class="table-section">
            <tr>
                <td>EditableOn</td>
                <td>
                     <ejs-dropdownlist ref="editableOn" id="editableon" :dataSource='editableData' :change='onEditableOn' :value='editableValue' :fields='editableFields'>
                    </ejs-dropdownlist>
                </td>
            </tr>
            <tr>
                <td class="sample-td">Enter your Name</td>
                <td class="sample-td">
                <ejs-inplaceeditor ref="editObj" id="inplace_editor" mode="Inline" type="Text" value="Andrew" submitOnEnter= "true" :model="textModel">
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

Vue.use(InPlaceEditorPlugin);
Vue.use(DropDownListPlugin);

export default {
    name: 'app',
    data () {
        return {
            textModel: {
                placeholder: 'Enter Some Text'
            },
            editableFields: { text: 'editable', value: 'id' },
            editableData: [{ id: 'Click', editable: 'Click' }, { id: 'DblClick', editable: 'Double Click' }, { id: 'EditIconClick', editable: 'Edit Icon Click' }],
            editableValue: 'Click',
        }
    },
    mounted: function(){
        this.editObj = this.$refs.editObj.ej2Instances;
    },
    methods: {
        onEditableOn: function() {
           var editableOn = this.$refs.editableOn.ej2Instances.value;
           this.$refs.editObj.ej2Instances.editableOn = editableOn;
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

## Action on focus out

Action to be performed when the user clicks outside the container, that means focusing out of editable content and it can be handled by the [actionOnBlur](../api/inplace-editor/#actiononblur) property, by default `Submit` assigned. It also has the following options.

* **[Cancel](../api/inplace-editor/actionBlur/)**: Cancels the editing and resets the old content.
* **[Submit](../api/inplace-editor/actionBlur/)**: Submits the edited content to the server.
* **[Ignore](../api/inplace-editor/actionBlur/)**: No action is performed with this type and allows to edit multiple editors.

In the following sample, when switching drop-down item, the selected value assigned to the `actionOnBlur` property.

{% tab template="in-place-editor/getting-started", es5Template="es5_action_on_blur", sourceFiles="index.ts,index.html" %}

```html
     <template>
    <div id="app">
        <table class="table-section">
            <tr>
                <td>ActionOnBlur</td>
                <td>
                     <ejs-dropdownlist ref="actions" id="actions" :dataSource='blurActionData' :change='onEditableOn' :value='actionValue' :fields='actionFields'>
                    </ejs-dropdownlist>
                </td>
            </tr>
            <tr>
                <td class="sample-td">Enter your Name</td>
                <td class="sample-td">
                <ejs-inplaceeditor ref="editObj" id="inplace_editor" mode="Inline" type="Text" value="Andrew" submitOnEnter= "true" :model="textModel"  >
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

Vue.use(InPlaceEditorPlugin);
Vue.use(DropDownListPlugin);

export default {
  name: 'app',
      data () {
        return {
            textModel: {
                placeholder: 'Enter Some Text'
            },
            actionFields: { text: 'editable', value: 'id' },
            blurActionData: [{ id: 'Submit', editable: 'Submit' }, {id: 'Cancel', editable: 'Cancel'}, { id:'Ignore', editable: 'Ignore'}],
            actionValue: 'Submit',
        };
    },
    mounted: function(){
        this.editObj = this.$refs.editObj.ej2Instances;
    },
    methods: {
        onEditableOn: function() {
            var actionType = this.$refs.actions.ej2Instances.value;
            this.$refs.editObj.ej2Instances.actionOnBlur = actionType;
            this.editObj.dataBind();
        },
    }
}
</script>
```

{% endtab %}

## Display modes

By default, In-place Editor input element highlighted with a dotted underline. To remove dotted underline from input element, add `data-underline="false"` attribute at In-place Editor root element.

In the following sample, denotes to indicate intractable and normal display modes with different samples.

{% tab template="in-place-editor/getting-started", es5Template="es5_under_line", sourceFiles="index.ts,index.html" %}

```html
<template>
<div id="app">
<h4>Example of data-underline attribute</h4>
    <table class="table-section">
        <tr>
        <td>Intractable UI</td>
        <td>
        <ejs-inplaceeditor mode="Inline" :model="textModel" type="Text" value="Andrew">
        </ejs-inplaceeditor>
        </td>
        </tr>
        <tr>
        <td class="sample-td">Normal UI </td>
        <td class="sample-td">
        <ejs-inplaceeditor mode="Inline" :model="textModel" type="Text" data-underline="false" value="Andrew">
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
            textModel: {
                placeholder: 'Enter Some Text'
            },
        };
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

h4{
    text-align: center;
    font-size: 18px;
}
</style>
```

{% endtab %}

## See Also

* [Disable the editor](./how-to/disable-edit-mode)
* [Animate the editor during popup mode](./how-to/custom-animation)