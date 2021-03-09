---
title: "In-place Editor Getting Started"
component: "In-place Editor"
description: "This section explains how to create an In-place Editor component in a Vue application with its basic features."
---

# Getting Started

This section briefly explains about how to create a simple **In-place Editor** using VueJS and demonstrates the basic of the In-place Editor component in a Vue environment.

## Dependencies

The following list of dependencies are required to use the In-place Editor component in your application.

```javascript
|-- @syncfusion/ej2-vue-inplace-editor
  |-- @syncfusion/ej2-base
  |-- @syncfusion/ej2-buttons
  |-- @syncfusion/ej2-calendars
  |-- @syncfusion/ej2-data
  |-- @syncfusion/ej2-dropdowns
  |-- @syncfusion/ej2-inputs
  |-- @syncfusion/ej2-lists
  |-- @syncfusion/ej2-navigations
  |-- @syncfusion/ej2-popups
  |-- @syncfusion/ej2-richtexteditor
  |-- @syncfusion/ej2-splitbuttons
  |-- @syncfusion/ej2-vue-base

```

## Get Started with Vue CLI

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your vue applications.
To install Vue CLI use the following command.

```bash
npm install -g @vue/cli
npm install -g @vue/cli-init
```

Start a new project using the following Vue CLI command.

```bash
vue init webpack-simple quickstart

cd quickstart
npm install

```

## Adding Syncfusion packages

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.
You can choose the component that you want to install. For this application, use the In-place Editor component.

To install the In-place Editor component, use the following command

```bash
npm install @syncfusion/ej2-vue-inplace-editor --save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.
* Vue.use()
* Vue.component()

### Using Vue.use()

Import the Component Plugin from the EJ2 Vue package and register the same using Vue.use() with the Component Plugin as its argument.

Refer the following code snippet.

```typescript
import { InPlaceEditorPlugin } from '@syncfusion/ej2-vue-inplace-editor';

Vue.use(InPlaceEditorPlugin);
```

> By registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the Component and Component Plugin from EJ2 Vue Package,
register the same using the Vue.component() with the name of Component from Component Plugin
and the EJ2 Vue Component as its arguments.

Refer to the following code snippet.

```typescript
import { InPlaceEditorComponent, InPlaceEditorPlugin } from '@syncfusion/ej2-vue-inplace-editor';

Vue.component(InPlaceEditorPlugin.name, InPlaceEditorComponent);
```

Note: By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Creating Vue Sample

Add the EJ2 Vue In-place Editor using `<ejs-inplaceeditor>` to the `<template>` section of the `App.vue` file in src directory,
the content attribute of the In-place Editor component is provided as name in data option in the `<script>` section.

```html
<template>
  <div id="app">
    <ejs-inplaceeditor id="inplace_editor" type="Text" value="Andrew" :model="model">
    </ejs-inplaceeditor>
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
      model: {
          placeholder: 'Enter employee name'
      },
    }
  }
}
</script>

```

## Adding CSS reference

Add the In-place Editor component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
@import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-lists/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-richtexteditor/styles/material.css";
@import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-inplace-editor/styles/material.css";
</style>
```

## Add the In-place Editor with Textbox

By default, the TextBox component is rendered in In-place Editor with the [`type`](../api/inplace-editor/inputType/) property sets as Text.

```html
<template>
    <div id="app">
    <ejs-inplaceeditor id="inplace_editor" type="Text" value="Andrew" :model="model">
    </ejs-inplaceeditor>
  </div>
</template>
<script>
import Vue from 'vue';
import { InPlaceEditorPlugin } from '@syncfusion/ej2-vue-inplace-editor';

Vue.use(InPlaceEditorPlugin);
export default {
  name: 'app',
  data: function(){
    return {
      model: {
          placeholder: 'Enter employee name'
      },
    }
  }
}
</script>

```

## Configure DropDownList

You can render DropDownList by changing the [`type`](../api/inplace-editor/inputType/) property as [`DropDownList`](../api/drop-down-list) and configure its properties and methods using the `model` property.

In the following sample, [`type`](../api/inplace-editor/inputType/) and model values are configured to render the [`DropDownList`](../api/drop-down-list) component.

