# Change sub menu position

The submenu position can be changed by using the [`beforeOpen`](../../api/menu/#beforeopen) event. Assign the top and left position where you want to open the submenu to the [`beforeOpen`](../../api/menu/#beforeopen) event arguments `args.top` and `args.left` respectively.

In the below sample, the sub menu opens above the parent menu item.

{% tab template="menu/getting-started", isDefaultActive=true %}

```html
<template>
    <div>
        <ejs-menu :items='menuItems' :beforeOpen='onBeforeOpen'></ejs-menu>
    </div>
</template>

<script>
import Vue from 'vue';
import { MenuPlugin } from "@syncfusion/ej2-vue-navigations";
import { enableRipple, closest } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(MenuPlugin);

export default {
  data: function() {
    return {
        // Menu items definition
        menuItems: [
        {
            text: 'File',
            items: [
                { text: 'Open' },
                { text: 'Save' },
                { text: 'Exit' }]
        },
        {
            text: 'Edit',
            items: [
                { text: 'Cut' },
                { text: 'Copy' },
                { text: 'Paste' }]
        },
        {
            text: 'View',
            items: [
                { text: 'Toolbar' },
                { text: 'Sidebar' }]
        },
        {
            text: 'Tools',
            items: [
                { text: 'Spelling & Grammar' },
                { text: 'Customize' },
                { text: 'Options' }]
        },
        { text: 'Go' },
        { text: 'Help' }
    ]
    };
  },
   methods: {
        onBeforeOpen(args) {
            // Getting parent menu item element offset
            let relativeOffset = closest(args.event.target, '.e-menu-item').getBoundingClientRect();
            // Getting sub menu wrapper element using closest method
            let subMenuEle = closest(args.element, '.e-menu-wrapper');
            subMenuEle.style.display = 'block';
            args.top = (relativeOffset.top - subMenuEle.getBoundingClientRect().height) + pageYOffset;
            args.left = relativeOffset.left + pageXOffset;
            subMenuEle.style.display = '';
        }
   }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";

body {
    margin-top: 200px;
    text-align: center;
}
</style>
```

{% endtab %}

>> For custom positioning, set both `top` and `left` position in the [`beforeOpen`](../../api/menu/#beforeopen) event.