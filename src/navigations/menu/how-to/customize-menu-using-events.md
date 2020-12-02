# Customize menu using events

The Menu provides a set of [`events`](../../api/menu#events) to enable users to customize it.

{% tab template="menu/getting-started" %}

```html
<template>
 <div id='container'>
        <div class="control-section">
            <div class="menu-section">
                <ejs-menu :items='menuItems' :beforeOpen='beforeOpen' :beforeClose='beforeClose' :onClose='onClose' :onOpen='onOpen' :select='select'></ejs-menu>
            </div>
            <div class="property-section">
                <table id="propertyTable" title="Event trace">
                    <tbody>
                        <th>Event trace:-</th>
                        <tr>
                            <td></td>
                        </tr>
                    </tbody>
                </table>
            </div>
            <button id='clear' @click=onClick>Clear</button>
        </div>
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
updateEventLog: function(args) {
    var propertyElem = document.getElementById('propertyTable');
    propertyElem.getElementsByTagName('td')[0].insertAdjacentHTML('beforeend', args.name + ' Event triggered. <br />');
},
beforeOpen: function(args) {
    this.updateEventLog(args);
},
beforeClose: function(args) {
    this.updateEventLog(args);
},
onClose: function(args) {
    this.updateEventLog(args);
},
onOpen: function(args) {
    this.updateEventLog(args);
},
select: function(args) {
    this.updateEventLog(args);
},
onClick: function(args) {
    var propertyElem = document.getElementById('propertyTable');
    propertyElem.getElementsByTagName('td')[0].innerHTML = '';
}
    }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";

html, body, .control-section {
    height: 95%;
}

.menu-section {
    margin-top: 100px;
    text-align: center;
    float: left;
}

.property-section {
    overflow: auto;
    width: 40%;
    height: 330px;
    float: right;
    font-family: monospace;
}

.property-section th {
    text-align: left;
}

#clear {
    float: right;
    clear: both;
}

</style>
```

{% endtab %}
