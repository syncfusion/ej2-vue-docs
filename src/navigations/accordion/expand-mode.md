---
title: "Accordion Expand mode"
component: "Accordion"
description: "The Accordion control supports expand mode options, that specify the types of expand mode while expanding or collapsing an item."
---

# ExpandMode

 The Accordion supports the two listed types of expand modes while expanding or collapsing the item.

* Single
* Multiple

## Single

The property enables to expand only one Accordion item at a time. If you expand any new item, the previously expanded one is collapsed and
new item changed to expanded state.

{% tab template="accordion/expandmode/single", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <ejs-accordion expandMode='Single'>
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

## Multiple

Default expand mode of the Accordion is `Multiple`. It enables you to expand more than one Accordion item at a time. Expand/collapse action
can also be toggled by clicking on it again. For example, expanded item is collapsed when you click on it again.

{% tab template="accordion/expandmode/multiple", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <ejs-accordion expandMode='Multiple'>
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

## See Also

* [How to keep single pane open always](./how-to/to-keep-single-pane-open-always/)