---
title: "Vue Dialog Getting Started"
component: "Dialog"
description: "Helps to get started with the dialog component along with its key features such as modal dialog, positioning, and draggable."
---

# Getting Started

This section explains how to create a simple Dialog and how to configure the Dialog component.

## Dependencies

The list of dependencies required to use the Dialog component in your application is given below:

```javascript
|-- @syncfusion/ej2-vue-popups
    |-- @syncfusion/ej2-vue-base
    |-- @syncfusion/ej2-vue-buttons
    |-- @syncfusion/ej2-popups
        |-- @syncfusion/ej2-base
        |-- @syncfusion/ej2-buttons
```

## Get Started with Vue CLI

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your vue applications.
To install Vue CLI use the following command.

```bash
npm install -g @vue/cli
```

Start a new project using below Vue CLI command.

```bash
vue init webpack-simple quickstart

cd quickstart
npm install

```

## Adding Syncfusion packages

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.
You can choose the component that you want to install. For this application, we are going to use Dialog component.

To install Dialog component, use the following command

```bash
npm install @syncfusion/ej2-vue-popups –save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.
* Vue.use()
* Vue.component()

### Using Vue.use()

Import the Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { DialogPlugin } from '@syncfusion/ej2-vue-popups';

Vue.use(DialogPlugin);
```

> By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the Component and Component Plugin from EJ2 Vue Package, register the same using the Vue.component() with name of Component from Component Plugin and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { DialogComponent, DialogPlugin } from '@syncfusion/ej2-vue-popups';

Vue.component(DialogPlugin.name, DialogComponent);
```

> By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Creating Vue sample

Add the EJ2 Vue Dialog using `<ejs-dialog>` to the `<template>` section of the `App.vue` file in src directory,
the content attribute of the Dialog component is provided as name in data option in the `<script>` section.

```html
<template>
    <div id="app">
    <ejs-dialog :header="Dialog" :content="content" ></ejs-dialog>
  </div>
</template>
<script>
import Vue from 'vue';
import { DialogPlugin } from '@syncfusion/ej2-vue-popups';

Vue.use(DialogPlugin);
export default {
  name: 'app',
   data () {
    return {
      content: 'The dialog component is used to display information and get input from the user.'
    }
  }
}
</script>
```

## Adding CSS reference

Add Dialog component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
</style>
```

