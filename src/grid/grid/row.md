---
title: "Row"
component: "Grid"
description: "Documentation for row templates (custom row content), detail templates, and DataGrid row styles."
---

# Row

It represents the record details that are fetched from the data source.

## Drag and Drop

The Grid Row drag and drop allows you to drag grid rows and drop to another Grid or custom component.
To enable Row drag and drop in the Grid, set the [`allowRowDragAndDrop`](../api/grid/#allowrowdraganddrop) to true.
The target component on which the Grid rows to be dropped can be set by using
[`targetID`](../api/grid/rowDropSettings/#targetid).

To use Row Drag and Drop, you need to inject `RowDD` in the `provide` section.

{% tab template="grid/row/default" %}

```html
<template>
    <div id="app">
        <ejs-grid id='Grid' :dataSource='srcData' :allowPaging="true" :pageSettings="pageOptions" :allowSelection="true" :allowRowDragAndDrop="true"
            :selectionSettings="selectionOptions" :rowDropSettings="srcDropOptions" width="49%">
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' width='120' textAlign='Right'></e-column>
                <e-column field='CustomerID' headerText='Customer Name' width='130'></e-column>
                <e-column field='Freight' headerText='Freight' width='120' format='C2' textAlign='Right'></e-column>
            </e-columns>
        </ejs-grid>

        <ejs-grid id='DestGrid' :dataSource='destData' :allowPaging="true" :pageSettings="pageOptions" :allowSelection="true"
            :allowRowDragAndDrop="true" :selectionSettings="selectionOptions" :rowDropSettings="destDropOptions" width="49%">
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' width='120' textAlign='Right'></e-column>
                <e-column field='CustomerID' headerText='Customer Name' width='130'></e-column>
                <e-column field='Freight' headerText='Freight' width='120' format='C2' textAlign='Right'></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, RowDD, Selection, Page  } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      srcData: data,
      pageSettings: { pageSize: 7 },
      destData: [],
      pageOptions: { pageSize: 7 },
      selectionOptions: { type: "Multiple" },
      srcDropOptions: { targetID: "DestGrid" },
      destDropOptions: { targetID: "Grid" }
    };
  },
  provide: {
    grid: [RowDD, Page, Selection]
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
  #Grid {
    float: left;
  }

  #DestGrid {
    float: right;
  }
</style>
```

{% endtab %}

> * Selection feature must be enabled for row drag and drop.
> * Multiple rows can be selected by clicking and dragging inside the grid.
For multiple row selection, the [`type`](../api/grid/selectionSettings/#type) property must be set to `Multiple`.

## Row spanning

The grid has option to span row cells. To achieve this, You need to define the [`rowSpan`](../api/grid/queryCellInfoEventArgs/#rowspan) attribute to span cells in the [`QueryCellInfo`](../api/grid/queryCellInfoEventArgs/) event.

In the following demo, `Davolio` cell is spanned to two rows in the `EmployeeName` column.

Also Grid supports the spanning of rows and columns for same cells. `Lunch Break` cell is spanned to two rows and three columns in the `1:00` column.

{% tab template="grid/column/spanning" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" height='300' width='auto' gridLines='Both' :allowTextWrap='true' :queryCellInfo='queryCellInfoEvent'>
            <e-columns>
                <e-column field='EmployeeID' headerText='Employee ID' width='150' textAlign='Right' isPrimaryKey={true}></e-column>
                <e-column field='EmployeeName' headerText='Employee Name' width='200'></e-column>
                <e-column field='9:00' headerText='9:00 AM' width='120'></e-column>
                <e-column field='9:30' headerText='9:30 AM' width='120'></e-column>
                <e-column field='10:00' headerText='10:00 AM' width='120'></e-column>
                <e-column field='10:30' headerText='10:30 AM' width='120'></e-column>
                <e-column field='11:00' headerText='11:00 AM' width='120'></e-column>
                <e-column field='11:30' headerText='11:30 AM' width='120'></e-column>
                <e-column field='12:00' headerText='12:00 PM' width='120'></e-column>
                <e-column field='12:30' headerText='12:30 PM' width='120'></e-column>
                <e-column field='1:00' headerText='1:00 PM' width='120'></e-column>
                <e-column field='1:30' headerText='1:30 PM' width='120'></e-column>
                <e-column field='2:00' headerText='2:00 PM' width='120'></e-column>
                <e-column field='2:30' headerText='2:30 PM' width='120'></e-column>
                <e-column field='3:00' headerText='3:00 PM' width='120'></e-column>
                <e-column field='3:30' headerText='3:30 PM' width='120'></e-column>
                <e-column field='4:00' headerText='4:00 PM' width='120'></e-column>
                <e-column field='4:30' headerText='4:30 PM' width='120'></e-column>
                <e-column field='5:00' headerText='5:00 PM' width='120'></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from 'vue';
import { GridPlugin } from '@syncfusion/ej2-vue-grids';
import { data  } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data: () => {
      return {
        data: data
        }
  },
  methods: {
    queryCellInfoEvent: function(args) {
        let data = args.data;
    switch (data.EmployeeID) {
        case 10001:
            if (args.column.field === '9:00' || args.column.field === '2:30' || args.column.field === '4:30') {
                args.colSpan = 2;
            } else if (args.column.field === '11:00') {
                args.colSpan = 3;
            } else if (args.column.field === 'EmployeeName') {
                args.rowSpan = 2;
            } else if (args.column.field === '1:00') {
                args.colSpan = 3;
                args.rowSpan = 2;
            }
            break;
        case 10002:
            if (args.column.field === '9:30' || args.column.field === '2:30' ||
                args.column.field === '4:30') {
                args.colSpan = 3;
            } else if (args.column.field === '11:00') {
                args.colSpan = 4;
            }
            break;
        case 10003:
            if (args.column.field === '9:00' || args.column.field === '11:30') {
                args.colSpan = 3;
            } else if (args.column.field === '10:30' || args.column.field === '3:30' ||
                args.column.field === '4:30' || args.column.field === '2:30') {
                args.colSpan = 2;
            }
            break;
        case 10004:
            if (args.column.field === '9:00') {
                args.colSpan = 3;
            } else if (args.column.field === '11:00') {
                args.colSpan = 4;
            } else if (args.column.field === '4:00' || args.column.field === '2:30') {
                args.colSpan = 2;
            }
            break;
        case 10005:
            if (args.column.field === '9:00') {
                args.colSpan = 4;
            } else if (args.column.field === '11:30') {
                args.colSpan = 3;
            } else if (args.column.field === '3:30' || args.column.field === '4:30' || args.column.field === '2:30') {
                args.colSpan = 2;
            }
            break;
        case 10006:
            if (args.column.field === '9:00' || args.column.field === '4:30' ||
                args.column.field === '2:30' || args.column.field === '3:30') {
                args.colSpan = 2;
            } else if (args.column.field === '10:00' || args.column.field === '11:30') {
                args.colSpan = 3;
            }
            break;
        case 10007:
            if (args.column.field === '9:00' || args.column.field === '3:00' || args.column.field === '10:30') {
                args.colSpan = 2;
            } else if (args.column.field === '11:30' || args.column.field === '4:00') {
                args.colSpan = 3;
            }
            break;
        default:
            this.extendQueryCellEvent(args, data.EmployeeID);
        }
    },
    extendQueryCellEvent: function(args, value) {
        switch (value) {
        case 10008:
            if (args.column.field === '9:00' || args.column.field === '10:30' || args.column.field === '2:30') {
                args.colSpan = 3;
            } else if (args.column.field === '4:00') {
                args.colSpan = 2;
            }
            break;
        case 10009:
            if (args.column.field === '9:00' || args.column.field === '11:30') {
                args.colSpan = 3;
            } else if (args.column.field === '4:30' || args.column.field === '2:30') {
                args.colSpan = 2;
            }
            break;
        case 100010:
            if (args.column.field === '9:00' || args.column.field === '2:30' ||
                args.column.field === '4:00' || args.column.field === '11:30') {
                args.colSpan = 3;
            } else if (args.column.field === '10:30') {
                args.colSpan = 2;
            }
            break;
        }
    }
    }
  });
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> * To disable the spanning for particular grid page, we need to use `requestType` from [`QueryCellInfo`](../api/grid/queryCellInfoEventArgs/) event argument.

## Customize Rows

You can customize the appearance of the Row by using the [`rowDataBound`](../api/grid/#rowdatabound) event.
The [`rowDataBound`](../api/grid/#rowdatabound) event triggers for every row. In that event handler,
you can get [`RowDataBoundEventArgs`](../api/grid/rowDataBoundEventArgs/) which contain details of the row.

{% tab template="grid/row/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data"  :enableHover='false' :allowSelection='false' height='315' :rowDataBound='rowDataBound'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
            <e-column field='OrderDate' headerText='Order Date' textAlign='Right' format='yMd' type='date' width=120> </e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  methods: {
    rowDataBound: function(args) {
        if (args.data['Freight'] < 30) {
            args.row.classList.add('below-30');
        } else if (args.data['Freight'] < 80) {
            args.row.classList.add('below-80');
        } else {
            args.row.classList.add('above-80');
        }
    }
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
  .below-30 {
    background-color: orangered;
  }

  .below-80 {
    background-color: yellow;
  }

  .above-80 {
    background-color: greenyellow
  }
</style>
```

{% endtab %}

## Styling alternate Row

You can change the grid's alternative rows' background color by overriding the `.e-altrow` class.

```css
.e-grid .e-altrow {
    background-color: #fafafa;
}
```

Please refer the following example.

{% tab template="grid/row/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data">
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
            <e-column field='OrderDate' headerText='Order Date' textAlign='Right' format='yMd' type='date' width=120> </e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
  .e-grid .e-altrow {
    background-color: #fafafa;
  }
</style>
```

{% endtab %}

## Row height

You can customize the row height of grid rows through the [`rowHeight`](../api/grid/#rowheight) property. The `rowHeight` property
is used to change the row height of entire grid rows.

In the below example, the `rowHeight` is set as '60px'.

{% tab template="grid/row/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" :enableHover='false' :allowSelection='false' height='295' rowHeight=60>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
            <e-column field='OrderDate' headerText='Order Date' textAlign='Right' format='yMd' type='date' width=120> </e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

### Customize row height for particular row

Grid row height for particular row can be customized using the [`rowDataBound`](../api/grid/#rowdatabound)
event by setting the `rowHeight` in arguments for each row based on the requirement.

In the below example, the row height for the row with OrderID as '10249' is set as '90px' using the `rowDataBound` event.

{% tab template="grid/row/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" height='315' :rowDataBound='rowDataBound'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
            <e-column field='OrderDate' headerText='Order Date' textAlign='Right' format='yMd' type='date' width=120 > </e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  methods: {
    rowDataBound: (args) {
      if (args.data['OrderID'] === 10249) {
          args.rowHeight = 90;
      }
    }
  }
});
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> * In virtual scrolling mode, it is not applicable to set the `rowHeight` using the `rowDataBound` event.

## Row Template

The [`rowTemplate`](../api/grid/#rowtemplate) has options to display custom `<tr>` element.

The `rowTemplate` property should be a function which returns an object. The object should contain a Vue component which should be assigned to the `template` property. The grid will look for the template property and render it as new Vue instance.

> In `rowTemplate`, the Vue component `template` should be a `<tr>` element.

{% tab template="grid/column/template" %}

{% raw %}

```html
<template>
    <div id="app">
      <ejs-grid :dataSource="data" height=310 width='auto' :rowTemplate='rowTemplate' >
        <e-columns>
            <e-column field='Employee Image' headerText='Employee Image' width='150' textAlign='Center'></e-column>
            <e-column field='Employee Details' headerText='Employee Details' width='300' textAlign='Left'></e-column>
        </e-columns>
      </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { employeeData } from "./datasource.js";
import { Internationalization } from '@syncfusion/ej2-base';

let instance = new Internationalization();

Vue.use(GridPlugin);

export default {
  data: () => {
    return {
      data: employeeData,
      rowTemplate: function () {
        return { template : Vue.component('rowTemplate',{
        template: `<tr>
        <td class="rowphoto">
            <img :src="image" :alt="altImage" />
        </td>
        <td class="details">
            <table class="CardTable" cellpadding="3" cellspacing="2">
                <colgroup>
                    <col width="50%">
                    <col width="50%">
                </colgroup>
                <tbody>
                    <tr>
                        <td class="CardHeader">First Name </td>
                        <td>{{data.FirstName}} </td>
                    </tr>
                    <tr>
                        <td class="CardHeader">Last Name</td>
                        <td>{{data.LastName}} </td>
                    </tr>
                    <tr>
                        <td class="CardHeader">Title</td>

                        <td>{{data.Title}} </td>
                    </tr>
                    <tr>
                        <td class="CardHeader">Birth Date</td>
                        <td>{{format(data.BirthDate)}} </td>
                    </tr>
                    <tr>
                        <td class="CardHeader">Hire Date</td>
                        <td>{{format(data.HireDate)}} </td>
                    </tr>
                </tbody>
            </table>
        </td>
    </tr>`,
          data: function() {
            return {
              data: {}
            }
          },
          methods: {
            format: function(value) {
                return instance.formatDate(value, { skeleton: 'yMd', type: 'date' });
            }
          },
          computed: {
            image: function() {
              return './' + this.data.EmployeeID + '.png';
            },
            altImage: function() {
              return this.data.EmployeeID;
            }
          }
        })}
      }
    };
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";

  .rowphoto img {
        width: 100px;
        height: 100px;
        border-radius: 50px;
        box-shadow: inset 0 0 1px #e0e0e0, inset 0 0 14px rgba(0,0,0,0.2);
    }

    @media screen and (max-width: 600px) and (min-width: 320px) {
        .rowphoto img {
            width: 50px;
            height: 50px;
        }
    }

    @media screen and (max-width: 800px) and (min-width: 600px) {
        .rowphoto img {
            width: 70px;
            height: 70px;
        }
    }

    .rowphoto,
    .details {
        border-color: #e0e0e0;
        border-style: solid;
    }

    .rowphoto {
        border-width: 1px 0px 0px 0px;
        text-align: center;
    }

    .details {
        border-width: 1px 0px 0px 0px;
        padding-left: 18px;
    }

    .e-bigger .details {
        padding-left: 25px;
    }

    .e-device .details {
        padding-left: 8px;
    }

    .details > table {
        width: 100%;
    }

    .CardHeader {
        font-weight: bolder;
    }

    td {
        padding: 2px 2px 3px 4px;
    }
</style>
```

{% endraw %}

{% endtab %}

## Detail Template

The [`detailTemplate`](../api/grid/#detailtemplate) provides an additional information about a data row which can show or hide by clicking on expand or collapse button. The [`detailTemplate`](../api/grid/#detailtemplate) property accepts the template for the detail row.

The [`detailTemplate`](../api/grid/#detailtemplate) property should be a function which returns an object. The object should contain a Vue component which should be assigned to the `template` property. The grid will look for the template property and render it as new Vue instance.

To use `detailTemplate`, inject the `DetailRow` in the `provide` section.

{% tab template="grid/column/template" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" :detailTemplate ='detailTemplate' >
            <e-columns>
                <e-column field='EmployeeID' headerText='Employee ID' width='125' textAlign='Right'></e-column>
                <e-column field='FirstName' headerText='Name' width='120'></e-column>
                <e-column field='Title' headerText='Title' width='170'></e-column>
                <e-column field='HireDate' headerText='Hire Date' width='135' textAlign='Right' format='yMd'></e-column>
                <e-column field='ReportsTo' headerText='Reports To' width='120' textAlign='Right'></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, DetailRow } from "@syncfusion/ej2-vue-grids";
import { employeeData } from "./datasource.js";
import { Internationalization } from '@syncfusion/ej2-base';

let instance = new Internationalization();

Vue.use(GridPlugin);

export default {
  data: () => {
    return {
      data: employeeData,
      detailTemplate: function () {
        return { template : Vue.component('detailTemplate',{
        template: `
       <table class="detailtable" width="100%">
        <colgroup>
            <col width="35%">
            <col width="35%">
            <col width="30%">
        </colgroup>
        <tbody>
            <tr>
                <td rowspan="4" style="text-align: center;">
                    <img class='photo' :src="image" :alt="altImage" />
                </td>
                <td>
                    <span style="font-weight: 500;">First Name: </span> {{data.FirstName}}
                </td>
                <td>
                    <span style="font-weight: 500;">Postal Code: </span> {{data.PostalCode}}
                </td>
            </tr>
            <tr>
                <td>
                    <span style="font-weight: 500;">Last Name: </span> {{data.LastName}}
                </td>
                <td>
                    <span style="font-weight: 500;">City: </span> {{data.City}}
                </td>
            </tr>
            <tr>
                <td>
                    <span style="font-weight: 500;">Title: </span> {{data.Title}}
                </td>
                <td>
                    <span style="font-weight: 500;">Phone: </span> {{data.HomePhone}}
                </td>
            </tr>
            <tr>
                <td>
                    <span style="font-weight: 500;">Address: </span> {{data.Address}}
                </td>
                <td>
                    <span style="font-weight: 500;">HireDate: </span> {{format(data.HireDate)}}
                </td>
            </tr>
        </tbody>
    </table>`,
        data: function() {
            return {
              data: {}
            }
          },
        methods: {
            format: function(value) {
                return instance.formatDate(value, { skeleton: 'yMd', type: 'date' });
            }
          },
        computed: {
            image: function() {
              return './' + this.data.EmployeeID + '.png';
            },
            altImage: function() {
              return this.data.EmployeeID;
            }
          }
        })}
      }
    };
  },
  provide: {
      grid:[DetailRow]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
 .detailtable td {
        font-size: 13px;
        padding: 4px;
        max-width: 0;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
    }

    .photo {
        width: 100px;
        height: 100px;
        border-radius: 50px;
        box-shadow: inset 0 0 1px #e0e0e0, inset 0 0 14px rgba(0,0,0,0.2);
    }

    @media screen and (max-width: 800px) and (min-width: 320px) {
        .photo {
            width: 70px;
            height: 70px;
        }
    }
</style>
```

{% endraw %}

{% endtab %}

## See Also

* [How to pass data to DetailTemplate in Vue Grid](https://www.syncfusion.com/forums/153907/how-to-pass-data-to-detailtemplate-in-vue-grid)