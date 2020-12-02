---
title: "Vue Toast Accessibility"
component: "Toast"
description: "The Toast component has accessibility support to access the features via keyboard, screen readers, or other assistive technology devices."
---

# Accessibility

The toast component has been designed with [WAI-ARIA](https://www.w3.org/TR/wai-aria/) specifications in mind by applying the prompt WAI-ARIA roles, states, and properties with the keyboard support. It helps users who use assistive WAI-ARIA accessibility support, which is achieved using attributes.

It provides information about the elements in a document for assistive technology.

The toast component implements the keyboard navigation support by using the following [WAI-ARIA practices](https://www.w3.org/TR/wai-aria-practices/) and is tested in major screen readers.

## ARIA attributes

<!-- markdownlint-disable MD033 -->

| Class | Description |
| -------- | -------- |
| role | <b>alert:</b> Identifies the element as a container when alert content will be added or updated. |

{% tab template="toast/accessibility", isDefaultActive=true %}

```html
<template>
   <div id='app'>
         <ejs-toast ref='elementRef' timeOut=0 id='element' title='Matt sent you a friend request' content='You have a new friend request yet to accept'></ejs-toast>
    </div>
</template>

<script>
import Vue from "vue";
import { ToastPlugin, Toast } from "@syncfusion/ej2-vue-notifications";

Vue.use(ToastPlugin);
export default {
  name: 'app',
  mounted: function() {
      this.$refs.elementRef.show();
  }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-vue-notifications/styles/material.css";
</style>

```

{% endtab %}