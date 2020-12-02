---
title: "Vue Toast Animations"
component: "Toast"
description: "The Toast component supports custom animations for both show and hide actions by providing an animation option."
---

# Animations

The toast component supports custom animations for both shows and hide actions from the provided animation option of the `Animation` library.

The default animation is given as `FadeIn` for showing the toast and `FadeOut` for hiding the toast.

The following sample demonstrates some types of animations that suit toast. You can check all the animation effects here.

{% tab template="toast/animations", isDefaultActive=true %}

```html
<template>
   <div id='app'>
        <div id="default" style="padding-bottom:75px;">
            <div class='row'>
                 <ejs-button ref='showButtonRef' class="e-btn" id="show_toast" v-on:click.native="showBtnClick">Show Toast</ejs-button>
             </div>
            <div class='row'>
                <div class="col-xs-6 col-sm-6 col-lg-6 col-md-6">
                    <label> Show Animation </label>
                </div>
                <div class="col-xs-6 col-sm-6 col-lg-6 col-md-6">
                     <ejs-dropdownlist ref='showAnimationRef' id='ShowAnimation' :dataSource='animationData' :fields='easeFields'
                        placeholder='Select a animate type' :change='showChange' :value='animationValue'></ejs-dropdownlist>
                </div>
            </div>
            <div class='row'>
                <div class="col-xs-6 col-sm-6 col-lg-6 col-md-6">
                    <label> Hide Animation </label>
                </div>
                <div class="col-xs-6 col-sm-6 col-lg-6 col-md-6">
                    <ejs-dropdownlist ref='hideAnimationRef' id='HideAnimation' :dataSource='animationData' :fields='easeFields'
                        placeholder='Select a animate type' :change='hideChange' :value='animationValue'></ejs-dropdownlist>
                </div>
            </div>
        </div>
         <ejs-toast ref='elementRef' id='element' :position='position' title='Matt sent you a friend request' content='You have a new friend request yet to accept'></ejs-toast>
    </div>
</script>
</div>
</template>

<script>
import Vue from "vue";
import { ToastPlugin, Toast } from "@syncfusion/ej2-vue-notifications";
import { DropDownListPlugin, DropDownList, ChangeEventArgs } from '@syncfusion/ej2-vue-dropdowns';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.use(ToastPlugin);
Vue.use(ButtonPlugin);
Vue.use(DropDownListPlugin);
export default {
  name: 'app',
   data: function(){
        return {
            position: { X: 'Right', Y: 'Bottom' },
            easeFields: { text: 'Text', value: 'Id' },
            animationData: [
                { Id: 'FadeIn', Text: 'Fade In' },
                { Id: 'FadeZoomIn', Text: 'Fade Zoom In' },
                { Id: 'FadeZoomOut', Text: 'Fade Zoom Out' },
                { Id: 'FlipLeftDownIn', Text: 'Flip Left Down In' },
                { Id: 'FlipLeftDownOut', Text: 'Flip Left Down Out' },
                { Id: 'FlipLeftUpIn', Text: 'Flip Left Up In' },
                { Id: 'FlipLeftUpOut', Text: 'Flip Left Up Out' },
                { Id: 'FlipRightDownIn', Text: 'Flip Right Down In' },
                { Id: 'FlipRightDownOut', Text: 'Flip Right Down Out' },
                { Id: 'FlipRightUpIn', Text: 'Flip Right Up In' },
                { Id: 'FlipRightUpOut', Text: 'Flip Right Up Out' },
                { Id: 'SlideBottomIn', Text: 'Slide Bottom In' },
                { Id: 'SlideBottomOut', Text: 'Slide Bottom Out' },
                { Id: 'SlideLeftIn', Text: 'Slide Left In' },
                { Id: 'SlideLeftOut', Text: 'Slide Left Out' },
                { Id: 'SlideRightIn', Text: 'Slide Right In' },
                { Id: 'SlideRightOut', Text: 'Slide Right Out' },
                { Id: 'SlideTopIn', Text: 'Slide Top In' },
                { Id: 'SlideTopOut', Text: 'Slide Top Out' },
                { Id: 'ZoomIn', Text: 'Zoom In' },
                { Id: 'ZoomOut', Text: 'Zoom Out' }
            ],
            animationValue: 'FadeIn'
        }
    },
  mounted: function() {
      this.toastObj = document.getElementById('element').ej2_instances[0];
      this.toastObj.show();
  },
  methods: {
      showBtnClick: function(args){
          this.toastObj.show();
      },
      showChange: function(args){
          this.toastObj.animation.show.effect = args.value;
      },
      hideChange: function(args){
          this.toastObj.animation.hide.effect = args.value;
      },
  }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-vue-notifications/styles/material.css";
</style>

<style lang="scss">
#loader {
    color: #008cff;
    height: 40px;
    left: 45%;
    position: absolute;
    top: 45%;
    width: 30%;
}
#app {
    max-width: 200px;
}
.row {
    margin: 15px;
}
</style>

```

{% endtab %}