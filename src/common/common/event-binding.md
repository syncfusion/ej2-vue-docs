# Event Binding

Syncfusion Vue UI components support Binding of both Custom and Native Events. For more information, refer official [Vue Documentation](https://vuejs.org/v2/guide/events.html)

## Custom Events

Custom events are the `Component` specific events provided by Syncfusion Vue components supported through `v-on` directive. The Syntax for Binding Custom Event is `v-on:event-name="function"`.

Refer the below code snippet for Binding of Custom Events.

```html

// Custom Event Binding

<template>
  <div id="calendar">
    <ejs-calendar v-on:created="display" />
  </div>
</template>

<script>
import Vue from 'vue';
import { CalendarPlugin } from '@syncfusion/ej2-vue-calendars';
Vue.use(CalendarPlugin);

export default {
  methods: {
    display: function() {
      window.alert('Calendar Created');
    }
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";

  #calendar {
    max-width: 250px;
    margin: 0 auto;
  }
</style>

```

## Native Events

Native events are the DOM events of Syncfusion Vue component's root element. `.native` modifier for `v-on` directive is used for binding these events. The Syntax for Binding Native Event is `v-on:event-name.native="function"`.

Refer the below code snippet for Binding Native Events.

```html

//Native Event Binding

<template>
  <div id="button">
    <ejs-button :content="name" v-on:click.native="clicked"></ejs-button>
  </div>
</template>

<script>
import Vue from 'vue';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
Vue.use(ButtonPlugin);

export default {
  data () {
    return {
      name: "Button"
    };
  },
  methods: {
    clicked: function() {
      window.alert('Button Clicked');
    }
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
</style>

```
