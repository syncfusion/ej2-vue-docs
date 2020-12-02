---
title: "Trace events of ProgressButton"
component: "ProgressButton"
description: "Vue ProgressButton how to section, change text content and styles, hide spinner, customize progress, event trace."
---

# Trace events of ProgressButton

The ProgressButton component triggers events based on its actions. The events can be used as extension points to perform custom operations.

The events available in ProgressButton are [`fail`](../../api/progress-button#fail), [`begin`](../../api/progress-button#begin), [`progress`](../../api/progress-button#progress), and [`end`](../../api/progress-button#end).

{% tab template="progress-button/default", isDefaultActive=true %}

```html
<template>
 <div id='container'>
        <div class="control-section">
            <div class="progress-btn-section">
                <ejs-progressbutton content='Progress' :enableProgress="true" :begin="begin" :end="end" :progress="progress" :fail="fail"></ejs-progressbutton>
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
            <button id='clear' class='e-btn' @click='onClick'>Clear</button>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { ProgressButtonPlugin} from "@syncfusion/ej2-vue-splitbuttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ProgressButtonPlugin);

export default {
    methods: {
        updateEventLog: function(args) {
            var propertyElem = document.getElementById('propertyTable');
            propertyElem.getElementsByTagName('td')[0].insertAdjacentHTML('beforeend', args.name + ' Event triggered. <br/>';
        },
        begin: function(args) {
            this.updateEventLog(args);
        },
        end: function(args) {
            this.updateEventLog(args);
        },
        progress: function(args) {
            this.updateEventLog(args);
        },
        fail: function(args) {
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
    @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
    @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";

    .progress-btn-section {
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