> The [Custom Resource Generator (CRG)](https://crg.syncfusion.com/) is an online web tool, which can be used to generate the custom script and styles for a set of specific components.
> This web tool is useful to combine the required component scripts and styles in a single file.

## Running the application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

{% tab template="dialog/getting-started", isDefaultActive=true %}

```html
<template>
  <div>
    <div id="target"  class="control-section">
        <ejs-dialog :target='target' :width='width' :content='content'>
        </ejs-dialog>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DialogPlugin } from '@syncfusion/ej2-vue-popups';
Vue.use(DialogPlugin);

export default {
    data: function() {
        return {
            target: "#target",
            width: '335px',
            content: 'This is a Dialog with content.'
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
    .control-section {
        height: 100%;
        min-height: 200px;
    }
</style>
```

{% endtab %}

> In the dialog control, max-height is calculated based on the dialog target element height. If the target property is not configured, the document.body is considered as a target. Therefore, to show a dialog in proper height, you need to add min-height to the target element.
> If the dialog is rendered based on the body, then the dialog will get the height based on its body element height. If the height of the dialog is larger than the body height, then the dialog's height will not be set. For this scenario, we can set the CSS style for the html and body to get the dialog height.

```css

html, body {
   height: 100%;
}

```

## Modal dialog

A modal shows an overlay behind the Dialog. So, the user should interact the Dialog compulsory before interacting with the remaining content in an application.

While the user clicks the overlay, the action can be handled through the [overlayClick](../api/dialog/#overlayclick) event. In the below sample, the Dialog close action is performed while clicking on the overlay.

> When the modal dialog is opened, the Dialog's target scrolling will be disabled. The scrolling will be enabled again once close the Dialog.

{% tab template="dialog/modal" %}

```html
<template>
  <div>
    <div id="modalTarget" class="control-section; position:relative" style="height:350px;">
        <!-- Render Button to open the modal Dialog -->
        <ejs-button id='modalbtn' v-on:click.native="modalBtnClick">Open</ejs-button>
        <!-- Render modal Dialog -->
        <ejs-dialog ref="modalDialog"  :isModal='isModal' :header='header' :target='target' :width='width' :animationSettings='animationSettings' :content='content' :open="modalDlgOpen" :close="modalDlgClose" :overlayClick="overlayClick">
        </ejs-dialog>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { DialogPlugin } from '@syncfusion/ej2-vue-popups';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
Vue.use(DialogPlugin);
Vue.use(ButtonPlugin);

export default {
    data: function() {
        return {
            target: "#modalTarget",
            width: '335px',
            header: 'Software Update',
            content: 'Your current software version is up to date.',
            isModal: true,
            animationSettings: { effect: 'None' }
        }
    },
    mounted: function(){
        document.getElementById('modalbtn').focus();
    },
    methods: {
        modalBtnClick: function() {
            this.$refs.modalDialog.show();
        },
        modalDlgClose: function() {
            document.getElementById('modalbtn').style.display = '';
        },
        modalDlgOpen: function() {
            document.getElementById('modalbtn').style.display = 'none';
        },
        overlayClick: function() {
            this.$refs.modalDialog.hide();
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
    #app {
        color: #008cff;
        height: 40px;
        left: 45%;
        position: absolute;
        top: 45%;
        width: 30%;
    }
    .control-section {
        height: 100%;
        min-height: 200px;
    }
</style>
```

{% endtab %}

## Enable header

The Dialog header can be enabled by adding the header content as text or HTML content through the [header](../api/dialog/#header) property.

{% tab template="dialog/header" %}

```html
<template>
  <div>
    <div id="target" class="control-section; position:relative" style="height:350px;">
        <!-- Render Dialog -->
        <ejs-dialog ref="headerDialog" :header='header' :target='target' :width='width' :content='content'>
        </ejs-dialog>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DialogPlugin } from '@syncfusion/ej2-vue-popups';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
Vue.use(DialogPlugin);
Vue.use(ButtonPlugin);

export default {
    data: function() {
        return {
            target: "#target",
            width: '335px',
            header: 'Dialog header',
            content: 'This is a Dialog with header.'
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
    #app {
        color: #008cff;
        height: 40px;
        left: 45%;
        position: absolute;
        top: 45%;
        width: 30%;
    }
    .control-section {
        height: 100%;
        min-height: 200px;
    }
</style>
```

{% endtab %}

## Enable footer

The Dialog provides built-in support to render the buttons on the footer (for ex: 'OK' or 'Cancel' buttons). Each Dialog button allows the user to perform any action while clicking on it.

The primary button will be focused automatically on open the Dialog, and add the `click` event to handle the actions

> When the Dialog initialize with more than one primary buttons, the first primary button gets focus on open the Dialog.

The below sample is rendered with button and its click event.

{% tab template="dialog/footer" %}

```html
<template>
  <div>
    <div id="target" class="control-section; position:relative" style="height:350px;">
        <!-- Render Button to open the Dialog -->
        <ejs-button id='dlgbtn' v-on:click.native="btnClick">Open</ejs-button>
        <!-- Render Dialog -->
        <ejs-dialog ref="footerDialog" :header='header' :target='target' :width='width' :buttons='buttons' :content='content' :open="dlgOpen" :close="dlgClose">
        </ejs-dialog>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DialogPlugin } from '@syncfusion/ej2-vue-popups';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
Vue.use(DialogPlugin);
Vue.use(ButtonPlugin);

export default {
    data: function() {
        return {
            target: "#target",
            width: '335px',
            header: 'Dialog',
            content: 'This is a Dialog with button and primary button.',
            buttons: [{ click: this.dlgButtonClick, buttonModel: { content: 'OK', isPrimary: true } },
            { click: this.dlgButtonClick, buttonModel: { content: 'Cancel' }}]
        }
    },
    mounted: function(){
        document.getElementById('dlgbtn').focus();
    },
    methods: {
        btnClick: function() {
            this.$refs.footerDialog.show();
        },
        dlgClose: function() {
            document.getElementById('dlgbtn').style.display = '';
        },
        dlgOpen: function() {
            document.getElementById('dlgbtn').style.display = 'none';
        },
        dlgButtonClick: function() {
            this.$refs.footerDialog.hide();
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
    #app {
        color: #008cff;
        height: 40px;
        left: 45%;
        position: absolute;
        top: 45%;
        width: 30%;
    }
    .control-section {
        height: 100%;
        min-height: 200px;
    }
</style>
```

{% endtab %}

## Draggable

The Dialog supports to drag within its target container by grabbing the Dialog header, which allows the user to reposition the Dialog dynamically.

> The Dialog can be draggable only when the Dialog header is enabled. From `16.2.x` version, enabled draggable support for modal dialog also.

{% tab template="dialog/draggable" %}

```html
<template>
    <div id="target"  class="control-section">
        <ejs-dialog :header="header" :content="content" :allowDragging="draggable" :target='target' :width='width'> </ejs-dialog>
    </div>
</template>
<script>
import Vue from 'vue';
import { DialogPlugin } from '@syncfusion/ej2-vue-popups';
Vue.use(DialogPlugin);
export default {
   data : function() {
    return {
        target: '#target',
        width: '300px',
        header: 'Dialog',
        draggable: true,
        content: 'This is a Dialog with drag enabled.'
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
    #app {
        color: #008cff;
        height: 40px;
        left: 45%;
        position: absolute;
        top: 45%;
        width: 30%;
    }
    .control-section {
        min-height: 355px;
        margin: 10px;
    }
</style>
```

{% endtab %}

## Positioning

The Dialog can be positioned using the [position](../api/dialog/#position) property by providing the X and Y co-ordinates. It can be positioned inside the target of the container or `<body>` of the element based on the given X and Y values.

for X is: left, center, right (or) any offset value
for Y is: top, center, bottom (or) any offset value
The below example demonstrates the different Dialog positions.

{% tab template="dialog/position" %}

```html
<template>
  <div>
     <div id="target" class="control-section">
         <ejs-button id="dialogBtn" v-on:click.native="buttonClick">Open Dialog</ejs-button>

        <ejs-dialog id='defaultDialog' header='Choose a Dialog Position' showCloseIcon='true' :position='position' :footerTemplate='footerTemplate' width='406px' ref='dialogObj'
            target='#target' :open='dialogOpen' :close='dialogClose' closeOnEscape='false'>
            <table style='width:371px' id ='poschange'>
                <tr>
                    <td><ejs-radiobutton id='radio1' label='Left Top' value='left top' name='xy' :change='changePosition' ></ejs-radiobutton></td>
                    <td><ejs-radiobutton id='radio2' label='Center Top' value='center top' name='xy' :change='changePosition'></ejs-radiobutton></td>
                    <td><ejs-radiobutton id='radio3' label='Right Top' value='right top' name='xy' :change='changePosition'></ejs-radiobutton></td>
                </tr>
                <tr>
                    <td><ejs-radiobutton id='radio4' label='Left Center' value='left center' name='xy' :change='changePosition' ></ejs-radiobutton></td>
                    <td><ejs-radiobutton id='radio5' checked='true' label='Center Center' value='center center' name='xy' :change='changePosition' ></ejs-radiobutton></td>
                    <td><ejs-radiobutton id='radio6' label='Right Center' value='right center' name='xy' :change='changePosition' ></ejs-radiobutton></td>
                </tr>
                <tr>
                    <td><ejs-radiobutton id='radio7' label='Left Bottom' value='left bottom' name='xy' :change='changePosition' ></ejs-radiobutton></td>
                    <td><ejs-radiobutton id='radio8' label='Center Bottom' value='center bottom' name='xy' :change='changePosition' ></ejs-radiobutton></td>
                    <td><ejs-radiobutton id='radio9' label='Right Bottom' value='right bottom' name='xy' :change='changePosition' ></ejs-radiobutton></td>
                </tr>
            </table>
        </ejs-dialog>
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import { DialogPlugin } from '@syncfusion/ej2-vue-popups';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
import { RadioButtonPlugin } from '@syncfusion/ej2-vue-buttons';
Vue.use(DialogPlugin);
Vue.use(ButtonPlugin);
Vue.use(RadioButtonPlugin);

export default {
    data: function() {
        return {
            footerTemplate: '<span id="posvalue" style="float:left;margin-left:8px;padding:10px;">Position: { X: "Center", Y: "Center" }</span>',
            position: { X: 'center', Y: 'center' }
        }
    },
    methods: {
        buttonClick: function(args){
            this.$refs.dialogObj.show();
        },
        changePosition: function(event) {
            this.$refs.dialogObj.position = { X: event.value.split(" ")[0], Y: event.value.split(" ")[1] };
            document.getElementById('posvalue').innerHTML = 'Position: {X: "' + event.value.split(" ")[0] + '", Y: "' + event.value.split(" ")[1] + '"}'
            var txt = event.event.target.parentElement.querySelector('.e-label').innerText.split(" ");
            document.getElementById('posvalue').innerHTML = 'Position: { X: "' + txt[0] + '", Y: "' + txt[1] + '" }';
        },
        dialogClose() {
            document.querySelector('#dialogBtn').style.display='inline-block';
        },
        dialogOpen() {
            document.querySelector('#dialogBtn').style.display='none';
        }
    }
}
</script>

<style>
    html,
    body,
    #container {
        height: 100%;
        overflow: hidden;
        width: 100%;
    }
    .control-section {
        min-height: 350px;
        max-width: 840px;
        margin: 10px;
    }
    #defaultDialog table,
    #defaultDialog th,
    #defaultDialog td {
        border: 1px solid #D8D8D8;
        border-collapse: collapse;
    }

    #container {
        height: 365px;
    }

    #defaultDialog.e-dialog .e-footer-content {
        padding: 0px 1px 4px ! important;
    }

    .tableStyle {
        margin: 17px;
        width: 304px;
    }

    .e-dialog .e-dlgcontent{
        padding: 10px 16px 10px;
    }

    .e-radio +label .e-label {
        line-height:18px;
    }

    td {
        padding: 6px;
    }
</style>
```

{% endtab %}

## See Also

* [Load dialog content using AJAX](./how-to/load-dialog-content-using-ajax)
* [How to position the dialog on center of the page on scrolling](./how-to/position-the-dialog-on-center-of-the-page-on-scrolling)
* [Prevent closing of modal dialog](./how-to/prevent-closing-of-modal-dialog)
* [Close dialog while click on outside of dialog](./how-to/close-dialog-while-click-on-outside-of-dialog)
* [How to make a reusable alert and confirm dialog](./dialog-utlility/)