```html
<template>
  <div id="app">
    <ejs-inplaceeditor id="element" type="DropDownList" mode= "Inline" :model="model">
    </ejs-inplaceeditor>
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
      model: {
           genderData: ['Male', 'Female'],
           placeholder: 'Select gender'
      },
    }
  }
}
</script>

```

## Integrate DatePicker

You can render [DatePicker](../api/datepicker) by changing the [`type`](../api/inplace-editor/inputType/) property as [`Date`](../api/inplace-editor/inputType/)  and also configure its properties and methods using [`model`](../api/inplace-editor#model) property.

In the below sample, [`type`](../api/inplace-editor/inputType/) and [`model`](../api/inplace-editor#model) values are configured to render the [DatePicker](../api/datepicker) component.

```html
<template>
  <div id="app">
    <ejs-inplaceeditor id="inplace_editor" type="Date" :model="model" :value="value">
    </ejs-inplaceeditor>
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
      value: new Date('04/12/2018'),
      model: {
            showTodayButton: true
      },
    }
  }
}
</script>

```

## Run the application

Now, run the `npm run dev` command in the console, it will build your application and open in the browser.

{% tab template="in-place-editor/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class="control-group">
        <h3> Modify Basic Details </h3>
          <table>
            <tr>
              <td>Name</td>
              <td class='left'>
                <ejs-inplaceeditor id="element" type="Text" mode="Inline" value="Andrew" :model="textModel"></ejs-inplaceeditor>
              </td>
            </tr>
            <tr>
              <td>Date of Birth</td>
              <td class='left'>
                <ejs-inplaceeditor id="dateofbirth" type="Date" mode="Inline" :value="dateValue" :model="dateModel"></ejs-inplaceeditor>
              </td>
            </tr>
            <tr>
              <td>Gender</td>
              <td class='left'>
                <ejs-inplaceeditor id="gender" type="DropDownList" mode= "Inline" value="Male" :model="dropdownModel"></ejs-inplaceeditor>
              </td>
            </tr>
          </table>
      </div>
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
      dateValue: new Date('04/12/2018'),
      dateModel: {
        showTodayButton: true,
         placeholder: 'Select date of birth'
      },
      textModel: {
          placeholder: 'Enter your name'
      },
      dropdownModel: {
           dataSource: ['Male', 'Female'],
           placeholder: 'Select gender'
      },
    }
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-lists/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-richtexteditor/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-inplace-editor/styles/material.css";
</style>

<style>
#app {
    visibility: hidden;
}

#app .control-group {
    text-align: center;
    margin-top: 50px;
}

#app .control-group table {
  width: 400px;
  margin:auto;
}

#app .control-group table td {
    height: 70px;
    width:  150px;
  }

  #app .control-group table td.left {
    text-align: left;
  }  
  
</style>

```

{% endtab %}

## Two-way binding

In In-place Editor, two-way binding support is achieved using the `v-model` directive in Vue. When you change a value in the first In-place Editor component, the changed value gets updated automatically to the second In-place Editor. The following example demonstrates, how to achieve two-way binding in In-place Editor.

{% tab template="in-place-editor/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div id='container'>
         <div class="control-group">
          <table>
            <tr>
                <td><b>TextBox :</b></td>
                <ejs-inplaceeditor id="textbox" type="Text" mode="Inline" :model="textModel" v-model="value">
                </ejs-inplaceeditor>

                <ejs-inplaceeditor id="textbox2" type="Text" mode="Inline" :model="textModel" v-model="value">
                </ejs-inplaceeditor>
            </tr>
            <tr>
                <td><b>Datepicker :</b></td>
                <ejs-inplaceeditor id="dateeditor1" mode="Inline" type="Date" :model="dateModel" v-model="datePickerValue">
                </ejs-inplaceeditor>

                <ejs-inplaceeditor id="dateeditor2" mode="Inline" type="Date" :model="dateModel" v-model="datePickerValue">
                </ejs-inplaceeditor>
            </tr>
            <tr>
                <td><b>DropDownList :</b></td>
                <ejs-inplaceeditor id="dropDowneditor1" mode="Inline" type="DropDownList" :model="dropdownModel" v-model="dropdownValue">
                </ejs-inplaceeditor>

                <ejs-inplaceeditor id="dropDowneditor2" mode="Inline" type="DropDownList" :model="dropdownModel" v-model="dropdownValue">
                </ejs-inplaceeditor>
            </tr>
        </table>
      </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { InPlaceEditorPlugin } from '@syncfusion/ej2-vue-inplace-editor';

Vue.use(InPlaceEditorPlugin);
export default {
  name: 'app',
  data () {
    let frameWorkList = ['Android', 'JavaScript', 'jQuery', 'TypeScript',
    'Angular', 'React', 'Vue','Ionic'];
    return {
      value: 'Andrew',
      dropdownValue: 'Android',
      datePickerValue: new Date('11/23/2018'),
      textModel: {
        placeholder: 'Enter employee name'
      },
      dropdownModel: {
        placeholder: 'Select frameWorks',
        dataSource: frameWorkList
      },
      dateModel: {
        placeholder: 'Select date'
      }
    }
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-lists/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-richtexteditor/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-inplace-editor/styles/material.css";
</style>

<style>
#app {
    visibility: hidden;
}

#app .control-group {
    text-align: center;
    margin-top: 50px;
}

#app .control-group table {
  width: 400px;
  margin:auto;
}

#app .control-group table td {
    height: 70px;
    width:  150px;
  }

  #app .control-group table td.left {
    text-align: left;
  }  

</style>

```

