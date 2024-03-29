---
title: "Form fields"
component: "DocumentEditor"
description: "Learn how to use form fields in Vue document editor"
---

# Form Fields

Document Editor Container component provide support for inserting Text, CheckBox, DropDown form fields through in-built toolbar.

![Form Fields](images/toolbar-form-fields.png)

## Insert form field

Form fields can be inserted using [`insertFormField`](../api/document-editor/editor/#insertformfield) method in editor module.

```typescript
//Insert Text form field
this.$refs.documenteditor.ej2Instances.editor.insertFormField('Text');
//Insert Checkbox form field
this.$refs.documenteditor.ej2Instances.editor.insertFormField('CheckBox');
//Insert Drop down form field
this.$refs.documenteditor.ej2Instances.editor.insertFormField('Dropdown');
```

## Get form field names

All the form fields names form current document can be retrieved using [`getFormFieldNames()`](../api/document-editor/#getformfieldnames).

```typescript
this.$refs.documenteditor.ej2Instances.getFormFieldNames();
```

## Get form field properties

Form field properties can be retrieved using [`getFormFieldInfo()`](../api/document-editor/#getformfieldinfo).

```typescript
//Text form field
var textfieldInfo = this.$refs.documenteditor.ej2Instances.getFormFieldInfo('Text1');
//Checkbox form field
var checkboxfieldInfo = this.$refs.documenteditor.ej2Instances.getFormFieldInfo('Check1');
//Dropdown form field
var dropdownfieldInfo = this.$refs.documenteditor.ej2Instances.getFormFieldInfo('Drop1');
```

## Set form field properties

Form field properties can be modified using [`setFormFieldInfo`](../api/document-editor/#setformfieldInfo).

```typescript
// Set text form field properties
var textfieldInfo = this.$refs.documenteditor.ej2Instances.getFormFieldInfo('Text1');
textfieldInfo.defaultValue = "Hello";
textfieldInfo.format = "Uppercase";
textfieldInfo.type = "Text";
this.$refs.documenteditor.ej2Instances.setFormFieldInfo('Text1',textfieldInfo);

// Set checkbox form field properties
var checkboxfieldInfo = this.$refs.documenteditor.ej2Instances.getFormFieldInfo('Check1');
checkboxfieldInfo.defaultValue = true;
this.$refs.documenteditor.ej2Instances.setFormFieldInfo('Check1',checkboxfieldInfo);

// Set checkbox form field properties
var dropdownfieldInfo = this.$refs.documenteditor.ej2Instances.getFormFieldInfo('Drop1');
dropdownfieldInfo.dropDownItems = ['One','Two', 'Three']
this.$refs.documenteditor.ej2Instances.setFormFieldInfo('Drop1',dropdownfieldInfo);
```

## Export form field data

Data of the all the Form fields in the document can be exported using [`exportFormData`](../api/document-editor/#exportformdata).

```typescript
var formFieldDate = this.$refs.documenteditor.ej2Instances.exportFormData();
```

## Import form field data

Form fields can be prefilled with data using [`importFormData`](../api/document-editor/#importformdata).

```typescript
var textformField = {fieldName: 'Text1', value: 'Hello World'};
var checkformField = {fieldName: 'Check1', value: true};
var dropdownformField = {fieldName: 'Drop1', value: 1};
//Import form field data
this.$refs.documenteditor.ej2Instances.importFormData([textformField,checkformField,dropdownformField]);
```

## Reset form fields

Reset all the form fields in current document to default value using [`resetFormFields`](../api/document-editor/#resetformfields).

```typescript
this.$refs.documenteditor.ej2Instances.resetFormFields();
```
