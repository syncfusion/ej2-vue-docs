# Animation

The **Animation** library is used to perform animation effects on HTML elements by running a sequence of frames.

## Animating a HTML Element

The `animate` method of `Animation` library can be used to animate the HTML elements. This method can also take additional `AnimationModel`. Refer the below code snippet to animate a multiple DOM element.

{% tab template="common/animation-multiple", isDefaultActive=true %}

```html

<template>
     <div id='container'>
        <div id='element1'></div>
        <div id='element2'></div>
    </div>
</template>
<script>
    import { Animation } from '@syncfusion/ej2-base';
    import Vue from "vue";
    export default {
        mounted: function () {
            var animation = new Animation({ duration: 5000 });
            animation.animate('#element1', { name: 'FadeOut' });
            animation.animate('#element2', { name: 'ZoomOut' });
        }
    }
</script>
<style>
  
#element1, #element2 {
    background: #333333;
    border: 1px solid #cecece;
    box-sizing: border-box;
    float: left;
    height: 100px;
    width:100px;
}

#element2 {
    margin-left: 20px;
}
</style>

```

{% endtab %}