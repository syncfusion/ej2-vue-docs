---
title: " Localization in Vue Maps control | Syncfusion "

component: "Maps"

description: "Learn here all about Localization of Syncfusion Vue Maps control and more."
---

# Localization in Vue Maps

The localization library allows localizing the default text content of the Maps control. The Maps control has the static text of some features such as tooltip of zoom toolbar, and that can be changed to any other culture(Arabic, Deutsch, French, etc) by defining the locale value and translation object.

<!-- markdownlint-disable MD033 -->

<table>
<tr>
<td><b>Locale key words</b></td>
<td><b>Text to display</b></td>
</tr>
<tr>
<td>Zoom</td>
<td>Zoom</td>
</tr>
<tr>
<td>ZoomIn</td>
<td>Zoom In</td>
</tr>
<tr>
<td>ZoomOut</td>
<td>Zoom Out</td>
</tr>
<tr>
<td>Reset</td>
<td>Reset</td>
</tr>
<tr>
<td>Pan</td>
<td>Pan</td>
</tr>
</table>

To load translation object in the application, use `load` function of **L10n** class. For more information about localization, refer [here](http://ej2.syncfusion.com/documentation/base/localization.html).

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <div class='wrapper'>
            <ejs-maps :zoomSettings='zoomSettings' :locale='locale' >
                <e-layers>
                    <e-layer :shapeData='shapeData' :shapePropertyPath='shapePropertyPath' :shapeDataPath='shapeDataPath' :dataSource='dataSource' :shapeSettings='shapeSettings' >
                    </e-layer>
                </e-layers>
            </ejs-maps>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, Zoom } from '@syncfusion/ej2-vue-maps';
import { usMap } from './usa.js';
import { electionData } from './election-data.js';
import { L10n } from '@syncfusion/ej2-base';
Vue.use(MapsPlugin);

L10n.load({
    'ar-AR': {
        'maps': {
            ZoomIn: 'تكبير',
            ZoomOut: 'تصغير',
            Zoom: 'زوم',
            Pan: 'مقلاة',
            Reset: 'إعادة تعيين'
        },
    }
});
export default {
data () {
    return {
        zoomSettings: {
            enable: true
        },
        locale: 'ar-AR',
        shapeData: usMap,
        shapePropertyPath:  'name',
        shapeDataPath:  'State',
        dataSource : electionData,
        shapeSettings: {
        colorValuePath: 'Candidate',
            colorMapping: [
            {
                value: 'Trump', color: '#D84444'
            },
            {
                value: 'Clinton', color: '#316DB5'
            }]
        }
    }
},
provide: {
    maps: [Zoom]
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