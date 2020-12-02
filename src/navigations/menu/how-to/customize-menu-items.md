# Customize menu items

## Add or remove menu items

Menu items can be added or removed using the [`insertAfter`](../../api/menu#insertafter), [`insertBefore`](../../api/menu#insertbefore) and [`removeItems`](../../api/menu#removeitems) methods.

In the following example, the **Europe** menu items are added before the **Oceania** item, the **Africa** menu items are added after the **Asia**, and the **South America** and **Mexico** items are removed from menu.

{% tab template="menu/getting-started" %}

```html
<template>
<div>
<ejs-menu ref="menu" id="menu" :items='menuItems' :fields='menuFields' :created='onCreated'></ejs-menu>
</div>
</template>

<script>
import Vue from 'vue';
import { MenuPlugin } from "@syncfusion/ej2-vue-navigations";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(MenuPlugin);

export default {
   data: function() {
        return {
           menuItems:  [
            {
                continent: 'Asia',
                countries: [
                    { country: 'China' },
                    { country: 'India' },
                    { country: 'Japan' }
                ]
            },
            {
                continent: 'North America',
                countries: [
                    { country: 'Canada' },
                    { country: 'Mexico' },
                    { country: 'USA' }
                ]
            },
            {
                continent: 'South America',
                countries: [
                    { country: 'Brazil' },
                    { country: 'Colombia' },
                    { country: 'Argentina' }
                ]
            },
            {
                continent: 'Oceania',
                countries: [
                    { country: 'Australia' },
                    { country: 'New Zealand' },
                    { country: 'Samoa' },
                ]
            },
            { continent: 'Antarctica' }
        ],
        menuFields: {
            text: ['continent', 'country'],
            children: ['countries']
        }
     };
   },
   methods: {
       onCreated: function(args) {
            var insertItem = [
                {
                    continent: 'Europe',
                    countries: [
                        { country: 'Finland' },
                        { country: 'Austria' }
                    ]
                }
            ];
            this.$refs.menu.insertBefore(insertItem, 'Oceania', false);
            insertItem = [
                {
                    continent: 'Africa',
                    countries: [
                        { country: 'Nigeria' }
                    ]
                }
            ];
            this.$refs.menu.insertAfter(insertItem, 'Oceania', false);
            this.$refs.menu.removeItems(['South America', 'Mexico'], false);
       }
   }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";

body {
    margin-top: 100px;
    text-align: center;
}

</style>
```

{% endtab %}

> To process items with `ID` values, set `isUnique` to `true`.

## Enable or disable menu items

You can enable and disable the menu items using the [`enableItems`](../../api/menu#enableitems) method in Menu. To enable menuItems, set the `enable` property in argument to `true` and vice-versa.

Install Syncfusion `Buttons` packages using below command.

```bash
npm install @syncfusion/ej2-vue-buttons --save
```

In the following example, the **Directory** header item, **Conferences**, and **Music** sub menu items are disabled.

{% tab template="menu/getting-started" %}

```html
<template>
    <div>
        <ejs-button ref='enableAll'  v-on:click.native="btnClick">Enable all items</ejs-button>
        <div class="menu-section">
            <ejs-menu ref="menu" id="menu" :items='menuItems' :created='onCreated' :beforeOpen='beforeOpen'></ejs-menu>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MenuPlugin } from "@syncfusion/ej2-vue-navigations";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(MenuPlugin);
Vue.use(ButtonPlugin);

var disableItems = ['Conferences', 'Music', 'Directory'];

export default {
   data: function() {
        return {
           menuItems:  [
    {
        text: 'Events',
        items: [
            { text: 'Conferences' },
            { text: 'Music' },
            { text: 'Workshops' }
        ]
    },
    {
        text: 'Movies',
        items: [
            { text: 'Now Showing' },
            { text: 'Coming Soon' }
        ]
    },
    {
        text: 'Directory',
        items: [
            { text: 'Media Gallery' },
            { text: 'Newsletters' }
        ]
    },
    {
        text: 'Queries',
        items: [
            { text: 'Our Policy' },
            { text: 'Site Map' }
        ]
    },
    { text: 'Services' }
]
     };
   },
   methods: {
       beforeOpen: function(args) {
        for (var i = 0; i  < args.items.length; i++) {
            if (disableItems.indexOf(args.items[i].text) > -1) {
                this.$refs.menu.enableItems([args.items[i].text], false, false);
            }
        }
       },
       btnClick: function(event) {
           this.$refs.menu.enableItems(disableItems, true, false);
           disableItems = [];
       },
       onCreated: function(args) {
           this.$refs.menu.enableItems(disableItems, false, false);
       }
   }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";

.menu-section {
    margin-top: 100px;
    text-align: center;
}

</style>
```

{% endtab %}

> To disable sub menu items, use the [`beforeOpen`](../../api/menu#beforeopen) event.

## Hide or show menu items

You can show or hide the menu items using the [`showItems`](../../api/menu#showitems) and [`hideItems`](../../api/menu#hideitems) methods.

{% tab template="menu/getting-started" %}

```html
<template>
    <div>
        <ejs-button ref='enableAll' v-on:click.native="btnClick">Show all items</ejs-button>
        <div class="menu-section">
            <ejs-menu ref="menu" id="menu" :items='menuItems' :created='onCreated' :beforeOpen='beforeOpen'></ejs-menu>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MenuPlugin } from "@syncfusion/ej2-vue-navigations";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(MenuPlugin);
Vue.use(ButtonPlugin);

var hiddenItems = ['Workshops', 'Music', 'Movies'];

export default {
   data: function() {
        return {
           menuItems:  [
    {
        text: 'Events',
        items: [
            { text: 'Conferences' },
            { text: 'Music' },
            { text: 'Workshops' }
        ]
    },
    {
        text: 'Movies',
        items: [
            { text: 'Now Showing' },
            { text: 'Coming Soon' }
        ]
    },
    {
        text: 'Directory',
        items: [
            { text: 'Media Gallery' },
            { text: 'Newsletters' }
        ]
    },
    {
        text: 'Queries',
        items: [
            { text: 'Our Policy' },
            { text: 'Site Map' }
        ]
    },
    { text: 'Services' }
]
     };
   },
   methods: {
       beforeOpen: function(args) {
        for (var i = 0; i  < args.items.length; i++) {
            if (hiddenItems.indexOf(args.items[i].text) > -1) {
                this.$refs.menu.hideItems([args.items[i].text], false);
            }
        }
       },
       btnClick: function(event) {
           this.$refs.menu.showItems(hiddenItems, false);
           hiddenItems = [];
       },
       onCreated: function(args) {
           this.$refs.menu.hideItems(hiddenItems, false);
       }
   }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";

.menu-section {
    margin-top: 100px;
    text-align: center;
}

</style>
```

{% endtab %}

> Using the [`beforeOpen`](../../api/menu#beforeopen) event, you can hide the sub menu items as in the above example since the menu supports to hide items only for headers initially.
