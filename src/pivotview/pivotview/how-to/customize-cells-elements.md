# Customize pivot table cell element

You can customize the pivot table cell element by using the `cellTemplate` property.
The cellTemplate property accepts either an HTML string or the element's ID, which can be used to append additional HTML elements to showcase each cell with custom format.

In this demo, the revenue cost for each year is represented with trend icons.

{% tab template="pivot-grid/common" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-pivotview id="pivotview" ref="pivotview" :dataSourceSettings="dataSourceSettings" :height="height" :dataBound="trend" :cellTemplate="cellTemplate"> </ejs-pivotview>
    </div>
</template>

<script>
import Vue from "vue";
import { PivotViewPlugin } from "@syncfusion/ej2-vue-pivotview";
import { renewableEnergy } from './datasource.js';

Vue.use(PivotViewPlugin);

var cellTemplateVue = Vue.component("cellTemplate", {
    template: `<span class="template-wrap" v-html=getCellContent(data)></span>`,
    data() {
        return {
            data: {}
        };
    },
    methods: {
            getCellContent: function (e) {
                return '<span class="tempwrap sb-icon-neutral pv-icons"></span>';
            }
        }
    });

export default {
  data () {
    return {
      dataSourceSettings: {
        dataSource: renewableEnergy,
        expandAll: true,
        enableSorting: true,
        drilledMembers: [{ name: 'Year', items: ['FY 2015', 'FY 2017', 'FY 2018'] }],
        formatSettings: [{ name: 'ProCost', format: 'C0' }],
        rows: [
            { name: 'Year', caption: 'Production Year' }
        ],
        columns: [
            { name: 'EnerType', caption: 'Energy Type' },
            { name: 'EneSource', caption: 'Energy Source' }
        ],
        values: [
            { name: 'ProCost', caption: 'Revenue Growth' }
        ],
        filters: []
      },
      height: 350,
      cellTemplate: function() {
        return { template: cellTemplateVue };
      },
    }
  },
  methods: {
    trend: function() {
      let pivotGridObj = (<any>this.$refs.pivotview).ej2Instances;
      var cTable = document.getElementsByClassName("e-table");
        var colLen = pivotGridObj.pivotValues[3].length;
        var cLen = cTable[3].children[0].children.length;
        var rLen = cTable[3].children[1].children.length;
        for (let k = 0; k < rLen; k++) {
            if (pivotGridObj.pivotValues[k] && pivotGridObj.pivotValues[k][0] !== undefined) {
                rowIndx = (pivotGridObj.pivotValues[k][0]).rowIndex;
                break;
            }
        }
        var rowHeaders = [].slice.call(cTable[2].children[1].querySelectorAll('td'));
        var rows = pivotGridObj.dataSourceSettings.rows;
        if (rowHeaders.length > 1) {
            for (var i = 0, Cnt = rows; i < Cnt.length; i++) {
                var fields = {};
                var fieldHeaders = [];
                    for (var j = 0, Lnt = rowHeaders; j < Lnt.length; j++) {
                        var header = rowHeaders[j];
                        if (header.className.indexOf('e-gtot') === -1 && header.className.indexOf('e-rowsheader') > -1 && header.getAttribute('fieldname') === rows[i].name) {
                            var headerName = rowHeaders[j].getAttribute('fieldname') + '_' + rowHeaders[j].textContent;
                            fields[rowHeaders[j].textContent] = j;
                            fieldHeaders.push(rowHeaders[j].textContent);
                        }
                    }
                    if (i === 0) {
                        for (var rnt = 0, Lnt = fieldHeaders; rnt < Lnt.length; rnt++) {
                            if (rnt !== 0) {
                                var row = fields[fieldHeaders[rnt]];
                                var prevRow = fields[fieldHeaders[rnt - 1]];
                                for (var j = 0, ci = 1; j < cLen && ci < colLen; j++, ci++) {
                                    var node = cTable[3].children[1].children[row].childNodes[j];
                                    var prevNode = cTable[3].children[1].children[prevRow].childNodes[j];
                                    var ri = node.getAttribute('index');
                                    var prevRi = prevNode.getAttribute('index');
                                    if (ri < pivotGridObj.pivotValues.length) {
                                        if ((pivotGridObj.pivotValues[prevRi][ci]).value > (pivotGridObj.pivotValues[ri][ci]).value && node.querySelector('.tempwrap')) {
                                            var trendElement = node.querySelector('.tempwrap');
                                            trendElement.className = trendElement.className.replace('sb-icon-neutral', 'sb-icon-loss');
                                        } else if ((pivotGridObj.pivotValues[prevRi][ci]).value < (pivotGridObj.pivotValues[ri][ci]).value && node.querySelector('.tempwrap')) {
                                            var trendElement = node.querySelector('.tempwrap');
                                            trendElement.className = trendElement.className.replace('sb-icon-neutral', 'sb-icon-profit');
                                        }
                                    }
                                }
                            }
                        }
                }
            }
        }
    },
  }
}
</script>
<style>
@import "@syncfusion/ej2-vue-pivotview/styles/material.css";

.e-pivotview .e-columnsheader .tempwrap {
  display: none;
}
.e-pivotview .e-rowsheader .tempwrap {
  display: none;
}

@font-face {
  font-family: 'e-pivot';
  src:
      url(data:application/x-font-ttf;charset=utf-8;base64,AAEAAAAKAIAAAwAgT1MvMjhUSmAAAAEoAAAAVmNtYXCs3q0zAAABkAAAAEpnbHlmdaItOwAAAegAAAE0aGVhZBRYEz0AAADQAAAANmhoZWEHmQNtAAAArAAAACRobXR4D7gAAAAAAYAAAAAQbG9jYQDAAHIAAAHcAAAACm1heHABDwBBAAABCAAAACBuYW1lc0cOBgAAAxwAAAIlcG9zdK9TctUAAAVEAAAARwABAAADUv9qAFoEAAAA)//4D6gABAAAAAAAAAAAAAAAAAAAABAABAAAAAQAAT8kba18PPPUACwPoAAAAANin5zgAAAAA2KfnOAAAAAAD6gPoAAAACAACAAAAAAAAAAEAAAAEADUAAQAAAAAAAgAAAAoACgAAAP8AAAAAAAAAAQPuAZAABQAAAnoCvAAAAIwCegK8AAAB4AAxAQIAAAIABQMAAAAAAAAAAAAAAAAAAAAAAAAAAAAAUGZFZABA4jToTQNS/2oAWgPoAJYAAAABAAAAAAAABAAAAAPoAAAD6AAAA+gAAAAAAAIAAAADAAAAFAADAAEAAAAUAAQANgAAAAgACAACAADiNOI56E3//wAA4jTiOehN//8AAAAAAAAAAQAIAAgACAAAAAEAAwACAAAAAAAAACYAcgCaAAAAAQAAAAADTAPoABUAAAkBBhY7AREUFjsBMjY1ETMyNicBJiIB3f7KCw4SxxAMqgwQxhIPC/7FCBgD3/6tDyH9wAwQEAwCQCEPAVMJAAEAAAAAA+oDTAA0AAABMx8BAR8DDwMBDwMjLwwhLwE1NzUnPwEhPwQ1PwQCXgIFCQFxBAIEAgEDBAf+ogYKBQUEAwQDAwICAQIBAQYJCf3mAgEDAgEBAh4KCAQCAQICAgIDA0wBBf7VAwQJCQkJCQf+4QQGAgEBAQIDBAQFC50DBAQDAQICCuANAgECBQIDAqcMBQQDAQAAAQAAAAADTAPoABYAAAEGFREjIgYXARYyNwE2JisBETQmKwEiAYsIxhIPDAE5CRgJATUMDhPGEAyqDAPgCAz9wCEP/q0JCQFTDyECQAwQAAAAABIA3gABAAAAAAAAAAEAAAABAAAAAAABAAcAAQABAAAAAAACAAcACAABAAAAAAADAAcADwABAAAAAAAEAAcAFgABAAAAAAAFAAsAHQABAAAAAAAGAAcAKAABAAAAAAAKACwALwABAAAAAAALABIAWwADAAEECQAAAAIAbQADAAEECQABAA4AbwADAAEECQACAA4AfQADAAEECQADAA4AiwADAAEECQAEAA4AmQADAAEECQAFABYApwADAAEECQAGAA4AvQADAAEECQAKAFgAywADAAEECQALACQBIyBlLWljb25zUmVndWxhcmUtaWNvbnNlLWljb25zVmVyc2lvbiAxLjBlLWljb25zRm9udCBnZW5lcmF0ZWQgdXNpbmcgU3luY2Z1c2lvbiBNZXRybyBTdHVkaW93d3cuc3luY2Z1c2lvbi5jb20AIABlAC0AaQBjAG8AbgBzAFIAZQBnAHUAbABhAHIAZQAtAGkAYwBvAG4AcwBlAC0AaQBjAG8AbgBzAFYAZQByAHMAaQBvAG4AIAAxAC4AMABlAC0AaQBjAG8AbgBzAEYAbwBuAHQAIABnAGUAbgBlAHIAYQB0AGUAZAAgAHUAcwBpAG4AZwAgAFMAeQBuAGMAZgB1AHMAaQBvAG4AIABNAGUAdAByAG8AIABTAHQAdQBkAGkAbwB3AHcAdwAuAHMAeQBuAGMAZgB1AHMAaQBvAG4ALgBjAG8AbQAAAAACAAAAAAAAAAoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAQBAgEDAQQBBQADVXAxC2Fycm93LXJpZ2h0CURvd25fU29ydAAAAA==) format('truetype');
  font-weight: normal;
  font-style: normal;
}

.pv-icons {
  font-family: 'e-pivot';
  font-style: normal;
  font-variant: normal;
  font-weight: normal;
  text-transform: none;
  line-height: 1;
}

.sb-icon-profit::before {
  content: '\e234';
  padding-left: 30px;
  margin: auto !important;
  color: #219122;
  size: 20px;
}

.sb-icon-neutral::before {
  content: '\e84d';
  padding-left: 30px;
  margin: auto !important;
  color: #82b5e9;
}

.sb-icon-loss::before {
  content: '\e239';
  padding-left: 30px;
  margin: auto !important;
  color: #ff2222;
}
</style>
```

{% endraw %}

{% endtab %}
