---
title: "Menu with datasource and HTML tags"
component: "Menu"
description: "Vue Menu supports HTML elements for menu items, databinding with local data source, parent child data, array of JSON data, and remote service with query."
---

# Data source binding and Custom menu items

## Data binding

The Menu supports data source bindings such as array of JavaScript objects that can be structured as either `hierarchical` or `self-referential` data.

### Hierarchical data

The Menu can be populated with hierarchical data source by assigning it to the [`items`](../api/menu/menuItemModel#items) property, and the fields with corresponding keys can be mapped to the [`fields`](../api/menu/fieldSettingsModel) property.

#### JSON data

The Menu can generate its menu items through an array of complex data source by mapping fields from the [`fields`](../api/menu/fieldSettingsModel) property.

{% tab template="menu/getting-started" %}

```html
<template>
<div>
<ejs-menu :items='datasource' :fields='menuFields'></ejs-menu>
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
            //Menu datasource
           datasource:  [
            {
                continent: 'Asia',
                countries: [
                    {
                        country: 'China',
                        languages: [
                            { language: 'Chinese' },
                            { language: 'Cantonese' }
                        ]
                    },
                    {
                        country: 'India',
                        languages: [
                            { language: 'English' },
                            { language: 'Hindi' },
                            { language: 'Tamil' }
                        ]
                    },
                    {
                        country: 'Japan',
                        languages: [
                            { language: 'Japanese' }
                        ]
                    }
                ]
            },
            {
                continent: 'Africa',
                countries: [
                    {
                        country: 'Nigeria',
                        languages: [
                            { language: 'English' },
                            { language: 'Hausa' }
                        ]
                    },
                    {
                        country: 'Egypt',
                        languages: [
                            { language: 'Arabic' }
                        ]
                    },
                    {
                        country: 'South Africa',
                        languages: [
                            { language: 'Tswana' },
                            { language: 'Swati' }
                        ]
                    }
                ]
            },
            {
                continent: 'North America',
                countries: [
                    {
                        country: 'Canada',
                        languages: [
                            { language: 'French' }
                        ]
                    },
                    {
                        country: 'Mexico',
                        languages: [
                            { language: 'Spanish' }
                        ]
                    },
                    {
                        country: 'USA',
                        languages: [
                            { language: 'English' }
                        ]
                    }
                ]
            },
            {
                continent: 'South America',
                countries: [
                    {
                        country: 'Brazil',
                        languages: [
                            { language: 'Portuguese' }
                        ]
                    },
                    {
                        country: 'Colombia',
                        languages: [
                            { language: 'Spanish' }
                        ]
                    },
                    {
                        country: 'Argentina',
                        languages: [
                            { language: 'Spanish' }
                        ]
                    }
                ]
            },
            {
                continent: 'Oceania',
                countries: [
                    {
                        country: 'Australia'
                    },
                    {
                        country: 'New Zealand'
                    },
                    {
                        country: 'Samoa'
                    },
                ]
            }
        ],
        menuFields: {
            text: ['continent', 'country', 'language'],
            children: ['countries', 'languages']
        }
    };
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

#### Data Service

In application level, remote data binding can be achieved using [`DataManager`](https://ej2.syncfusion.com/documentation/data).
To create Menu, assign `items` property with resultant data from
[`callback`](https://ej2.syncfusion.com/documentation/api/data/deferred/#then) function.

{% tab template="menu/getting-started" %}

```html
<template>
    <div class="template-menu-control">
        <ejs-menu v-if="items" :items="items" :fields="menuFields"></ejs-menu>
    </div>
</template>

<script>
import Vue from 'vue';
import { MenuPlugin } from "@syncfusion/ej2-vue-navigations";
import { ODataAdaptor, DataManager, Query } from "@syncfusion/ej2-data";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(MenuPlugin);

var SERVICE_URI = 'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/';
var result;

export default {
   data: function() {
    return {
        items: this.menuItems(),
        menuFields: {
            text: ['FirstName','ShipName'],
            children: ['Orders']
        }
      }
   },
   methods: {
    menuItems() {
        new DataManager({ url: SERVICE_URI, adaptor: new ODataAdaptor, crossDomain: true })
        .executeQuery(
        new Query().from('Employees').take(5).hierarchy(
            new Query()
            .foreignKey('EmployeeID')
            .from('Orders').take(13),
            function() {
                return [1,2,3,4,5]
            }
        ))
        .then((e) => {
            this.items =  e.result
        });
        return this.items;
     }
   }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";

.template-menu-control {
    margin-top: 100px;
    text-align: center;
}
</style>
```

{% endtab %}

### Self-referential data

Menu can be populated from self-referential data structure that contains array of JSON objects with `parentId` mapping.

In the following example, the **id**, **pId**, and **text** columns from self-referential data have been mapped to the **itemId**, **parentId**, and **text** fields, respectively.

{% tab template="menu/getting-started" %}

```html
<template>
<div>
<ejs-menu :items='datasource' :fields='menuFields'></ejs-menu>
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
            //Menu datasource
           datasource:  [
        { id: 'parent1', text: 'Events' },
    { id: 'parent2', text: 'Movies' },
    { id: 'parent3', text: 'Directory' },
    { id: 'parent4', text: 'Queries', pId: null },
    { id: 'parent5', text: 'Services', pId: null },

    { id: 'parent6', text: 'Conferences', pId: 'parent1' },
    { id: 'parent7', text: 'Music', pId: 'parent1' },
    { id: 'parent8', text: 'Workshops', pId: 'parent1' },

    { id: 'parent9', text: 'Now Showing', pId: 'parent2' },
    { id: 'parent10', text: 'Coming Soon', pId: 'parent2' },

    { id: 'parent10', text: 'Media Gallery', pId: 'parent3' },
    { id: 'parent11', text: 'Newsletters', pId: 'parent3' },

    { id: 'parent12', text: 'Our Policy', pId: 'parent4' },
    { id: 'parent13', text: 'Site Map', pId: 'parent4' },
    { id: 'parent14', text: 'Pop', pId: 'parent7' },
    { id: 'parent15', text: 'Folk', pId: 'parent7' },
    { id: 'parent16', text: 'Classical', pId: 'parent7' }
    ],
    //Menu fields definition
    menuFields: {
    itemId:'id',
    text: 'text',
    parentId: 'pId'
}
    };

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

## Custom menu items

The Menu can be customized using Essential JS2 [Template engine](https://ej2.syncfusion.com/documentation/common/template-engine.html) to render the elements.

To customize menu items in your application, set your customized template string to the [`template`](../api/menu#template) property. In the following example, the menu has been rendered with customized menu items.

Install Syncfusion `Layouts` and `Navigations` packages using below command.

```bash
npm install @syncfusion/ej2-vue-layouts --save
npm install @syncfusion/ej2-vue-navigations --save
```

{% tab template="menu/getting-started" %}

```html

<template>
    <div class="template-menu-control">
        <ejs-menu :items="data" :fields="menuFields" :template="menuTemplate"></ejs-menu>
    </div>
</template>

<script>
import Vue from "vue";
import { MenuPlugin } from "@syncfusion/ej2-vue-navigations";

Vue.use(MenuPlugin);

export default {
  data: function() {
    var menutemplateVue = Vue.component("demo", {
    template: '  <span v-if="data.category"> {{data.category}} </span>'+
    ' <div v-else-if="data.value" style="width: 100%;display: flex;justify-content: space-between;">'+
     '<img v-if="data.url" class="e-avatar e-avatar-small" v-bind:style="image" />' +
       '<span style="width:100%;">{{data.value}}</span></div>' +
    '<span class="e-menu-template" v-else-if="data.support">'+
        '<ul>'+
        '<li v-bind:key="index" v-for="(val,index) of data.support">'+
        ' {{val.value}} ' +
            '<span v-if="val.count" class="e-badge e-badge-success">{{val.count}}</span> '+
        ' </li> '+
        '</ul>'+
    '</span>'+
    '<div tabindex="0" class="e-card" v-else>'+
        '<div class="e-card-header">'+
            '<div class="e-card-header-caption">'+
                '<div class="e-card-header-title">About Us</div>'+
            '</div>'+
        '</div>'+
        '<div class="e-card-content">{{data.about.value}} </div>'+
        '<div class="e-card-actions">'+
            '<button class="e-btn e-outline">Read More </button>'+
        '</div>'+
    '</div>',
    data() {
        return {
        data: {}
        }
    },
    computed: {
        image: function() {
        return 'background-image: url(https://ej2.syncfusion.com/react/demos/src/menu/images/' + this.data.url + '.png);';
        }
    }
    });

    return {
        data: [
            {
                category: 'Products',
                options: [
                    { value: 'JavaScript', url: 'javascript' },
                    { value: 'Angular', url: 'angular' },
                    { value: 'ASP.NET Core', url: 'core' },
                    { value: 'ASP.NET MVC', url: 'mvc' }
                ]
            },
            {
                category: 'Services',
                options: [
                    {
                        support: [
                            { value: 'Application Development', count: '1200+' },
                            { value: 'Maintenance & Support', count: '3700+' },
                            { value: 'Quality Assurance' },
                            { value: 'Cloud Integration', count: '900+' }
                        ]
                    }
                ]
            },
            {
                category: 'About Us',
                options: [
                    {
                        about: {
                            value: "We are on a mission to provide world-class best software solutions for web, mobile and desktop platforms. Around 900+ applications are desgined and delivered to our customers to make digital & strengthen their businesses."
                        }
                    }
                ]
            },
            { category: 'Careers' },
            { category: 'Sign In' }
        ],
        menuFields: {
            text: ['category', 'value'],
            children: ['options']
        },
        menuTemplate: function () {
            return {
                template : menutemplateVue
            }
        }
    };
  }
}
</script>

<style>

@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-notifications/styles/material.css";
@import "../node_modules/@syncfusion/ej2-layouts/styles/material.css";
/* ej2 Menu template styles */

.template-menu-control {
    margin-top: 45px;
    text-align: center;
}

/* Common customization */

.e-bigger .template-menu-control .e-menu-wrapper.e-control ul.e-ul .e-menu-item,
.template-menu-control .e-menu-wrapper.e-control ul.e-ul .e-menu-item,
.template-menu-control .e-menu-wrapper.e-control ul.e-ul .e-menu-item .e-menu-template {
    display: flex;
    height: auto;
    padding: 0;
}

/* Avatar customization */

.e-bigger .template-menu-control .e-menu-wrapper ul .e-menu-item .e-avatar {
    background-size: auto;
    text-indent: 40px;
}

.template-menu-control .e-menu-wrapper ul .e-menu-item .e-avatar {
    background-color: inherit;
    background-position: 0;
    background-size: 25px;
    color: inherit;
    font-size: inherit;
    height: inherit;
    justify-content: left;
    margin: 0 10px;
    width: 100%;
    text-indent: 35px;
}

/* Badge customization */

.template-menu-control .e-menu-wrapper ul .e-menu-item ul li {
    padding: 0 10px;
}

.e-bigger .template-menu-control .e-menu-wrapper ul .e-menu-item ul li .e-badge {
    margin: 18px 0px 0px 10px;
}

.template-menu-control .e-menu-wrapper ul .e-menu-item ul li .e-badge {
    float: right;
    margin: 13px 0px 0px 10px;
}

.template-menu-control .e-menu-wrapper ul .e-menu-item ul li:hover {
    background-color: #eee;
}

/* Card customization */

.e-bigger .template-menu-control .e-menu-wrapper ul.e-ul .e-menu-item .e-card {
    width: 320px;
}

.template-menu-control .e-menu-wrapper ul.e-ul .e-menu-item .e-card {
    width: 290px;
    font-size: inherit;
    cursor: default;
    background-color: inherit;
    border-color: transparent;
}

.template-menu-control .e-menu-wrapper ul.e-ul .e-menu-item .e-card .e-card-content {
    white-space: normal;
    color: inherit;
    padding-top: 0;
    text-align: justify;
    font-size: inherit;
}

.e-bigger .template-menu-control .e-menu-wrapper ul.e-ul .e-menu-item .e-card .cb-icons {
    width: 40px;
    font-size: 40px;
    height: 40px;
}

.template-menu-control .e-menu-wrapper ul.e-ul .e-menu-item .e-card .cb-icons {
    width: 30px;
    font-size: 30px;
    height: 30px;
}

.template-menu-control .e-menu-wrapper ul.e-ul .e-menu-item .e-card .e-card-btn {
    background-color: inherit;
}

</style>

```

{% endtab %}

## See Also

* [Render menu with items](./getting-started#getting-started)