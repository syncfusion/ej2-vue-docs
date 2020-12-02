---
title: "Menu use case scenarios"
component: "Menu"
description: "Vue Menu how to section, toolbar menu, mobile menu, custom menu."
---

# Use case scenarios

## Scrollable menu

The menu component supports horizontal and vertical scrolling to render large menus and submenus in an adaptive way. This can be achieved by enabling the [`enableScrolling`](../api/menu/#enablescrolling) property and by restricting the corresponding menu/submenu size.

{% tab template="menu/getting-started", isDefaultActive=true %}

```html
<template>
    <div>
        <ejs-menu :items='menuItems' :beforeOpen='onBeforeOpen' cssClass='e-scrollable-menu' :enableScrolling='true'></ejs-menu>
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
            text: 'Appliances',
            items: [
                {
                    text: 'Kitchen',
                    items: [
                        { text: 'Electric Cookers' },
                        { text: 'Coffee Makers' },
                        { text: 'Blenders' },
                        { text: 'Microwave Ovens' }
                    ]
                },
                {
                    text: 'Television',
                    items: [
                        { text: 'Our Exclusive TVs' },
                        { text: 'Smart TVs' },
                        { text: 'Big Screen TVs' }
                    ]
                },
                {
                    text: 'Washing Machine'
                },
                {
                    text: 'Refrigerators'
                },
                {
                    text: 'Air Conditioners',
                    items: [
                        { text: 'Inverter ACs' },
                        { text: 'Split ACs' },
                        { text: 'Window ACs' },
                    ]
                },
                {
                    text: 'Water Purifiers'
                },
                {
                    text: 'Air Purifiers'
                },
                {
                    text: 'Chimneys'
                },
                {
                    text: 'Inverters'
                },
                {
                    text: 'Healthy Living'
                },
                {
                    text: 'Vacuum Cleaners'
                },
                {
                    text: 'Room Heaters'
                },
                {
                    text: 'New Launches'
                }
            ]
        },
        {
            text: 'Accessories',
            items: [
                {
                    text: 'Mobile',
                    items: [
                        { text: 'Headphones' },
                        { text: 'Memory Cards' },
                        { text: 'Power Banks' },
                        { text: 'Mobile Cases' },
                        { text: 'Screen Protectors' }
                    ]
                },
                {
                    text: 'Laptops'
                },
                {
                    text: 'Desktop PC',
                    items: [
                        { text: 'Pendrives' },
                        { text: 'External Hard Disks' },
                        { text: 'Monitors' },
                        { text: 'Keyboards' }
                    ]
                },
                {
                    text: 'Camera',
                    items: [
                        { text: 'Lens' },
                        { text: 'Tripods' }
                    ]
                }
            ]
        },
        {
            text: 'Fashion',
            items: [
                {
                    text: 'Men'
                },
                {
                    text: 'Women'
                }
            ]
        },
        {
            text: 'Home & Living',
            items: [
                {
                    text: 'Furniture'
                },
                {
                    text: 'Decor'
                },
                {
                    text: 'Smart Home Automation'
                },
                {
                    text: 'Dining & Serving'
                }
            ]
        },
        {
            text: 'Entertainment',
            items: [
                {
                    text: 'Televisions'
                },
                {
                    text: 'Home Theatres'
                },
                {
                    text: 'Gaming Laptops'
                }
            ]
        },
        {
            text: 'Contact Us'
        },
        {
            text: 'Help'
        }]
    };
  },
   methods: {
        onBeforeOpen(args) {
            // Restricting sub menu wrapper height
            if (args.parentItem.text === 'Appliances') {
                closest(args.element, '.e-menu-wrapper').style.height = '230px';
            }
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
/* Restricting the parent menu wrapper size */
.e-menu-wrapper.e-scrollable-menu:not(.e-menu-popup) {
    width: 492px;
}
</style>
```

{% endtab %}

## Menu in toolbar

The following example demonstrates how to integrate Menu with Toolbar component.

{% tab template="menu/getting-started" %}

```html
<template>
<div class="toolbar-menu-control">
<ejs-toolbar ref="toolbar" :created="onCreated">
    <e-items>
        <e-item :template='menuTemplate'></e-item>
        <e-item prefixIcon='em-icons e-shopping-cart' align='Right' ></e-item>
    </e-items>
</ejs-toolbar>
</div>
</template>

<script>
import Vue from 'vue';
import { MenuPlugin, ToolbarPlugin } from "@syncfusion/ej2-vue-navigations";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(MenuPlugin);
Vue.use(ToolbarPlugin);

var menutemplateVue = Vue.component("demo1", {
  template: '<ejs-menu :items="menuItems" :animationSettings="animation"></ejs-menu>',
  data() {
    return {
      data: {},
      menuItems: [
            {
                text: 'Appliances',
                items: [
                    {
                        text: 'Kitchen',
                        items: [
                            { text: 'Electric Cookers' },
                            { text: 'Coffee Makers' },
                            { text: 'Blenders' }
                        ]
                    },
                    {
                        text: 'Washing Machine',
                        items: [
                            { text: 'Fully Automatic' },
                            { text: 'Semi Automatic' }
                        ]
                    },
                    {
                        text: 'Air Conditioners',
                        items: [
                            { text: 'Inverter ACs' },
                            { text: 'Split ACs' },
                            { text: 'Window ACs' }
                        ]
                    }
                ]
            },
            {
                text: 'Accessories',
                items: [
                    {
                        text: 'Mobile',
                        items: [
                            { text: 'Headphones' },
                            { text: 'Memory Cards' },
                            { text: 'Power Banks' }
                        ]
                    },
                    {
                        text: 'Computer',
                        items: [
                            { text: 'Pendrives' },
                            { text: 'External Hard Disks' },
                            { text: 'Monitors' }
                        ]
                    }
                ]
            },
            {
                text: 'Fashion',
                items: [
                    {
                        text: 'Men',
                        items: [
                            { text: 'Shirts' },
                            { text: 'Jackets' },
                            { text: 'Track Suits' }
                        ]
                    },
                    {
                        text: 'Women',
                        items: [
                            { text: 'Kurtas' },
                            { text: 'Salwars' },
                            { text: 'Sarees' }
                        ]
                    }
                ]
            },
            {
                text: 'Home & Living',
                items: [
                    {
                        text: 'Furniture',
                        items: [
                            { text: 'Beds' },
                            { text: 'Mattresses' },
                            { text: 'Dining Tables' }
                        ]
                    },
                    {
                        text: 'Decor',
                        items: [
                            { text: 'Clocks' },
                            { text: 'Wall Decals' },
                            { text: 'Paintings' }
                        ]
                    }
                ]
            }
        ],
      animation: { effect: 'none' }
    };
  }
});

export default {
   data: function() {
    return {
        menuTemplate: function() {
            return {
                template: menutemplateVue
            }
        }
    }
  },
  methods: {
      onCreated: function() {
          this.$refs.toolbar.$el.ej2_instances[0].refreshOverflow();
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

@font-face {
    font-family: 'e-menu';
    src:
    url(data:application/x-font-ttf;charset=utf-8;base64,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) format('truetype');
    font-weight: normal;
    font-style: normal;
}

.em-icons {
    font-family: 'e-menu';
    font-style: normal;
    font-variant: normal;
    font-weight: normal;
    text-transform: none;
    line-height: 2;
}

.toolbar-menu-control .e-toolbar-items .e-toolbar-item .e-tbar-btn .e-btn-icon.e-shopping-cart {
    font-size: 20px;
    margin-right: 1px;
}

.toolbar-menu-control .e-shopping-cart::before {
    content: '\e7e8';
}

.toolbar-menu-control .e-menu-wrapper .e-menu {
    border: none;
}

.toolbar-menu-control {
    margin: 45px auto 0;
    max-width: 950px;
}

.toolbar-menu-control .e-toolbar .e-toolbar-left .e-toolbar-item.e-template {
    padding: 0;
}

.toolbar-menu-control .e-toolbar {
    overflow: visible !important;
}

.toolbar-menu-control .e-menu-wrapper {
    margin-right: 160px;
}

.toolbar-menu-control .e-hscroll .e-hscroll-content {
    position: static;
}

@media only screen and (max-width: 1300px) {
    .toolbar-menu-control {
        width: auto;
    }
}

</style>
```

{% endtab %}

## Hamburger menu

The following example demonstrates the use case of menu with Accordion component integrated in SideBar.

{% tab template="menu/getting-started" %}

```html
<template>
<div>
    <div class="header">
        <span id="hamburger" class="e-icons menu default" @click='hamburgerClick'></span>
        <div class="content">Header content</div>
    </div>
    <ejs-sidebar ref="sidebar" id='default-sidebar' width='220px' type='Over'>
        <div class="title-header">
            <div style="display:inline-block"> Menu </div>
            <span  id="close" class="e-icons" @click='close'></span>
        </div>
        <div class="content-area">
            <ejs-accordion ref="accordion" :items='items' :expanding='expand' :clicked='clicked'></ejs-accordion>
        </div>
    </ejs-sidebar>
</div>
</template>

<script>
import Vue from 'vue';
import { Accordion } from "@syncfusion/ej2-navigations";
import { SidebarPlugin, AccordionPlugin } from "@syncfusion/ej2-vue-navigations";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(SidebarPlugin);
Vue.use(AccordionPlugin);

export default {
   data: function() {
    return {
                 items: [
        {
            header: 'Appliances',
            content: '<div id="Appliances_Items"></div>',
            subItems: [
                {
                    header: 'Kitchen',
                    content: '<div id="Appliances_Kitchen_Items"></div>',
                    subItems: [
                        { header: 'Electric Cookers' },
                        { header: 'Coffee Makers' },
                        { header: 'Blenders' },
                    ]
                },
                {
                    header: 'Washing Machine',
                    content: '<div id="Appliances_Washing_Items"></div>',
                    subItems: [
                        { header: 'Fully Automatic' },
                        { header: 'Semi Automatic' }
                    ]
                },
                {
                    header: 'Air Conditioners',
                    content: '<div id="Appliances_Conditioners_Items"></div>',
                    subItems: [
                        { header: 'Inverter ACs' },
                        { header: 'Split ACs' },
                        { header: 'Window ACs' },
                    ]
                }
            ]
        },
        {
            header: 'Accessories',
            content: '<div id="Accessories_Items"></div>',
            subItems: [
                {
                    header: 'Mobile',
                    content: '<div id="Accessories_Mobile_Items"></div>',
                    subItems: [
                        { header: 'Headphones' },
                        { header: 'Memory Cards' },
                        { header: 'Power Banks' }
                    ]
                },
                {
                    header: 'Computer',
                    content: '<div id="Accessories_Computer_Items"></div>',
                    subItems: [
                        { header: 'Pendrives' },
                        { header: 'External Hard Disks' },
                        { header: 'Monitors' }
                    ]
                }
            ]
        },
        {
            header: 'Fashion',
            content: '<div id="Fashion_Items"></div>',
            subItems: [
                { header: 'Men' },
                { header: 'Women' }
            ]
        },
        {
            header: 'Home & Living',
            content: '<div id="Home_Living_Items"></div>',
            subItems: [
                { header: 'Furniture' },
                { header: 'Decor' }
            ]
        },
        {
            header: 'Entertainment',
            content: '<div id="Entertainment_Items"></div>',
            subItems: [
                { header: 'Televisions' },
                { header: 'Home Theatres' },
                { header: 'Gaming Laptops' }
            ]
        }
    ],
    };
  },
  methods: {
    expand: function(e) {
        if (e.isExpanded) {
            if (e.element.getElementsByClassName('e-acrdn-content')[0].children[0].classList.contains('e-accordion')) {
                return;
            }
            //Initialize Nested Accordion component
            var nestAcrdn = new Accordion({
                items: e.item.subItems,
                expanding: this.expand,
                clicked: this.clicked
            });

            var elemId = e.element.getElementsByClassName('e-acrdn-content')[0].children[0].id;
            //Render initialized Nested Accordion component
            nestAcrdn.appendTo('#' + elemId);
        }
    },

    clicked: function(e){
        if (!e.item && !(e.originalEvent.target.closest('.e-acrdn-item').getElementsByClassName('e-tgl-collapse-icon').length)) {
            this.$refs.sidebar.hide();
        }
    },

    hamburgerClick: function() {
        this.$refs.sidebar.show();
    },

    close: function() {
        this.$refs.sidebar.hide();
    }
  }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";

body {
    margin: 0;
}

.header {
    width: 100%;
    background-color: #7b8cfb;
}

#default-sidebar,
.header .content {
    background-color: #7b8cfb;
    color: white;
    border: none;
}

.header .content {
    font-size: 20px;
    line-height: 50px;
    text-align: center;
}

.main-content {
    text-align: center;
    font-size: 20px;
    padding: 100px 15px;
}

#default-sidebar .close-btn:hover {
    color: rgba(0, 0, 0, .87);
    background-color: #fafafa;
}

#hamburger.menu {
    font-size: 25px;
    cursor: pointer;
    float: left;
    line-height: 50px;
    position: absolute;
    z-index: 1000;
    left: 25px;
    color: white;
}

#hamburger.menu:before {
    content: '\e99a';
}

#close:before {
    content: "\e945";
}

.title-header {
    text-align: center;
    font-size: 18px;
    padding: 15px 15px 35px;
}

.e-sidebar .title-header #close {
    cursor: pointer;
    line-height: 25px;
    float: right;
}

</style>
```

{% endtab %}

## Mobile view

The following example demonstrates the use case of Menu in Mobile mode by using ListView component with hamburger.

Install Syncfusion `Lists` packages using below command.

```bash
npm install @syncfusion/ej2-vue-lists --save
```

{% tab template="menu/getting-started", iframeHeight="580px" %}

```html
<template>
<div class="layoutWrapper">
    <div class="speaker">
        <div class="camera"></div>
    </div>
    <div class="layout">
        <div id="container">
            <div id="header">
                <span id="hamburger" @click="hamburgerClick" class="e-icons menu default"></span>
                <div class="content">Header</div>
            </div>
            <!-- ListView element -->
            <ejs-listview  ref="listview" :dataSource="dataSource" headerTitle="Menu" :showHeader="true" :select="onSelect" tabindex="1" v-bind:style="{display: 'none'}" ></ejs-listview>
            <span id="close" @click="onClick" class="e-icons" v-bind:style="{display: 'none'}"></span>
        </div>
    </div>
    <div class="outerButton"> </div>
</div>
</template>

<script>
import Vue from 'vue';
import { ListViewPlugin } from "@syncfusion/ej2-vue-lists";
import { enableRipple, Animation } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ListViewPlugin);

export default {
   data: function() {
    return {
                 dataSource: [
    {
      text: 'Appliances',
      id: 'list1',
      child: [
        {
          text: 'Kitchen',
          id: 'list1_1',
          child: [
            { id: 'list1_1_1', text: 'Electric Cookers' },
            { id: 'list1_1_2', text: 'Coffee Makers' },
            { id: 'list1_1_3', text: 'Blenders' },
          ]
        },
        {
          text: 'Washing Machine',
          id: 'list1_2',
          child: [
            { id: 'list1_2_1', text: 'Fully Automatic' },
            { id: 'list1_2_2', text: 'Semi Automatic' }
          ]
        },
        {
          text: 'Air Conditioners',
          id: 'list1_3',
          child: [
            { id: 'list1_3_1', text: 'Inverter ACs' },
            { id: 'list1_3_2', text: 'Split ACs' },
            { id: 'list1_3_3', text: 'Window ACs' },
          ]
        }
      ]
    },
    {
      text: 'Accessories',
      id: 'list2',
      child: [
        {
          text: 'Mobile',
          id: 'list2_1',
          child: [
            { id: 'list2_1_1', text: 'Headphones' },
            { id: 'list2_1_2', text: 'Memory Cards' },
            { id: 'list2_1_3', text: 'Power Banks' }
          ]
        },
        {
          text: 'Computer',
          id: 'list2_2',
          child: [
            { id: 'list2_2_1', text: 'Pendrives' },
            { id: 'list2_2_2', text: 'External Hard Disks' },
            { id: 'list2_2_3', text: 'Monitors' }
          ]
        }
      ]
    },
    {
      text: 'Fashion',
      id: 'list3',
      child: [
        { id: 'list3_1', text: 'Men' },
        { id: 'list3_2', text: 'Women' }
      ]
    },
    {
      text: 'Home & Living',
      id: 'list4',
      child: [
        { id: 'list4_1', text: 'Furniture' },
        { id: 'list4_2', text: 'Decor' }
      ]
    },
    {
      text: 'Entertainment',
      id: 'list5',
      child: [
        { id: 'list5_1', text: 'Televisions' },
        { id: 'list5_2', text: 'Home Theatres' },
        { id: 'list5_3', text: 'Gaming Laptops' }
      ]
    }
  ]
    };
  },
  methods: {
    onSelect: function(e) {
        if (e.data && !(e.data.child)) {
            this.$refs.listview.ej2Instances.element.style.display = 'none';
            document.getElementById('close').style.display = 'none';
        }
    },

    onClick: function(e){
        this.$refs.listview.ej2Instances.element.style.display = 'none';
        document.getElementById('close').style.display = 'none';
    },

    hamburgerClick: function() {
        var element = this.$refs.listview.ej2Instances.element;
        var animation = new Animation({ duration: 500 });
        animation.animate(element, {
        name: 'SlideDown',
        begin: function(args) {
            element.style.display = 'block';
            document.getElementById('close').style.display = 'block';
        }
        });
    }
  }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-lists/styles/material.css";

.layoutWrapper {
  line-height: initial;
  border: 1px solid black;
  width: 285px;
  height: 505px;
  margin: auto;
  margin-bottom: 15px;
  border-radius: 28px;
  position: relative;
  background-image: linear-gradient(to top, #ffffff, #f5f5f5);
}

.layoutWrapper .speaker {
  border: 1px solid black;
  border-radius: 5px;
  width: 33.33333333%;
  height: 5px;
  margin: 15px auto 0px auto;
  position: relative;
}

.layoutWrapper .outerButton {
  width: 30px;
  height: 30px;
  border: 1px solid black;
  border-radius: 50%;
  position: absolute;
  bottom: calc(0% + 10px);
  left: calc(50% - 15px);
}

.layoutWrapper .camera {
  position: absolute;
  left: calc(-15% - 10px);
  top: -100%;
  width: 10px;
  height: 10px;
  border-radius: 50%;
  border: 1px solid black;
}

.layoutWrapper .layout {
  border: 1px solid black;
  margin: 20px 13px 0px 13px;
}

.layout #container {
  height: 405px;
  background-color: white;
}

#header {
  width: 100%;
  background-color: #7b8cfb;
}

.layout .e-listview .e-list-header,
.layout .e-listview .e-but-back {
  background-color: #7b8cfb;
  color: white;
}

#header .content {
  background-color: #7b8cfb;
  color: white;
  border: none;
  font-size: 20px;
  line-height: 50px;
  text-align: center;
}

#hamburger.menu {
  font-size: 25px;
  cursor: pointer;
  float: left;
  line-height: 50px;
  position: absolute;
  z-index: 1000;
  left: 25px;
  color: white;
}

#hamburger.menu:before {
  content: '\e99a';
}

#listview {
  position: absolute;
  width: 257px;
  overflow: hidden;
  top: 43px;
  left: 14px;
  z-index: 1000;
}

#close:before {
  content: "\e945";
}

#close {
  position: absolute;
  right: 25px;
  color: white;
  top: 60px;
  z-index: 1000;
}

</style>
```

{% endtab %}
