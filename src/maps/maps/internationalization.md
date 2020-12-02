---
title: "Internationalization"
component: "Maps"
description: "Internationalization support in maps"
---

# Internationalization

Maps provides support for internationalization for the below elements.

* Data label
* Tooltip

For more information about number and date formatter you can refer
[`internationalization`](http://ej2.syncfusion.com/documentation/base/intl.html).

<!-- markdownlint-disable MD036 -->
**Globalization**

Globalization is the process of designing and developing an component that works in different
cultures/locales. Internationalization library is used to globalize number, date, time values in
Maps component using [`format`] property in the maps model.

**Numeric Format**

In the below example tooltip is globalized to Deutsch culture.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
          <div class='wrapper'>
            <ejs-maps  :format='format' >
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
import { setCulture } from '@syncfusion/ej2-base';
import { usMap } from './usa.js';
import { electionData } from './election-data.js';
setCulture('de');
Vue.use(MapsPlugin);
export default {
data () {
    return{
        format: 'c',
        shapeData: usMap,
        shapePropertyPath:  'name',
        shapeDataPath:  'State',
        dataSource : electionData,
        tooltipSettings: {
            visible: true,
            valuePath: 'Trump'
        },
        shapeSettings: {
            colorValuePath: 'Candidate',
            colorMapping: [{
                value: 'Trump', color: '#D84444'
            },
            {
                value: 'Clinton', color: '#316DB5'
            }]
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
