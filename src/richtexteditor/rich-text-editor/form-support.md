---
title: "Rich Text Editor Form Support"
component: "Rich Text Editor"
description: "This section for Syncfusion vue Rich Text Editor component demonstrates how to work with form and it's validation."
---

# Form support

The following sample demonstrates how to get the Rich Text Editor value in button click.

## Render the Rich Text Editor

Render the Rich Text Editor in form.

{% tab template="rich-text-editor/markdown", isDefaultActive=true %}

```html
<template>
<div id="app">
    <div id='container'>
        <br>
        <form id="myForm" >
          <ejs-richtexteditor name="name" id="name" v-model="name" :blur="blur"></ejs-richtexteditor>
          <span style='color: red' v-for="error in errors">{{ error }}</span>
          <p>
    <button id="validateSubmit" class="sample-btn e-control e-btn" type="button" data-ripple="true">Submit</button>
          <button id="reset-btn" class="sample-btn e-control e-btn" type="reset" data-ripple="true">Reset</button>
  </p>
      </form>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import { RichTextEditorPlugin, Toolbar, Link, Image, HtmlEditor } from "@syncfusion/ej2-vue-richtexteditor";
import { FormValidator } from '@syncfusion/ej2-inputs';

Vue.use(RichTextEditorPlugin);

export default {
  data:{
    errors:[],
    name:null,
  },
  methods:{
    blur: function(){
      if(this.name) return true;
      this.errors = [];
      if(!this.name) this.errors.push("value required.");
    }
  },
  provide:{
        richtexteditor:[Toolbar, Link, Image, HtmlEditor]
    }
};
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-lists/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-richtexteditor/styles/material.css";
</style>
```

{% endtab %}

## See Also

* [How to integrate the third party library](./third-party-integration/)
* [How to validate the value](./validation/)