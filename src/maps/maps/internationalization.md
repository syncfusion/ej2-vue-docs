---
title: " Internationalization in Vue Maps control | Syncfusion "

component: "Maps"

description: "Learn here all about Internationalization of Syncfusion Vue Maps control and more."
---

# Internationalization in Vue Maps control

Maps provide support for internationalization for the below elements.

* Data label
* Tooltip

For more information about number and date formatter, refer to the [`internationalization`](http://ej2.syncfusion.com/documentation/base/intl.html) section.

<!-- markdownlint-disable MD036 -->

## Globalization

Globalization is the process of designing and developing a component that works in different
cultures/locales. Internationalization library is used to globalize number, date, time values in
Maps component using [`format`](../api/maps/mapsModel/#format) property in the [`Maps`](../api/maps/mapsModel/).

## Numeric Format

The numeric formats such as currency, percentage and so on can be displayed in the tooltip and data labels of the Maps using the [`format`](../api/maps/mapsModel/#format) property in the [`Maps`](../api/maps/mapsModel/). In the below example, the tooltip is globalized to **"German"** culture. When setting the [`useGroupingSeparator`](../api/maps/mapsModel/#usegroupingseparator) property as "**true**", the numeric text in the Maps separates with the comma separator.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <div class='wrapper'>
            <ejs-maps  :format='format' :useGroupingSeparator='useGroupingSeparator' >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapePropertyPath='shapePropertyPath' :shapeDataPath='shapeDataPath' :dataSource='dataSource' :shapeSettings='shapeSettings' :tooltipSettings='tooltipSettings'></e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, MapsTooltip } from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
import { setCulture } from '@syncfusion/ej2-base';
setCulture('de');
Vue.use(MapsPlugin);
export default {
data () {
    return {
        format: 'c',
        useGroupingSeparator: true,
        shapeData: world_map,
        shapePropertyPath: 'name',
        shapeDataPath: 'Country',
        dataSource: [
            { "Country": "China", "Membership": "Permanent", population: '38332521' },
            { "Country": "France", "Membership": "Permanent", population: '19651127' },
            { "Country": "Russia", "Membership": "Permanent", population: '3090416' },
            { "Country": "Kazakhstan", "Membership": "Non-Permanent", population: '1232521' },
            { "Country": "Poland", "Membership": "Non-Permanent", population: '90332521' },
            { "Country": "Sweden", "Membership": "Non-Permanent", population: '383521' }
        ],
        shapeSettings: {
            colorValuePath: 'Membership',
            colorMapping: [
                {
                    value: 'Permanent', color: '#D84444'
                },
                {
                    value: 'Non-Permanent', color: '#316DB5'
                }
            ]
        },
        tooltipSettings: {
            visible: true,
            valuePath: 'population'
        }
    }
},
provide: {
    maps: [MapsTooltip]
}
}
</script>
<style>
  .wrapper {
    max-width: 400px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}
