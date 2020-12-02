---
title: "Accordion Getting Started"
component: "Accordion"
description: "This section explains how to create Accordion control in an Vue application with its basic features."
---

# Getting Started

This section briefly explains about how to create a simple **Accordion** using VueJS and
configure the Accordion items using Essential JS 2.

## Dependencies

The following list of dependencies are required to use the Accordion component in your application.

```javascript
|-- @syncfusion/ej2-vue-navigations
  |-- @syncfusion/ej2-base
  |-- @syncfusion/ej2-vue-base
  |-- @syncfusion/ej2-navigations
    |-- @syncfusion/ej2-inputs
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
You can choose the component that you want to install. For this application, we are going to use Accordion component.

To install Accordion component, use the following command

```bash
npm install @syncfusion/ej2-vue-navigations –save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.
* Vue.use()
* Vue.component()

### Using Vue.use()

Import the Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { AccordionPlugin } from '@syncfuion/ej2-vue-navigations';

Vue.use(AccordionPlugin);
```

> By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the Component and Component Plugin from EJ2 Vue Package,
register the same using the Vue.component() with name of Component from ComponentPlugin
and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { AccordionComponent, AccordionPlugin } from '@syncfusion/ej2-vue-navigations';

Vue.component(AccordionPlugin.name, AccordionComponent);
```

Note: By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Creating Vue Sample

Add the EJ2 Vue Accordion using `<ejs-accordion>` to the `<template>` section of the `App.vue` file in src directory,
the content attribute of the Accordion component is provided as name in data option in the `<script>` section.

```html
<template>
    <div id="app">
    <ejs-accordion >
            <e-accordionitems>
        <e-accordionitem expanded='true' header='ASP.NET' content='Microsoft ASP.NET is a set of technologies in the Microsoft .NET Framework for building Web applications and XML Web services.'></e-accordionitem>
        <e-accordionitem header='ASP.NET MVC' content='The Model-View-Controller (MVC) architectural pattern separates an application into three main components: the model, the view, and the controller.'></e-accordionitem>
        <e-accordionitem header='JavaScript' content='JavaScript (JS) is an interpreted computer programming language.It was originally implemented as part of web browsers so that client-side scripts could interact with the user, control the browser, communicate asynchronously, and alter the document content that was displayed.'></e-accordionitem>
      </e-accordionitems>
    </ejs-accordion>
  </div>
</template>
<script>
import Vue from 'vue';
import { AccordionPlugin } from '@syncfusion/ej2-vue-navigations';

Vue.use(AccordionPlugin);
export default {
  name: 'app',
}
</script>
```

## Adding CSS Reference

Add Accordion component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
</style>
```

## Running the Application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

{% tab template="accordion/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <ejs-accordion >
            <e-accordionitems>
        <e-accordionitem expanded='true' header='ASP.NET' content='Microsoft ASP.NET is a set of technologies in the Microsoft .NET Framework for building Web applications and XML Web services.'></e-accordionitem>
        <e-accordionitem header='ASP.NET MVC' content='The Model-View-Controller (MVC) architectural pattern separates an application into three main components: the model, the view, and the controller.'></e-accordionitem>
        <e-accordionitem header='JavaScript' content='JavaScript (JS) is an interpreted computer programming language.It was originally implemented as part of web browsers so that client-side scripts could interact with the user, control the browser, communicate asynchronously, and alter the document content that was displayed.'></e-accordionitem>
      </e-accordionitems>
    </ejs-accordion>
  </div>
</template>
<script>
import Vue from 'vue';
import { AccordionPlugin } from '@syncfusion/ej2-vue-navigations';

Vue.use(AccordionPlugin);
export default {
  name: 'app',
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
</style>
```

{% endtab %}

## Initialize the Accordion using HTML elements

The Accordion component can be rendered based on the given HTML element using `<ejs-accordion>`.
You need to follow the below structure of HTML elements to render the Accordion inside the `<ejs-accordion>` tag.

```html
  <ejs-accordion>   --> Root Accordion Element
       <div>      --> Accordion Item Container
            <div>   --> Accordion Header Container
                <div> </div> --> Accordion Header
            </div>
            <div>  --> Accordion Panel Container
                <div> </div> --> Accordion Content
             </div>
        </div>
  </ejs-accordion>
```

{% tab template="accordion/accordion-container" %}

```html
<template>
    <div id="app">
    <ejs-accordion>
          <div>
                <div>
                    <div> ASP.NET </div>
                </div>
                <div>
                    <div> Microsoft ASP.NET is a set of technologies in the Microsoft .NET Framework for building Web applications
                        and XML Web services </div>
                </div>
            </div>
            <div>
                <div>
                    <div> ASP.NET MVC </div>
                </div>
                <div>
                    <div> The Model-View-Controller (MVC) architectural pattern separates an application into three main components:
                        the model, the view, and the controller </div>
                </div>
            </div>
            <div>
                <div>
                    <div> JavaScript </div>
                </div>
                <div>
                    <div> JavaScript (JS) is an interpreted computer programming language.It was originally implemented as part
                        of web browsers so that client-side scripts could interact with the user, control the browser </div>
                </div>
            </div>
    </ejs-accordion>
  </div>
</template>
<script>
import Vue from 'vue';
import { AccordionPlugin } from '@syncfusion/ej2-vue-navigations';

Vue.use(AccordionPlugin);
export default {
  name: 'app',
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
</style>
```

{% endtab %}