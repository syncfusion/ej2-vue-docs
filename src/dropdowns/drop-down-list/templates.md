---
title: "Drop-down list Template"
component: "DropDownList"
description: "This section demonstrates on how to customize the appearance of each item in the pop-up list of Syncfusion vue drop-down list component using template option."
---

# Templates

The DropDownList has been provided with several options to customize each list item, group title,
selected value, header, and footer elements. It uses the Essential JS 2
`Template engine` to compile and render the elements properly.

## Item template

The content of each list item within the DropDownList can be customized with the
help of [itemTemplate](../api/drop-down-list/#itemtemplate)
property.

In the following sample, each list item is split into two columns to display relevant data's.

{% tab template="drop-down-list/templates/item-template", isDefaultActive=true %}

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
        itemTemplate : function() {
          return {template: itemVue};
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
</style>
```

{% endtab %}

## Value template

The currently selected value that is displayed by default on the DropDownList input
element can be customized using the [valueTemplate](../api/drop-down-list/#valuetemplate) property.

In the following sample, the selected value is displayed as a combined text of both `FirstName` and `City`
in the DropDownList input, which is separated by a hyphen.

{% tab template="drop-down-list/templates/value-template", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-dropdownlist id='dropdownlist' placeholder='Select an employee' sortOrder='Ascending' :itemTemplate='itemTemplate' :valueTemplate='valueTemplate' :dataSource='dataSource' :query='query' :fields='fields'></ejs-dropdownlist>
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

var valueVue = Vue.component("valueTemplate", {
  template: `<span>{{data.FirstName}} - {{data.City}}</span>`,
  data() {
    return {
      data: {}
    };
  }
});

export default {
  data (){
      return {
        itemTemplate : function() {
          return {template: itemVue};
        },
        valueTemplate: function() {
          return {template: valueVue};
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
</style>
```

{% endtab %}

## Group template

The group header title under which appropriate sub-items are categorized can also be
customize with the help of
[groupTemplate](../api/drop-down-list/#grouptemplate) property.
This template is common for both inline and floating group header template.

In the following sample, employees are grouped according to their city.

{% tab template="drop-down-list/templates/group-template", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:5px auto; width:250px;">
        <br>
        <ejs-dropdownlist id='dropdownlist' placeholder='Select an employee' sortOrder='Ascending' :groupTemplate="groupTemplate" :dataSource='dataSource' :query='query' :fields='fields'></ejs-dropdownlist>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(DropDownListPlugin);
import { DataManager,Query,ODataV4Adaptor,Predicate } from "@syncfusion/ej2-data";

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
        groupTemplate : function (e) {
          return {
            template: groupVue
          }
        },
        query :  new Query().from('Employees').select(['FirstName', 'City', 'EmployeeID']).take(6).where(new Predicate('City', 'equal', 'london').or('City', 'equal', 'seattle')),
        dataSource : new DataManager({
             url: 'https://services.odata.org/V4/Northwind/Northwind.svc/',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
        }),
        fields: { text: 'FirstName', value: 'EmployeeID', groupBy: 'City' }
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
</style>
```

{% endtab %}

## Header template

The header element is shown statically at the top of the popup list items within the
DropDownList, and any custom element can be placed as a header element using the
[headerTemplate](../api/drop-down-list/#headertemplate) property.

In the following sample, the list items and its headers are designed and displayed as two columns
similar to multiple columns of the grid.

{% tab template="drop-down-list/templates/header-template", isDefaultActive=true %}

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

var headerVue = Vue.component("headerTemplate", {
  template: `<span class='head'><span class='name'>Name</span><span class='city'>City</span></span>`,
  data() {
    return {
      data: {}
    };
  }
});

var itemVue = Vue.component("itemTemplate", {
  template: `<span class='item' ><span class='name'>{{data.FirstName}}</span><span class='city'>{{data.City}}</span></span>`,
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
        query : new Query().from('Employees').select(['FirstName', 'City', 'EmployeeID']).take(6),
        fields : { text: 'FirstName', value: 'EmployeeID' },
        headerTemplate :  function(e) {
                return {
                    template: headerVue
                };
        },
        itemTemplate : function(e) {
                return {
                    template: itemVue
                };
        }
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
}

.name,
.city {
    display: table-cell;
    vertical-align: middle;
    width: 50%;
}

.head .name {
    text-indent: 16px;
 }

 .head .city {
    text-indent: 10px;
 }
   #app {
      color: #008cff;
      height: 40px;
      position: absolute;
      width: 90%;
      top: 10%;
    }

  .combobox {
    width: 30%;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Footer template

The DropDownList has options to show a footer element at the bottom of the list items in the popup list.
Here, you can place any custom element as a footer element using
the [footerTemplate](../api/drop-down-list/#footertemplate) property.

In the following sample, footer element displays the total number of list items present in the DropDownList.

{% tab template="drop-down-list/templates/footer-template", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-dropdownlist id='dropdownlist' placeholder='Select a game' :footerTemplate='footerTemplate' :dataSource='dataSource'></ejs-dropdownlist>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(DropDownListPlugin);
var itemVue = Vue.component("itemTemplate", {
  template: `<span class='foot'> Total list item: 5</span>`,
  data() {
    return {
      data: {}
    };
  }
});
export default {
  data (){
      var sportsData =  ['Badminton', 'Cricket', 'Football', 'Golf', 'Tennis'];
    return {
        footerTemplate : function(e) {
          return {
            template: itemVue
          }
        },
        dataSource : sportsData,
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

The DropDownList is provided with support to custom design the popup list content when no data is found
and no matches found on search with the help of
[noRecordsTemplate](../api/drop-down-list/#norecordstemplate) property.

In the following sample, popup list content displays the notification of no data available.

{% tab template="drop-down-list/templates/no-template", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-dropdownlist id='dropdownlist' placeholder='Select an item' :noRecordsTemplate='noRecordsTemplate' :dataSource='dataSource'></ejs-dropdownlist>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(DropDownListPlugin);
var itemVue = Vue.component("noRecordsTemplate", {
  template: `<span class='norecord'> NO DATA AVAILABLE</span>`,
  data() {
    return {
      data: {}
    };
  }
});
export default {
    data (){
      var sportsData =  [];
    return {
        noRecordsTemplate : function (e) {
          return {
            template: itemVue
          }
        },
        dataSource : sportsData
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
[actionFailureTemplate](../api/drop-down-list/#actionfailuretemplate) property.

In the following sample, when the data fetch request fails, the DropDownList displays the notification.

{% tab template="drop-down-list/templates/failure-template", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-dropdownlist id='dropdownlist' placeholder='Select an customer' sortOrder='Ascending' :actionFailureTemplate='failureTemplate' :dataSource='dataSource' :query='query' :fields='fields'></ejs-dropdownlist>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(DropDownListPlugin);
import { DataManager,Query,ODataV4Adaptor } from "@syncfusion/ej2-data";
var itemVue = Vue.component("failureTemplate", {
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
        failureTemplate : function(e) {
          return {
            template: itemVue
          }
        },
        query :  new Query().from('Customers').select(['ContactName', 'CustomerID']).take(6),
        dataSource : new DataManager({
             url: 'https://services.odata.org/V4/Northwind/Northwind.svcs/',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
        }),
        fields: { text: 'ContactName', value: 'CustomerID' }
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
* [How to render tooltip for the options](./how-to/tooltip/)