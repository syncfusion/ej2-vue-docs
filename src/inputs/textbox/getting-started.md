---
title: "Getting Started"
component: "TextBox"
description: "Helps to get started with text box component along with its key features such as a floating label, adding icons (input group), and ripple effect."
---

# Getting Started

This section briefly explains about how to create a simple TextBox through CSS classes using Essential JS 2
[quickstart](https://github.com/syncfusion/ej2-quickstart.git) seed repository.

## Dependencies

The following list of dependencies are required to use the TextBox component in your application.

```js
|-- @syncfusion/ej2-vue-inputs
  |-- @syncfusion/ej2-inputs
  |-- @syncfusion/ej2-base

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
You can choose the component that you want to install. For this application, we are going to use Textbox component.

To install Textbox component, use the following command

```bash
npm install @syncfusion/ej2-vue-inputs –save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.
* Vue.use()
* Vue.component()

Since the Textbox is a pure CSS component there is no need to refer the scripts

* The TextBox CSS files are available in the `ej2-inputs` package folder.
This can be referenced in your application using the following code.

* Add Textbox component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
</style>
```

> The [Custom Resource Generator (CRG)](https://crg.syncfusion.com/) is an online web tool, which can be used to generate the custom script and styles for a set of specific components.
> This web tool is useful to combine the required component scripts and styles in a single file.

## Adding TextBox to the application

Add the input element with `e-input` class into the `<template>` section of the `App.vue` file in src directory.

```html
<template>
    <div id ='wrap'>
        <div id ='input-container'>
            <div>
                <!--element which is going to render the TextBox-->
                <input class="e-input" type="text" placeholder="Enter Date" />
            </div>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
export default {
  name: 'wrap',
}
</script>

```

## Adding icons to the TextBox

You can create a TextBox with icon as a group by creating the parent div element with the class `e-input-group` and add the icon element as span with the class `e-input-group-icon`. For detailed information, refer to the [Groups](./groups/) section.

```html
      <!--element which is going to render the TextBox with date icon-->
      <div class="e-input-group">
            <input class="e-input" name='input' type="text" placeholder="Enter Date"/>
            <span class="e-input-group-icon e-input-popup-date"></span>
      </div>
```

```css
  .e-input-group-icon.e-input-popup-date:before {
    content: "\e901";
  }
  
```

* Now, run the application in the browser using the following command.

```shell
npm run dev
```

Output will be as follows:

{% tab template="textbox/icon-samples", isDefaultActive=true %}

```html
<template>
    <div class ='wrap'>
        <div id ='input-container'>
                <input class="e-input" type="text" placeholder="Enter Date" />
            <div class="e-input-group">
                <input class="e-input" name='input' type="text" placeholder="Enter Date"/>
                <span class="e-input-group-icon e-input-popup-date"></span>
            </div>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';

export default {
   data: function() {
        return { }
    },
    mounted: function() {
        // To get the all input fields and its container.

        let inputElement = document.querySelectorAll('.e-input-group .e-input,.e-float-input.e-input-group input');

        // Add 'e-input-focus' class to the input for achive ripple effect when focus on the input field.

        for (let i = 0; i < inputElement.length; i++) {
            inputElement[i].addEventListener("focus", function () {
                let parentElement = this.parentNode;
                if (parentElement.classList.contains('e-input-in-wrap')) {
                    parentElement.parentNode.classList.add('e-input-focus');
                } else {
                    this.parentNode.classList.add('e-input-focus');
                }
            });
            inputElement[i].addEventListener("blur", function () {
                let parentElement = this.parentNode;
                if (parentElement.classList.contains('e-input-in-wrap')) {
                    parentElement.parentNode.classList.remove('e-input-focus');
                } else {
                    this.parentNode.classList.remove('e-input-focus');
                }
            });
        }

        // Add 'e-input-btn-ripple' class to the icon element for achive ripple effect when click on the icon.

        var inputIcon = document.querySelectorAll('.e-input-group-icon');
        for (let i = 0; i < inputIcon.length; i++) {
            inputIcon[i].addEventListener('mousedown', function () {
                this.classList.add('e-input-btn-ripple');
            });
            inputIcon[i].addEventListener('mouseup', function () {
                let element = this;
                setTimeout(function () {
                    element.classList.remove('e-input-btn-ripple');
                }, 500);
            });
        }
    });
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";

  .wrap {
    box-sizing: border-box;
    margin: 0 auto;
    padding: 20px 10px;
    width: 340px;
  }

  #input-container .e-input-group {
    margin: 30px 0;
  }
  .e-input-group-icon:before {
    font-family: e-icons;
  }

  .e-input-group .e-input-group-icon.e-input-popup-date {
    font-size:16px;
  }

  .e-input-group.e-small .e-input-group-icon.e-input-popup-date {
    font-size:14px;
  }

  .e-input-group-icon.e-input-popup-date:before {
    content: "\e901";
  }
</style>

```

{% endtab %}

## Floating label

The floating label TextBox floats the label above the TextBox after focusing, or filled with value in the TextBox.
You can create the floating label TextBox by using `floatLabelType` API.

{% tab template="textbox/icon-samples", isDefaultActive=true %}

```html
<template>
    <div class ='wrap'>
        <div id ='input-container'>
            <ejs-textbox id='textbox' floatLabelType="Auto" placeholder="First Name"></ejs-textbox>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { TextBoxPlugin } from '@syncfusion/ej2-vue-inputs';
Vue.use(TextBoxPlugin);

export default {
   data: function() {
        return { }
    };
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";

  .wrap {
    box-sizing: border-box;
    margin: 0 auto;
    padding: 20px 10px;
    width: 340px;
  }
</style>

```

{% endtab %}

## See Also

* [How to render TextBox programmatically](./how-to/add-textbox-programmatically)
* [How to add floating label to TextBox programmatically](./how-to/add-floating-label-to-textbox-programmatically)