{% endtab %}

## Submitting data to the server (save)

You can submit editor value to server by configuring the [`url`](../api/inplace-editor#url), [`adaptor`](../api/inplace-editor/adaptorType/), and [`primaryKey`](../api/inplace-editor#primarykey) property.

| Property   | Usage                                           |
|------------|---------------------------------------------------------|
| **`url`**        | Gets the url for server submit action.        |
| **`adaptor`**    | Specifies the adaptor type that is used by DataManager to communicate with DataSource.                |
| **`primaryKey`** | Defines the unique primary key of editable field which can be used for saving data in the data-base.|

> The [`primaryKey`](../api/inplace-editor#primarykey) property is mandatory. If it's not set, edited data are not sent to the server.

## Refresh with modified value

The edited data is submitted to the server and you can see the new values getting reflected in the In-place Editor.

{% tab template="in-place-editor/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class="container">
        <div class="control-group" style="text-align:center;margin: 100px auto">
          Best Employee of the year:  <ejs-inplaceeditor id="element" type="DropDownList" mode="Inline" value="Andrew Fuller" name="Employee" :url="serviceUrl" primaryKey="Employee" adaptor="UrlAdaptor" :model="dropdownModel" :actionSuccess= "actionSuccess" :created='created'></ejs-inplaceeditor>
        </div>
        <table style="margin:auto;width:50%">
          <tr>
            <td style="text-align: left">
               Old Value :
            </td>
            <td id="oldValue" ref="oldValue" style="text-align: left">

            </td>
          </tr>
          <tr>
            <td style="text-align: left">
               New Value :
            </td>
            <td id="newValue" ref="newValue" style="text-align: left">
                Andrew Fuller
            </td>
          </tr>
        </table>
      </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { InPlaceEditorPlugin, MultiSelect, ActionEventArgs } from '@syncfusion/ej2-vue-inplace-editor';

Vue.use(InPlaceEditorPlugin);
export default {
  name: 'app',
  data () {
    return {
      serviceUrl: "https://ej2services.syncfusion.com/development/web-services/api/Editor/UpdateData",
      dropdownModel: {
           dataSource: ['Andrew Fuller', 'Janet Leverling', 'Laura Callahan', 'Margaret Hamilt', 'Michael Suyama', 'Nancy Davloio', 'Robert King'],
           popupHeight: '200px',
           placeholder: 'Select employee'
      },
    }
  },
  methods: {
    created: function() {
      this.newValue = this.$refs.newValue;
      this.oldValue = this.$refs.oldValue;
    },
    actionSuccess: function(e){
      this.oldValue.textContent =  this.newValue.textContent;
      this.newValue.textContent = e.value;
    }
  },
  provide:{
        "inplaceeditor":[MultiSelect]
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-lists/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-richtexteditor/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-inplace-editor/styles/material.css";
</style>

<style>

.e-inplaceeditor {
    min-width: 200px;
    text-align: left
}

</style>

```

{% endtab %}

## See Also

* [Types of rendering the editor](./integration/)