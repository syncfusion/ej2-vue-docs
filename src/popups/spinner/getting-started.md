---
title: "Getting Started"
component: "Spinner"
description: "This example demonstrates how to create the Essential JS 2 Spinner control with its basic features in Vue application."
---

# Getting Started

Initialize the Spinner using `createSpinner` method and show/hide the spinner using `showSpinner` and `hideSpinner` methods accordingly. Set the target to the spinner to render it based on specific target.

The following steps explains you on how to create and how to show/hide your Spinner.

* Import the `createSpinner` method from `ej2-popups` library into your vue file as shown in below.

```typescript
import { createSpinner } from '@syncfusion/ej2-popups';
```

* Show and hide this spinner by using `showSpinner` and `hideSpinner` methods for loading in your page and import them in your vue file as shown in below.

```typescript
import { showSpinner, hideSpinner } from '@syncfusion/ej2-popups';
```

## Create the Spinner globally

The Spinner can be render globally in a page using public exported functions of the `ej2-popups` package.

```typescript
import { showSpinner, hideSpinner } from '@syncfusion/ej2-popups';
```

{% tab template="spinner/getting-started", isDefaultActive=true %}

```html
<template>
   <div id="app">

    </div>
</template>

<script>
import Vue from 'vue';
import { createSpinner, showSpinner, hideSpinner } from '@syncfusion/ej2-popups';

export default {
  name: 'app',
  mounted: function() {

    //createSpinner() method is used to create spinner
    createSpinner({
      // Specify the target for the spinner to show
      target: document.getElementById('app')
    });

    // showSpinner() will make the spinner visible
    showSpinner(document.getElementById('app'));

    setInterval(function(){
      // hideSpinner() method used hide spinner
      hideSpinner(document.getElementById('app'));
    }, 100000);
  }
}
</script>

<style>
 @import "../../node_modules/@syncfusion/ej2-popups/styles/material.css";
</style>
```

{% endtab %}