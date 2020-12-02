---
title: "Autocomplete Template"
component: "AutoComplete"
description: "This section for Syncfusion vue autocomplete component explains on how to customize the appearance of each item in the pop-up list using template option."
---

# Templates

The AutoComplete has been provided with several options to customize each list items,
group title, header and footer elements. It uses the Essential JS 2 Template engine
to compile and render the elements properly.

## Item template

The content of each list item within the AutoComplete can be customized with the help of [`itemTemplate`](../api/auto-complete/#itemtemplate) property.
In the following sample, each list item is split into two columns to display relevant data's.

{% tab template="auto-complete/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='autocomplete'>
        <ejs-autocomplete id='employees' :query='query' :dataSource='data' :fields='fields' :placeholder='waterMark' :sortOrder='sortOrder' :itemTemplate='iTemplate' popupHeight="450px"></ejs-autocomplete>
     </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { AutoCompletePlugin } from '@syncfusion/ej2-vue-dropdowns';
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

Vue.use(AutoCompletePlugin);

var itemVue = Vue.component("itemTemplate", {
  template: `<span><span class='name'>{{data.FirstName}}</span><span class ='city'>{{data.City}}</span></span>`,
  data() {
    return {
      data: {}
    };
  }
});

var remoteData = new DataManager({
    url: 'https://services.odata.org/V4/Northwind/Northwind.svc',
    adaptor: new ODataV4Adaptor,
    crossDomain: true
});

export default {
  name: 'app',
   data () {
    return {
      fields: { value: 'FirstName' },
            waterMark: 'Find an employee',
            sortOrder: 'Ascending',
            data: remoteData,
            iTemplate: function(e) {
                return {
                    template: itemVue
                };
            },
          query: new Query().from('Employees').select(['FirstName', 'City', 'EmployeeID']).take(6),
    }
  }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  #app {
    color: #008cff;
    height: 40px;
    position: absolute;
    width: 90%;
    top: 10%;
  }

  .autocomplete {
    width: 30%;
    margin: 0 auto;
  }

  .city{
    right: 15px;
    position: absolute;
  }
</style>
```

{% endtab %}

## Group template

The group header title under which appropriate sub-items are categorized can also be
customize with the help of [`groupTemplate`](../api/auto-complete/#grouptemplate) property. This template is common for both
inline and floating group header template.

In the following sample, employees are grouped according to their city.

{% tab template="auto-complete/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='autocomplete'>
        <ejs-autocomplete id='employees' :query='query' :dataSource='data' :fields='fields' :placeholder='waterMark' :sortOrder='sortOrder' :groupTemplate='gTemplate' popupHeight="450px"></ejs-autocomplete>
      </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { AutoCompletePlugin } from '@syncfusion/ej2-vue-dropdowns';
import { Query, Predicate, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

Vue.use(AutoCompletePlugin);

var groupTemplate = Vue.component("groupTemplate", {
  template: `<strong>{{data.City}}</strong>`,
  data() {
    return {
      data: {}
    };
  }
});

var remoteData = new DataManager({
    url: 'https://services.odata.org/V4/Northwind/Northwind.svc',
    adaptor: new ODataV4Adaptor,
    crossDomain: true
});

export default {
  name: 'app',
   data () {
    return {
      fields: { value: 'FirstName', groupBy:'City' },
            waterMark: 'Find an employee',
            sortOrder: 'Ascending',
            data: remoteData,
            gTemplate: function(e) {
                return {
                    template: groupTemplate
                };
            },
            query: new Query().from('Employees').select(['FirstName', 'City', 'EmployeeID']).take(6).where(new Predicate('City', 'equal','london').or('City','equal','seattle')),
    }
  }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  #app {
    color: #008cff;
    height: 40px;
    position: absolute;
    width: 90%;
    top: 10%;
  }

  .autocomplete {
    width: 30%;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Header template

The header element is shown statically at the top of the suggestion list items within
the AutoComplete, and any custom element can be placed as a header element using
[`headerTemplate`](../api/auto-complete/#headertemplate) property.

In the following sample, the list items and its headers are designed and displayed as two columns similar to multiple columns of the grid.

{% tab template="auto-complete/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
     <div class='autocomplete'>
        <ejs-autocomplete id='employees' :query='query' :dataSource='data' :fields='fields' :placeholder='waterMark' :headerTemplate='hTemplate' :sortOrder='sortOrder' :itemTemplate='iTemplate' popupHeight="450px"></ejs-autocomplete>
     </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { AutoCompletePlugin } from '@syncfusion/ej2-vue-dropdowns';
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

Vue.use(AutoCompletePlugin);

var headerVue = Vue.component("headerTemplate", {
  template: `<span class='head'><span class='name'>Name</span><span class='city'>City</span></span>`,
  data() {
    return {
      data: {}
    };
  }
});

var itemVue = Vue.component("itemTemplate", {
  template: `<span class='item'><span class='name'> {{data.FirstName}}</span><span class ='city'>{{data.City}}</span></span>`,
  data() {
    return {
      data: {}
    };
  }
});

var remoteData = new DataManager({
    url: 'https://services.odata.org/V4/Northwind/Northwind.svc',
    adaptor: new ODataV4Adaptor,
    crossDomain: true
});

export default {
  name: 'app',
   data () {
    return {
      fields: { value: 'FirstName' },
            waterMark: 'Find an employee',
            sortOrder: 'Ascending',
            data: remoteData,
            iTemplate: function(e) {
                return {
                    template: itemVue
                };
            },
            hTemplate: function(e) {
                return {
                    template: headerVue
                };
            },
            query: new Query().from('Employees').select(['FirstName', 'City', 'EmployeeID']).take(6),
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  #app {
    color: #008cff;
    height: 40px;
    position: absolute;
    width: 90%;
    top: 10%;
  }

  .autocomplete {
    width: 30%;
    margin: 0 auto;
  }
  .city{
    right: 15px;
    position: absolute;
  }
</style>
```

{% endtab %}

## Footer template

The AutoComplete has options to show a footer element at the bottom of the list items
in the suggestion list. Here, you can place any custom element as a footer element
using [`footerTemplate`](../api/auto-complete/#footertemplate) property.

In the following sample, footer element displays the total number of list items present in the AutoComplete.

{% tab template="auto-complete/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='autocomplete'>
        <ejs-autocomplete ref='instance' :footerTemplate='fTemplate' id='employees' :dataSource='data' :placeholder='waterMark' :open='onopen'></ejs-autocomplete>
     </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { AutoCompletePlugin } from '@syncfusion/ej2-vue-dropdowns';

Vue.use(AutoCompletePlugin);

var footVue = Vue.component("footerTemplate", {
  template: `<span class='foot'></span>`,
  data() {
    return {
      data: {}
    };
  }
});

export default {
  name: 'app',
  mounted() {
    document.getElementsByClassName('e-autocomplete')[0].addEventListener('keyup', (e) => {
      this.onopen();
    })
  },
   data () {
    return {
            waterMark: 'Find a game',
            sortOrder: 'Ascending',
            data: ['Badminton', 'Basketball', 'Cricket',
                'Football', 'Golf', 'Gymnastics',
                'Hockey', 'Rugby', 'Snooker', 'Tennis'
            ],
            fTemplate: function(e) {
                return {
                    template: footVue
                };
            },
    }
  },
  methods: {
    onopen: function() {
      var count = this.$refs.instance.getItems().length;
      var ele = document.getElementsByClassName('foot')[0];
      ele.innerHTML =  "Total list item: " + count;
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  #app {
      color: #008cff;
      height: 40px;
      position: absolute;
      width: 90%;
      top: 10%;
    }

  .autocomplete {
    width: 30%;
    margin: 0 auto;
  }

  .foot {
    text-indent: 1.2em;
    display: block;
    font-size: 15px;
    line-height: 40px;
    border-top: 1px solid #e0e0e0;
  }
</style>
```

{% endtab %}

## No records template

The AutoComplete is provided with support to custom design the popup list content when
no data is found and no matches found on search with the help of [`noRecordsTemplate`](../api/auto-complete/#norecordstemplate)
property.

In the following sample, popup list content displays the notification of no data available.

{% tab template="auto-complete/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='autocomplete'>
        <ejs-autocomplete ref='instance' id='employees' :dataSource='data' :placeholder='waterMark' :noRecordsTemplate='nTemplate'></ejs-autocomplete>
     </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { AutoCompletePlugin } from '@syncfusion/ej2-vue-dropdowns';

Vue.use(AutoCompletePlugin);

var nVue = Vue.component("noRecordsTemplate", {
  template: `<span class="norecord"> NO DATA AVAILABLE</span>`,
  data() {
    return {
      data: {}
    };
  }
});

export default {
  name: 'app',
   data () {
    return {
            waterMark: 'Find an item',
            data: [],
            nTemplate: function(e) {
                return {
                    template: nVue
                };
            },
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";;
  #app {
      color: #008cff;
      height: 40px;
      position: absolute;
      width: 90%;
      top: 10%;
    }

  .autocomplete {
    width: 30%;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Action failure template

There is also an option to custom design the popup list content when the data fetch
request fails at the remote server. This can be achieved using the actionFailureTemplate property.

In the following sample, when the data fetch request fails, the AutoComplete displays the notification.

{% tab template="auto-complete/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='autocomplete'>
        <ejs-autocomplete ref='instance' :fields='fields' :query='query' id='employees' :dataSource='data' :placeholder='waterMark' :actionFailureTemplate='actionTemplate'></ejs-autocomplete>
     </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { AutoCompletePlugin } from '@syncfusion/ej2-vue-dropdowns';
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

Vue.use(AutoCompletePlugin);

var actionVue = Vue.component("actionFailureTemplate", {
  template: `<span class="action-failure"> Data fetch got failed</span>`,
  data() {
    return {
      data: {}
    };
  }
});

var remoteData = new DataManager({
    url: 'https://services.odata.org/V4/Northwind/Northwind.svcs',
    adaptor: new ODataV4Adaptor,
    crossDomain: true
});

export default {
  name: 'app',
   data () {
    return {
            waterMark: 'Find an employee',
            data: remoteData,
            actionTemplate: function(e) {
                return {
                    template: actionVue
                };
            },
            query: new Query().from('Employees').select(['FirstName']).take(6),
            fields: { value: 'FirstName' }
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  #app {
      color: #008cff;
      height: 40px;
      position: absolute;
      width: 90%;
      top: 10%;
    }

  .autocomplete {
    width: 30%;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## See Also

* [How to achieve filtering](./filtering/)
* [How to group the data using header](./grouping#grouping)
* [How to show the list items with icon](./how-to/icon-support/)