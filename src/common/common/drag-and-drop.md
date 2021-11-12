# Drag and Drop

Drag and Drop is supported through two libraries. Those are [`Draggable`](https://ej2.syncfusion.com/documentation/api/base/draggable) and [`Droppable`](https://ej2.syncfusion.com/documentation/api/base/droppable). Draggable makes DOM to be dragged using mouse or touch gestures and Droppable mark required DOM as droppable zone.

## Initializing Draggable

You can make any element draggable by passing the element to Draggable constructor. Refer the following code snippet to enable draggable for the DOM element.

 {% tab template="common/draggable-default" %}

```html
<template>
    <div id='container'>
        <div id='element1'>
            <p>Draggable Element </p>
        </div>
    </div>
</template>
<script>
    import { Draggable } from '@syncfusion/ej2-base';
    import Vue from "vue";
    export default {
        mounted: function () {

            var dragElement = document.getElementById('element1');
            var draggable = new Draggable(dragElement, { clone: false });
        }
    }
</script>
<style>
    #element1,
    .helper {
        height: 100px;
        width: 150px;
        border: 1px solid #cecece;
        cursor: move;
        user-select: none;
        color: #6a77a7;
        touch-action: none;
    }

    p {
        padding-top: 23px;
        text-align: center;
    }

    .helper {
        opacity: 0.6;
    }

    .select {
        border: 1px solid #cccccc;
        background: #ededed;
    }
</style>

```
    .helper {
        opacity: 0.6;
    }

    .select {
        border: 1px solid #cccccc;
        background: #ededed;
    }
</style>

```
 {% endtab %}

## Creating Droppable zone

You can convert any DOM element as a droppable zone, which accepts the draggable elements. Refer the following code snippet to enable droppable zone.

{% tab template="common/droppable-default"  %}

```html
<template>
    <div id='droppable'>
        <p class='drop'>
            <span>Drop Target</span>
        </p>
    </div>
</template>
<script>
    import { Droppable } from '@syncfusion/ej2-base';
    import Vue from "vue";
    export default {
        mounted: function () {

            var droppable = new Droppable(document.getElementById('droppable'));

        }
    }
</script>
<style>
    .drop {
        padding-top: 23px;
        text-align: center;

    }

    #droppable {
        margin: 5px;
        line-height: 170px;
        font-size: 14px;
        width: 250px;
        border: 1px solid #cecece;
        background: #f6f6f6;
        touch-action: none;
    }
</style>
```

 {% endtab %}

## Defining Drop Action

To define a drop action set [`drop`](https://ej2.syncfusion.com/documentation/api/base/droppable#drop) callback function during droppable object creation. You can get details of dropped element through dropped element property in event argument. Refer the following code snippet to use basic drag and drop action.

{% tab template="common/drag-drop-action", es5Template="drag-drop-template" %}

```html

<template>
    <div id='container'>
        <div id='droppable'>
            <p class='drop'><span>Drop Target </span></p>
        </div>
        <div id='element1'>
            <p class='drag-text'>Drag </p>
        </div>

    </div>
</template>
<script>
    import { Draggable, Droppable } from '@syncfusion/ej2-base';
    import Vue from "vue";
    export default {
        mounted: function () {
            var draggable = new Draggable(document.getElementById('element1'), {
                clone: false
            });
            var droppable = new Droppable(document.getElementById('droppable'), {
                drop: (e) => {
                    e.droppedElement.querySelector('.drag-text').textContent = 'Dropped';
                }
            });
        }
    }
</script>
<style>
    #element1 {
        height: 100px;
        width: 150px;
        border: 1px solid #cecece;
        cursor: move;
        background: #cdffe3;
        user-select: none;
        touch-action: none;
    }

    #element1 p {
        padding-top: 23px;
        text-align: center;

    }

    .drop {
        padding-top: 23px;
        text-align: center;

    }

    #droppable {
        margin: 5px;
        line-height: 170px;
        font-size: 14px;
        width: 250px;
        border: 1px solid #cecece;
        background: #f6f6f6;
        touch-action: none;
    }
</style>
```

 {% endtab %}

## See Also

[Define handle element for Draggable](https://ej2.syncfusion.com/documentation/api/base/draggable#handle)<br/>
[Restricting Draggable within conainer](https://ej2.syncfusion.com/documentation/api/base/draggable#dragarea)<br>
[Visual feedback of draggable element](https://ej2.syncfusion.com/documentation/api/base/draggable#clone)<br>
[Accepting specific drag element in droppable](https://ej2.syncfusion.com/documentation/api/base/droppable#accept)