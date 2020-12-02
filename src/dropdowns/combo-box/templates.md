---
title: "Combo box Template"
component: "ComboBox"
description: "This section for Syncfusion vue combo box component demonstrates the customization of the appearance of each item in the pop-up list using template option."
---

# Templates

The ComboBox has been provided with several options to customize each list items, group title,
header, and footer elements.

To customize vue ComboBox items Using templates, you can check on this video:

`youtube:aeFDX7a70Tw`

## Item template

The content of each list item within the ComboBox can be customized with the
help of [itemTemplate](../api/combo-box/#itemtemplate)
property.

In the following sample, each list item is split into two columns to display relevant data's.

{% tab template="combobox/templates/item", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-dropdownlist id='dropdownlist' placeholder='Select an employee' sortOrder='Ascending' :itemTemplate='itemTemplate' :dataSource='dataSource' :query='query' :fields='fields'></ejs-dropdownlist>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(DropDownListPlugin);
import { DataManager,Query,ODataV4Adaptor } from "@syncfusion/ej2-data";

var itemVue = Vue.component("itemTemplate", {
  template: `<span><span class='name'>{{data.FirstName}}</span><span class ='city'>{{data.City}}</span></span>`,
  data() {
    return {
      data: {}
    };
  }
});

export default {
  data (){
      return {
        itemTemplate : function(e) {
                return {
                    template: itemVue
                };
        },
        query :  new Query().from('Employees').select(['FirstName', 'City', 'EmployeeID']).take(6),
        dataSource : new DataManager({
            url: 'https://services.odata.org/V4/Northwind/Northwind.svc/',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
        }),
        fields: { text: 'FirstName', value: 'EmployeeID' }
    }
  }
}

</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  .city {
    right: 15px;
    position: absolute;
  }
  .combobox {
    width: 30%;
    margin: 0 auto;
  }
  #app {
    color: #008cff;
    height: 40px;
    position: absolute;
    top: 10%;
    width: 90%;
  }

</style>
```

{% endtab %}

## Group template

The group header title under which appropriate sub-items are categorized can also be
customize with the help of
[groupTemplate](../api/combo-box/#grouptemplate) property.
This template is common for both inline and floating group header template.

In the following sample, employees are grouped according to their city.

{% tab template="combobox/templates/group", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div class='combobox'>
        <ejs-combobox id='combobox' sortOrder="Ascending" :dataSource='employeeData' :groupTemplate='groupTemplate' :fields='fields' :query='query' placeholder="Select an employee"></ejs-combobox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ComboBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(ComboBoxPlugin);
import { Query, DataManager, Predicate, ODataV4Adaptor } from '@syncfusion/ej2-data';

var groupVue = Vue.component("groupTemplate", {
  template: `<strong>{{data.City}}</strong>`,
  data() {
    return {
      data: {}
    };
  }
});

export default {
  data (){
    return {
        employeeData : new DataManager({
            url: 'https://services.odata.org/V4/Northwind/Northwind.svc/',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
        }),
        query : new Query().from('Employees').select(['FirstName', 'City', 'EmployeeID']).take(6).where(new Predicate('City', 'equal', 'london').or('City', 'equal', 'seattle')),
        fields : { text: 'FirstName', value: 'EmployeeID', groupBy: 'City' },
        groupTemplate : function(e) {
                return {
                    template: groupVue
                };
        },
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
    top: 10%;
    width: 90%;
  }

  .combobox {
    width: 30%;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Header template

The header element is shown statically at the top of the popup list items within the
ComboBox, and any custom element can be placed as a header element using the
[headerTemplate](../api/combo-box/#headertemplate) property.

In the following sample, the list items and its headers are designed and displayed as two columns
similar to multiple columns of the grid.

{% tab template="combobox/templates/header", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div class='combobox'>
        <br>
        <ejs-combobox id='combobox' sortOrder="Ascending" :dataSource='employeeData' :itemTemplate='itemTemplate' :headerTemplate='headerTemplate' :fields='fields' :query='query' placeholder="Select an employee"></ejs-combobox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ComboBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(ComboBoxPlugin);
import { Query, DataManager, Predicate, ODataV4Adaptor } from '@syncfusion/ej2-data';

export default {
  data (){
    return {
        employeeData : new DataManager({
            url: 'https://services.odata.org/V4/Northwind/Northwind.svc/',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
        }),
        query : new Query().from('Employees').select(['FirstName', 'City', 'EmployeeID']).take(6),
        fields : { text: 'FirstName', value: 'EmployeeID' },
        headerTemplate : "<span class='head'><span class='name'>Name</span><span class='city'>City</span></span>"
        itemTemplate : "<span class='item' ><span class='name'>${FirstName}</span><span class='city'>${City}</span></span>"
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  .head,
.item {
    display: table;
    width: 100%;
    margin: auto;
}

.head {
    height: 40px;
    font-size: 15px;
    font-weight: 600;
    text-indent: 1.067em;
}

.name,
.city {
    display: table-cell;
    vertical-align: middle;
    width: 50%;
}
  #app {
    color: #008cff;
    height: 40px;
    position: absolute;
    top: 10%;
    width: 90%;
  }

  .combobox {
    width: 30%;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Footer template

The ComboBox has options to show a footer element at the bottom of the list items in the popup list.
Here, you can place any custom element as a footer element using the
[footerTemplate](../api/combo-box/#footertemplate) property.

In the following sample, footer element displays the total number of list items present in the ComboBox.

{% tab template="combobox/templates/footer", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-combobox id='combobox' :dataSource='sportsData' :footerTemplate='footerTemplate' placeholder="Select a game"></ejs-combobox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ComboBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(ComboBoxPlugin);

var footerVue = Vue.component("footerTemplate", {
  template: `<span class='foot'> Total list item: 4</span>`,
  data() {
    return {
      data: {}
    };
  }
});

export default {
  data (){
      var data = ["BasketBall", "Cricket", "Football", "Golf"];
    return {
        sportsData: data,
        footerTemplate : function(e) {
          return {
            template: footerVue
          }
        }
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
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

The ComboBox is provided with support to custom design the popup list content when no data is found
and no matches found on search with the help of
[noRecordsTemplate](../api/combo-box/#norecordstemplate) property.

In the following sample, popup list content displays the notification of no data available.

{% tab template="combobox/templates/empty", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-combobox id='combobox' :dataSource='sportsData' :noRecordsTemplate='noRecordsTemplate' placeholder="Select an item"></ejs-combobox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ComboBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(ComboBoxPlugin);

var footerVue = Vue.component("noRecordsTemplate", {
  template: `<span class='norecord'> NO DATA AVAILABLE</span>`,
  data() {
    return {
      data: {}
    };
  }
});

export default {
  data (){
      var data = [];
    return {
        sportsData: data,
        noRecordsTemplate : function(e) {
          return {
            template: footerVue
          }
        }
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
</style>
```

{% endtab %}

## Action failure template

There is also an option to custom design the popup list content when the data fetch request
fails at the remote server. This can be achieved using the
[actionFailureTemplate](../api/combo-box/#actionfailuretemplate) property.

In the following sample, when the data fetch request fails, the ComboBox displays the notification.

{% tab template="combobox/templates/action-failure", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-combobox id='combobox' :dataSource='customerData' :actionFailureTemplate='actionFailureTemplate' :fields='fields' :query='query' placeholder="Select a customer"></ejs-combobox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ComboBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(ComboBoxPlugin);
import { Query, DataManager, Predicate, ODataV4Adaptor } from '@syncfusion/ej2-data';

var footerVue = Vue.component("actionFailureTemplate", {
  template: `<span class='action-failure'> Data fetch get fails</span>`,
  data() {
    return {
      data: {}
    };
  }
});

export default {
  data (){
    return {
        customerData : new DataManager({
           url: 'https://services.odata.org/V4/Northwind/Northwind.svcs/',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
        }),
        query : new Query().from('Customers').select(['ContactName', 'CustomerID']).take(6),
        fields : { text: 'ContactName', value: 'CustomerID' },
        actionFailureTemplate : function(e) {
          return {
            template: footerVue
          }
        }
        }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
</style>
```

{% endtab %}

## See Also

* [How to achieve filtering](./filtering/)
* [How to group the data using header](./grouping/)
* [How to show the list items with icon](./how-to/icons-support/)