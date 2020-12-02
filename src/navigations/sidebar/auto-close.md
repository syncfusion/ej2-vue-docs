---
title: "Auto Close"
component: "Sidebar"
description: "Sidebar can be initialized in expand or collapsed state in user specified resolutions."
---

# Auto-close

The Sidebar often behaves differently on mobile display and differently on desktop display. It has an
effective feature that offers to set it in opened or closed state depending on the specified resolution. This
is achieved through [mediaQuery](../api/sidebar#mediaquery) property that allows you to set the Sidebar in an expanded state or collapsed
state only in user-defined resolution.

{% tab template="sidebar/getting-started", isDefaultActive=true %}

```html
<template>
<div id="app">
    <ejs-sidebar id="default-sidebar"  :width="width" :mediaQuery= "mediaQuery">
      <div class="title"> Sidebar content</div>
    </ejs-sidebar>
    <div>
      <div class="title">Main content</div>
        <div class="sub-title">
            * Sidebar will collapse and expand in based on screen resolution automatically
        </div>
    </div>
</div>
</template>
<script>
import Vue from 'vue';
import { SidebarPlugin } from '@syncfusion/ej2-vue-navigations';

Vue.use(SidebarPlugin);
export default {
    data () {
        return {
          width: '280px',
          mediaQuery: window.matchMedia('(min-width: 600px)'),
        }
    }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";

.title {
    text-align: center;
    font-size: 20px;
    padding: 15px;
}

.sub-title {
    text-align: center;
    font-size: 12px;
    padding: 10px;
}

.center {
    text-align: center;
    display: none;
    font-size: 13px;
    font-weight: 400;
    margin-top: 20px;
}

#default-sidebar {
    background-color: rgb(25, 118, 210);
    color: #ffffff;
}

</style>
```

{% endtab %}

## Open close

* In the following sample,the Sidebar will be in an expanded state only in resolution below `400px`.

{% tab template="sidebar/getting-started", isDefaultActive=true %}

```html
<template>
<div id="app">
    <ejs-sidebar id="default-sidebar"  :width="width" :mediaQuery= "mediaQuery">
      <div class="title"> Sidebar content</div>
    </ejs-sidebar>
    <div>
        <div class="title">Main content</div>
        <div class="sub-title">
            * Sidebar will collapse and expand in based on screen resolution automatically
        </div>
    </div>
</div>
</template>
<script>
import Vue from 'vue';
import { SidebarPlugin } from '@syncfusion/ej2-vue-navigations';

Vue.use(SidebarPlugin);
export default {
    data () {
        return {
          width: '280px',
          mediaQuery: window.matchMedia('(max-width: 400px)'),
        }
    }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";

.title {
    text-align: center;
    font-size: 20px;
    padding: 15px;
}

.sub-title {
    text-align: center;
    font-size: 12px;
    padding: 10px;
}

.center {
    text-align: center;
    display: none;
    font-size: 13px;
    font-weight: 400;
    margin-top: 20px;
}

#default-sidebar {
    background-color: rgb(25, 118, 210);
    color: #ffffff;
}
</style>
```

{% endtab %}