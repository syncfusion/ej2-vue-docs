---
title: "Multiline"
component: "Textbox"
description: "Explains about multiple lines of text like address, description and feedback are allows to fill in multiline textbox and it can be editable or can copy the text."
---

# Multiline TextBox

This feature allows the textbox to accept one or more lines of text like address, description, comments, and more.

## Create multiline textbox

You can convert the default textbox into the multiline textbox by setting the [multiline](../api/textbox/#multiline) API value as true or pass HTML5 textarea as element to the textbox.

> The multiline textbox allows you to resize it in vertical direction alone.

{% tab template="textbox/textarea" %}

```html
<template>
        <div class="multiline">
            <ejs-textbox name='default' :multiline="true" placeholder="Enter your address" value= 'Mr. Dodsworth Dodsworth, System Analyst, Studio 103, The Business Center'></ejs-textbox>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { TextBoxPlugin } from '@syncfusion/ej2-vue-inputs';
Vue.use(TextBoxPlugin);

export default {
 data: function(){
        return {
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
    #container {
        visibility: hidden;
        padding-left: 5%;
        width: 100%;
    }
    #loader {
        color: #008cff;
        font-family: 'Helvetica Neue','calibiri';
        font-size: 14px;
        height: 40px;
        left: 45%;
        position: absolute;
        top: 45%;
        width: 30%;
    }
    .multiline{
    margin: 10px auto;
    width: 30%;
  }

</style>
```

{% endtab %}

## Implementing floating label

You can achieve the floating label behavior in the multiline textbox by setting [floatLabelType](../api/textbox/#floatlabeltype) as 'Auto'. The placeholder text act as floating label to the multiline textbox. You can provide the placeholder text to the multiline textbox either by using the [placeholder](../api/textbox/#placeholder) property or placeholder attribute.

{% tab template="textbox/float" %}

```html
<template>
        <div class="multiline">
            <label class="label">Float label type auto</label>
            <ejs-textbox id='default' :multiline="true" placeholder="Enter your address" floatLabelType="Auto" maxlength="15"></ejs-textbox>
            <label class="label">Float label type always</label>
            <ejs-textbox id='default' :multiline="true" placeholder="Enter your address" floatLabelType="Always"></ejs-textbox>
            <label class="label">Float label type never</label>
            <ejs-textbox id='default' :multiline="true" placeholder="Enter your address" floatLabelType="Never"></ejs-textbox>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { TextBoxPlugin } from '@syncfusion/ej2-vue-inputs';
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
Vue.use(TextBoxPlugin);
Vue.use(ButtonPlugin);

export default {
 data: function(){
        return {
             clickHandler: function(event) {
                  this.$refs.textareaObj.addAttributes({maxlength: 15});
             }
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
    #container {
        visibility: hidden;
        padding-left: 5%;
        width: 100%;
    }
    #loader {
        color: #008cff;
        font-family: 'Helvetica Neue','calibiri';
        font-size: 14px;
        height: 40px;
        left: 45%;
        position: absolute;
        top: 45%;
        width: 30%;
    }
    .multiline{
    margin: 10px auto;
    width: 30%;
  }

</style>
```

{% endtab %}

## Auto resizing

By default, you can manually resize the multiline textbox. But you can also create an `auto resizing` multiline textbox with both the initial and dynamic value change. It can be done by calculating the height of the textarea in the created event for initial value update and in the input event for dynamic value update of the auto resize multiline textbox, as explained in the following code sample.

{% tab template="textbox/auto-resize" %}

```html
<template>
        <div class="multiline">
            <ejs-textbox ref="textareaObj" id='default' :multiline="true" value= 'Mr. Dodsworth Dodsworth, System Analyst, Studio 103, The Business Center' placeholder="Enter your address" floatLabelType="Auto" :input= "inputHandler" :created= "createHandler"></ejs-textbox>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { TextBoxPlugin } from '@syncfusion/ej2-vue-inputs';
Vue.use(TextBoxPlugin);

export default {
 data: function(){
        return {
            createHandler: (args) => {
                this.$refs.textareaObj.addAttributes({rows: 1});
                this.$refs.textareaObj.$el.style.height = "auto";
                this.$refs.textareaObj.$el.style.height = (this.$refs.textareaObj.$el.scrollHeight)+"px";
            },
            inputHandler: (args) => {
                args.event.currentTarget.style.height = "auto";
                args.event.currentTarget.style.height = (args.event.currentTarget.scrollHeight)+"px";
            }
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
    #container {
        visibility: hidden;
        padding-left: 5%;
        width: 100%;
    }
    #loader {
        color: #008cff;
        font-family: 'Helvetica Neue','calibiri';
        font-size: 14px;
        height: 40px;
        left: 45%;
        position: absolute;
        top: 45%;
        width: 30%;
    }
    .multiline{
        margin: 10px auto;
        width: 30%;
    }

</style>
```

{% endtab %}

## Disable resizing

By default, the multiline textbox is rendered with resizable. You can disable the resize of the multiline textbox by applying the following CSS styles.

```CSS
    textarea.e-input,
    .e-float-input textarea,
    .e-float-input.e-control-wrapper textarea,
    .e-input-group textarea,
    .e-input-group.e-control-wrapper textarea {
        resize: none;
    }

```

{% tab template="textbox/disable" %}

```html
<template>
        <div class="multiline">
            <ejs-textbox name='default' :multiline="true" placeholder="Enter your address" floatLabelType="Auto" cssClass="sample"></ejs-textbox>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { TextBoxPlugin } from '@syncfusion/ej2-vue-inputs';
Vue.use(TextBoxPlugin);

export default {
 data: function(){
        return {
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
    #container {
        visibility: hidden;
        padding-left: 5%;
        width: 100%;
    }
    #loader {
        color: #008cff;
        font-family: 'Helvetica Neue','calibiri';
        font-size: 14px;
        height: 40px;
        left: 45%;
        position: absolute;
        top: 45%;
        width: 30%;
    }
    .multiline{
        margin: 10px auto;
        width: 30%;
    }
    .sample textarea[name=default]{
        resize: none;
    }

</style>
```

{% endtab %}

## Limit the text length

By default, the text length of the multiline textbox is unlimited. You can limit the text length by setting the `maxLength` attribute using the [addAttributes](../api/textbox/#addattributes) method.

{% tab template="textbox/maxlength" %}

```html
<template>
        <div class="multiline">
            <label class="label">Add maxlength attribute through inline</label>
            <ejs-textbox id='default' :multiline="true" placeholder="Enter your address" floatLabelType="Auto" maxlength="15"></ejs-textbox>
            <label class="label">Add maxlength attribute through addAttributes method</label>
            <ejs-textbox id='default' :multiline="true" placeholder="Enter your address" floatLabelType="Auto" ref="textareaObj"></ejs-textbox>
             <ejs-button id='modalbtn' v-on:click.native="modalBtnClick">Add max length</ejs-button>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { TextBoxPlugin } from '@syncfusion/ej2-vue-inputs';
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
Vue.use(TextBoxPlugin);
Vue.use(ButtonPlugin);

export default {
 data: function(){
        return {
             modalBtnClick: function() {
                 this.$refs.textareaObj.addAttributes({maxlength: 15});
             }
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
    #container {
        visibility: hidden;
        padding-left: 5%;
        width: 100%;
    }
    #loader {
        color: #008cff;
        font-family: 'Helvetica Neue','calibiri';
        font-size: 14px;
        height: 40px;
        left: 45%;
        position: absolute;
        top: 45%;
        width: 30%;
    }
    .multiline{
    margin: 10px auto;
    width: 30%;
  }

</style>
```

{% endtab %}

## Count characters

You can show the number of characters entered inside the textarea by calculating the character count in the input event of multiline textbox. The character count is updated while entering or deleting any character inside the textarea. The character count shows how many characters can be entered or left to be entered.

{% tab template="textbox/auto-resize" %}

```html
<template>
        <div class="multiline">
            <ejs-textbox id='default' :multiline="true" placeholder="Enter your address" floatLabelType="Auto" :input= "inputHandler" maxlength="25"></ejs-textbox>
            <span id='numbercount'></span>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { TextBoxPlugin } from '@syncfusion/ej2-vue-inputs';
Vue.use(TextBoxPlugin);

export default {
 data: function(){
        return {
            inputHandler: (args) => {
                let word, addresscountRem, addressCount;
                word = args.value;
                addressCount = word.length;
                addresscountRem = document.getElementById('numbercount');
                addresscountRem.textContent = addressCount+"/25";
            }
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
    #container {
        visibility: hidden;
        padding-left: 5%;
        width: 100%;
    }
    #loader {
        color: #008cff;
        font-family: 'Helvetica Neue','calibiri';
        font-size: 14px;
        height: 40px;
        left: 45%;
        position: absolute;
        top: 45%;
        width: 30%;
    }
    .multiline{
    margin: 10px auto;
    width: 30%;
  }
  #numbercount{
    margin-left: 170px;
  }


</style>
```

{% endtab %}
