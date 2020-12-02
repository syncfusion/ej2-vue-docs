---
title: "Multiselect Template"
component: "MultiSelect"
description: "This section demonstrates the customization of the appearance of each item in the pop-up list of Syncfusion vue multiselect component using template option."
---

# Templates

The MultiSelect has been provided with several options to customize each list item, group title,
selected value, header, and footer elements.

To customize MultiSelect dropdown items Using templates, you can check on this video:

`youtube:biPKSEpTgwM`

## Item template

The content of each list item within the MultiSelect can be customized with the
help of [itemTemplate](../api/multi-select/#itemtemplate)
property.

In the following sample, each list item is split into two columns to display relevant data's.

{% tab template="multi-select/template/item", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-multiselect id='multiselect' sortOrder='Ascending' :itemTemplate='itemTemplate' :dataSource='employeeData' :query='query' :fields='fields' placeholder="Select an employee"></ejs-multiselect>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { MultiSelectPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(MultiSelectPlugin);
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

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
      employeeData : new DataManager({
            url: 'https://services.odata.org/V4/Northwind/Northwind.svc/',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
      }),
      query : new Query().from('Employees').select(['FirstName', 'City', 'EmployeeID']).take(6),
      fields : { text: 'FirstName', value: 'EmployeeID' },
      itemTemplate : function(e) {
        return {
          template: itemVue
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
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
.city {
    right: 15px;
    position: absolute;
}
</style>
```

{% endtab %}

## Value template

The currently selected value that is displayed by default on the MultiSelect input element can be customized using the
[valueTemplate](../api/multi-select/#valuetemplate) property.

In the following sample, the selected value is displayed as a combined text of both `FirstName` and `City`
in the MultiSelect input, which is separated by a hyphen.

{% tab template="multi-select/template/value", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-dropdownlist id='dropdownlist' placeholder='Select an employee' sortOrder='Ascending' :valueTemplate="valueTemplate" :itemTemplate="itemTemplate" :dataSource='dataSource' :query='query' :fields='fields'></ejs-dropdownlist>
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
        valueTemplate : function(e) {
          return {
            template: valueVue
          }
        },
        itemTemplate : function(e) {
          return {
            template: itemVue
          }
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
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
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
[groupTemplate](../api/multi-select/#grouptemplate) property.
This template is common for both inline and floating group header template.

In the following sample, employees are grouped according to their city.

{% tab template="multi-select/template/group", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-multiselect id='multiselect' sortOrder='Ascending' :groupTemplate='groupTemplate' :dataSource='employeeData' :query='query' :fields='fields' placeholder="Select an employee"></ejs-multiselect>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { MultiSelectPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(MultiSelectPlugin);
import { Query, DataManager, ODataV4Adaptor, Predicate } from '@syncfusion/ej2-data';
var itemVue = Vue.component("groupTemplate", {
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
          template: itemVue
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
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
</style>
```

{% endtab %}

## Header template

The header element is shown statically at the top of the popup list items within the
MultiSelect, and any custom element can be placed as a header element using the
[headerTemplate](../api/multi-select/#headertemplate) property.

In the following sample, the list items and its headers are designed and displayed as two columns
similar to multiple columns of the grid.

{% tab template="multi-select/template/header", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-multiselect id='multiselect' sortOrder='Ascending' :headerTemplate='headerTemplate' :itemTemplate='itemTemplate' :dataSource='employeeData' :query='query' :fields='fields' placeholder="Select an employee"></ejs-multiselect>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { MultiSelectPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(MultiSelectPlugin);
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

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
      headerTemplate : function(e) {
        return {
          template: headerVue
        }
      },
      itemTemplate : function(e) {
        return {
          template: itemVue
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
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
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
</style>
```

{% endtab %}

## Footer template

The MultiSelect has options to show a footer element at the bottom of the list items in the popup list. Here, you can place
 any custom element as a footer element using the [footerTemplate](../api/multi-select/#footertemplate) property.

In the following sample, footer element displays the total number of list items present in the MultiSelect.

{% tab template="multi-select/template/footer", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-multiselect id='multiselect' :dataSource='sportsData' :footerTemplate='footerTemplate' :open='onPopupOpen' :select='updateDataCount' placeholder="Select a game"></ejs-multiselect>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { MultiSelectPlugin } from "@syncfusion/ej2-vue-dropdowns";
import { isNullOrUndefined } from "@syncfusion/ej2-base";
Vue.use(MultiSelectPlugin);

var footerVue = Vue.component("footerTemplate", {
  template: `<span class='foot'></span>`,
  data() {
    return {
      data: {}
    };
  }
});
export default {
  data (){
    var data = ['Badminton', 'Cricket', 'Football', 'Golf', 'Tennis'];
    return {
      sportsData: data,
      footerTemplate : function(e) {
        return {
          template: footerVue
        }
      }
    }
  },
  methods: {
    updateDataCount: function() {
      var remainingDatasCount = document.querySelectorAll('.e-list-item').length - document.querySelectorAll('.e-hide-listitem').length;
      if (remainingDatasCount !== 0) {
        document.querySelector('.foot').innerText = "Total list item: " + (remainingDatasCount -1);
      }
    },
    onPopupOpen: function(e) {
        e.popup.element.querySelector('.foot').innerText  = "Total list item: " + (5- document.querySelectorAll('.e-chips-collection .e-chips').length);
    }
  }
}

</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
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

The MultiSelect is provided with support to custom design the popup list content when no data is found
and no matches found on search with the help of
[noRecordsTemplate](../api/multi-select/#norecordstemplate) property.

In the following sample, popup list content displays the notification of no data available.

{% tab template="multi-select/template/no-records", isDefaultActive=true %}

```html

<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-multiselect id='multiselect' :dataSource='data' :noRecordsTemplate='noRecordsTemplate' placeholder="Select an item"></ejs-multiselect>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { MultiSelectPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(MultiSelectPlugin);

var footerVue = Vue.component("footerTemplate", {
  template: `<span class='norecord'> NO DATA AVAILABLE</span>`,
  data() {
    return {
      data: {}
    };
  }
});

export default {
  data (){
    return {
      data: [],
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
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
</style>
```

{% endtab %}

## Action failure template

There is also an option to custom design the popup list content when the data fetch request
fails at the remote server. This can be achieved using the
[actionFailureTemplate](../api/multi-select/#actionfailuretemplate) property.

In the following sample, when the data fetch request fails, the MultiSelect displays the notification.

{% tab template="multi-select/template/action", isDefaultActive=true %}

```html

<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-multiselect id='multiselect' :actionFailureTemplate='actionFailureTemplate' :dataSource='customerData' :query='query' :fields='fields' placeholder="Select a customer"></ejs-multiselect>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { MultiSelectPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(MultiSelectPlugin);
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

var footerVue = Vue.component("footerTemplate", {
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
      actionFailureTemplate : function (e) {
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
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
</style>
```

{% endtab %}

## See Also

* [How to bind the data](./data-binding/)
* [How to group the data using header](./grouping/)
* [How to customize the options in MultiSelect](./chip-customization/)