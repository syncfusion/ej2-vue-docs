---
title: "Vue Dialog Animation"
component: "Dialog"
description: "Explains how to open or close the modal dialog component with various animation effects, duration, and delay (animation dialog box)."
---

# Animation

The Dialog can be animated during the open and close actions. Also, user can customize animation's `delay`, `duration` and `effect`.

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
delay</td><td>
The Dialog animation will start with the mentioned delay</td></tr>
<tr>
<td>
duration</td><td>
Specifies the animation duration to complete with one animation cycle</td></tr>
<tr>
<td>
effect</td><td>
Specifies the animation effects of Dialog open and close actions effect.
<br /><br />
List of supported animation effects:
<br />
'Fade' | 'FadeZoom' | 'FlipLeftDown' | 'FlipLeftUp' | 'FlipRightDown' | 'FlipRightUp' | 'FlipXDown' |
'FlipXUp' | 'FlipYLeft' | 'FlipYRight' | 'SlideBottom' | 'SlideLeft' | 'SlideRight' | 'SlideTop' |
'Zoom'| 'None'
<br /><br />
If the user sets ‘Fade’ effect, then the Dialog will open with ‘FadeIn’ effect and close with ‘FadeOut’ effect
</td></tr>
</table>

In the below sample, `Zoom` effect is enabled. So, The Dialog will open with `ZoomIn`
and close with `ZoomOut` effects.

{% tab template="dialog/animation", isDefaultActive=true %}

```html
<template>
  <div>
     <div id="target" class="control-section">
        <div id='customization'>
            <div class='animate'>
               <ejs-button v-on:click.native='buttonClick' id='Zoom'>Zoom</ejs-button>
            </div>
            <div class='animate'>
                <ejs-button v-on:click.native='buttonClick' id='FlipXDown'>FlipX Down</ejs-button>
            </div>
            <div class='animate'>
                <ejs-button v-on:click.native='buttonClick' id='FlipXUp'>FlipX Up</ejs-button>
            </div>
            <div class='animate'>
                <ejs-button v-on:click.native='buttonClick' id='FlipYLeft'>FlipY Left</ejs-button>
            </div>
            <div class='animate'>
                <ejs-button v-on:click.native='buttonClick' id='FlipYRight'>FlipY Right</ejs-button>
            </div>
        </div>
        <ejs-dialog id='dialog' header='Animation Dialog' content='The dialog is configured with animation effect. It is opened or closed with "Zoom In or Out" animation.' showCloseIcon='true' :isModal='isModal' :animationSettings='animationSettings' width='285px' ref='dialogObj'
            target='#target' :buttons='dlgButton'>
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
            dlgButton: [{ 'click': () => { this.$refs.dialogObj.hide(); }, buttonModel: { content: 'OK', isPrimary: true }}],
            isModal: true,
            animationSettings: { effect: 'Zoom' }
        }
    },
    methods: {
        buttonClick: function(e){
            var effect = e.target.getAttribute('id');
            var txt = e.target.parentElement.innerText;
            txt = (txt === 'Zoom In/Out') ? 'Zoom In or Out' : txt;
            this.$refs.dialogObj.content = 'The dialog is configured with animation effect. It is opened or closed with "' + txt + '" animation.';
            this.$refs.dialogObj.animationSettings = { effect: effect, duration: 400};
            setTimeout(() => {
                this.$refs.dialogObj.show();
            },400);
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
    #customization {
        display: table;
        margin: 0 auto;
    }
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
        min-height: 340px;
     }
    .animate {
        display: table-cell;
        padding-left: 20px;
    }
    #customization .e-btn.e-outline:hover,
    #customization .e-css.e-btn.e-outline:hover,
    #customization .e-btn.e-outline:hover:focus,
    #customization .e-css.e-btn.e-outline:hover:focus,
    #customization .e-btn.e-outline:focus,
    #customization .e-css.e-btn.e-outline:focus {
        background-color: #ffffff;
        border-color: #0078d6;
        color:#0078d6;
        outline: none;
    }
</style>
```

{% endtab %}