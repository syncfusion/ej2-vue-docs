---
title: "Row"
component: "TreeGrid"
description: "Documentation for row customizations in TreeGrid."
---

# Row

The row represents record details fetched from data source.

## Customize rows

You can customize the appearance of a row by using the [`rowDataBound`](../api/treegrid/#rowdatabound) event.
The [`rowDataBound`](../api/treegrid/#rowdatabound) event triggers for every row. In the event handler, you can get the
`RowDataBoundEventArgs` that contains details of the row.

{% tab template="treegrid/row/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" :treeColumnIndex='1' childMapping='subtasks' height='315px' :rowDataBound='rowDataBound'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' textAlign='Right'  width='90'></e-column>
                <e-column field='taskName' headerText='Task Name' width='180'></e-column>
                <e-column field='startDate' headerText=' Start Date' textAlign='Right'  format='yMd' type='date' width='90'></e-column>
                <e-column field='duration' headerText='Duration' textAlign='Right'  width='80'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data () {
    return {
      data: sampleData,
    };
  },
  methods:{
     rowDataBound: function(args) {
         if (args.data['duration'] == 0 ) {
        args.row.style.background= '#336c12';
    } else if (args.data['duration'] < 3) {
        args.row.style.background= '#7b2b1d';
    }
    }
}
}
</script>

```

{% endtab %}

## Styling alternate rows

 You can change the treegrid's alternative rows' background color by overriding the `.e-altrow` class.

```css
.e-treegrid .e-altrow {
    background-color: #fafafa;
}
```

Please refer to the following example.

{% tab template="treegrid/row/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" :treeColumnIndex='1' childMapping='subtasks' height='315px'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' textAlign='Right'  width='90'></e-column>
                <e-column field='taskName' headerText='Task Name' width='180'></e-column>
                <e-column field='startDate' headerText=' Start Date' textAlign='Right'  format='yMd' type='date' width='90'></e-column>
                <e-column field='duration' headerText='Duration' textAlign='Right'  width='80'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data () {
    return {
      data: sampleData,
    };
  },
}
</script>
<style>
  .e-grid .e-altrow {
    background-color: #fafafa;
  }
</style>

```

{% endtab %}

## Row height

You can customize the row height of treegrid rows through the [`rowHeight`](../api/treegrid/#rowheight) property. The `rowHeight` property
is used to change the row height of entire treegrid rows.

In the below example, the `rowHeight` is set as '60px'.

{% tab template="treegrid/row/row" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" :treeColumnIndex='1' childMapping='subtasks' :enableHover='false' :allowSelection='false' height='275' rowHeight=60>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' textAlign='Right'  width='90'></e-column>
                <e-column field='taskName' headerText='Task Name' width='180'></e-column>
                <e-column field='startDate' headerText=' Start Date' textAlign='Right'  format='yMd' type='date' width='90'></e-column>
                <e-column field='duration' headerText='Duration' textAlign='Right'  width='80'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data () {
    return {
      data: sampleData,
    };
  },
}
</script>

```

{% endtab %}

### Customize row height for particular row

Grid row height for particular row can be customized using the [`rowDataBound`](../api/treegrid/#rowdatabound)
event by setting the `rowHeight` in arguments for each row based on the requirement.

In the below example, the row height for the row with Task ID as '3' is set as '90px' using the `rowDataBound` event.

{% tab template="treegrid/row/row" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" :treeColumnIndex='1' childMapping='subtasks' :rowDataBound='rowDataBound' height='275' >
            <e-columns>
                <e-column field='taskID' headerText='Task ID' textAlign='Right'  width='90'></e-column>
                <e-column field='taskName' headerText='Task Name' width='180'></e-column>
                <e-column field='startDate' headerText=' Start Date' textAlign='Right'  format='yMd' type='date' width='90'></e-column>
                <e-column field='duration' headerText='Duration' textAlign='Right'  width='80'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data () {
    return {
      data: sampleData,
    };
  },
  methods: {
   rowDataBound: function (args) {
     if((args.data as TasKDetails).taskID === 3){
        args.rowHeight = 90;
      }
    }
}
}
</script>

```

{% endtab %}

## Row template

The [`rowTemplate`](../api/treegrid/#rowtemplate) has an option to customise the look and behavior of the treegrid rows. The [`rowTemplate`](../api/treegrid/#rowtemplate) property accepts either the template string or HTML element ID.

{% tab template="treegrid/row/rowtemplate" %}

```html
<template>
<div id="app">
<ejs-treegrid :dataSource="data" childMapping='Children' height=275 :rowHeight = '83' width='auto' :treeColumnIndex='0' :rowTemplate='rowTemplate'>
            <e-columns>
                <e-column field='EmpID' headerText='Employee ID' width='180'></e-column>
                <e-column field='Name' headerText='Employee Name' width = '150'></e-column>
                <e-column field='Address' headerText = 'Employee Details' width='350'></e-column>
            </e-columns>
        </ejs-treegrid>
        </div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { textdata } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data: () => {
    return {
      data: textdata,
      rowTemplate: function () {
        return { template : Vue.component('rowTemplate',{
        template: `<tr>
    <td class="border" style='padding-left:18px;'>
        <div>{{data.EmpID}}</div>
                        </td>
                        <td class="border" style='padding: 10px 0px 0px 20px;'>
                            <div style="font-size:14px;">
                              {{data.Name}}
                                <p style="font-size:9px;">{{data.Designation}}</p>
                            </div>
                        </td>
                        <td class="border">
                            <div>
                                <div style="position:relative;display:inline-block;">
                                    <img :src="image" :alt="data.FullName" />
                                </div>
                                <div style="display:inline-block;">
                                    <div style="padding:5px;">{{data.Address}}</div>
                                    <div style="padding:5px;">{{data.Country}}</div>
                                    <div style="padding:5px;font-size:12px;">{{data.Contact}}</div>
                                </div>
                            </div>
                        </td>
                </tr>`,
                data: function() {
            return {
              data: {}
            }
          },
          computed: {
    image: function() {
      return '../../../../treegrid/images/' + this.data.FullName + '.png';
    }
  }
  })}
      }
    };
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-treegrid/styles/material.css";

  .border {
        border-color: #e0e0e0;
        border: 1px solid #e0e0e0;
        border-width: 1px 0px 0px 0px;
    }

    img {
        width: 60px;
        height: 60px;
        vertical-align: baseline;
        border-radius: 50px;
        margin-left: 20px;
        background-repeat: no-repeat;
    }
</style>

```

{% endtab %}

The [`rowTemplate`](../api/treegrid/#rowtemplate) property accepts only the TR element.

### Row template with formatting

If the [`rowTemplate`](../api/treegrid/#rowtemplate) is used, the value cannot be  formatted  inside the template using the [`columns.format`](../api/treegrid/column/#format) property. In that case, a function should be defined globally to format the value and invoke it inside the template.

{% tab template="treegrid/row/rowtemplateformat" %}

```html
<template>
<div id="app">
  <ejs-treegrid :dataSource="data" childMapping='Children' height=275 :rowHeight = '83' width='auto' :treeColumnIndex='0' :rowTemplate='rowTemplate'>
            <e-columns>
                <e-column field='EmpID' headerText='Employee ID' width='180'></e-column>
                <e-column field='Address' headerText = 'Employee Details' width='350'></e-column>
                <e-column field='DOB' headerText = 'DOB' width = '150'></e-column>
            </e-columns>
        </ejs-treegrid>
        </div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { textdata } from "./datasource.js";
import { Internationalization } from '@syncfusion/ej2-base';

let instance = new Internationalization();

Vue.use(TreeGridPlugin);

export default {
  data: () => {
    return {
      data: textdata,
      rowTemplate: function () {
        return { template : Vue.component('rowTemplate',{
        template: `<tr>
    <td class="border" style='padding-left:18px;'>
        <div>{{data.EmpID}}</div>
                        </td>
                        <td class="border">
                            <div>
                                <div style="position:relative;display:inline-block;">
                                    <img :src="image" :alt="data.FullName" />
                                </div>
                                <div style="display:inline-block;">
                                    <div style="padding:5px;">{{data.Address}}</div>
                                    <div style="padding:5px;">{{data.Country}}</div>
                                    <div style="padding:5px;font-size:12px;">{{data.Contact}}</div>
                                </div>
                            </div>
                        </td>
                        <td class="border" style='padding-left: 20px;'>
                            <div>{{format(data.DOB)}}</div>
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
      return '../../../../treegrid/images/' + this.data.FullName + '.png';
    }
  }
  })}
      }
    };
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-treegrid/styles/material.css";

  .border {
        border-color: #e0e0e0;
        border: 1px solid #e0e0e0;
        border-width: 1px 0px 0px 0px;
    }

    img {
        width: 60px;
        height: 60px;
        vertical-align: baseline;
        border-radius: 50px;
        margin-left: 20px;
        background-repeat: no-repeat;
    }
</style>

```

{% endtab %}

### Limitations

Row template feature is not compatible with all the features which are available in treegrid and it has limited features support. Here we have listed out the features which are compatible with row template feature.

* Filtering
* Paging
* Sorting
* Scrolling
* Searching
* Rtl
* Context Menu
* State Persistence

## Detail Template

The detail template provides additional information about a particular row. By expanding the parent row the child rows are expanded along with their detail template. The [`detailTemplate`](../api/treegrid/#detailtemplate) property accepts either the template string or HTML element ID.

{% tab template="treegrid/row/detailtemplate" %}

```html
<template>
<div id="app">
<ejs-treegrid :dataSource="data" childMapping='Children' height=317 width='auto' :treeColumnIndex='0' :detailTemplate='detailTemplate'>
    <e-columns>
      <e-column field='Name' headerText='First Name' width='180'></e-column>
      <e-column field='DOB' headerText = 'DOB' width='105' type='date' format='yMd'></e-column>
      <e-column field='Designation' headerText = 'Designation' width='180'></e-column>
      <e-column field='Country' headerText = 'Country' width='148'></e-column>
    </e-columns>
</ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, DetailRow } from "@syncfusion/ej2-vue-treegrid";
import { textdata } from "./datasource.js";
import { Internationalization } from '@syncfusion/ej2-base';

let instance = new Internationalization();

Vue.use(TreeGridPlugin);

export default {
  data: () => {
    return {
      data: textdata,
      detailTemplate: function () {
        return { template : Vue.component('detailTemplate',{
        template: `<div>
     <div style="position: relative; display: inline-block; float: left; font-weight: bold; width: 10%;padding:5px 4px 2px 27px;;">
        <img :src="image" alt="{{data.FullName}}"/>
    </div>
    <div style="padding-left: 10px; display: inline-block; width: 66%; text-wrap: normal;font-size:13px;font-family:'Segoe UI';">
        <div class="e-description" style="word-wrap: break-word;">
            <b>{{data.Name}}</b> was born on {{format(data.DOB)}}. Now lives at {{data.Address}}, {{data.Country}}. {{data.Name}} holds a position of <b>{{data.Designation}}</b> in our WA department, (Seattle USA).
        </div>
        <div class="e-description" style="word-wrap: break-word;margin-top:5px;">
            <b style="margin-right:10px;">Contact:</b>{{data.Contact}}
        </div>
    </div>
</div>`,
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
      return '../../../../treegrid/images/' + this.data.FullName + '.png';
    }
  }
  })}
      }
    };
  },
  provide: {
  treegrid: [DetailRow]
  }
}
</script>

```

{% endtab %}

## Drag and drop

The TreeGrid rows can be reordered, dropped to another TreeGrid or custom control by enabling the [`allowRowDragAndDrop`](../api/treegrid/#allowrowdraganddrop) to true.

To use row drag and drop, inject the `RowDD` module in the TreeGrid.

### Drag and drop within TreeGrid

The TreeGrid row drag and drop allows you to drag and drop TreeGrid rows on the same TreeGrid using drag icon. To enable row drag and drop, set the [`allowRowDragAndDrop`](../api/treegrid/#allowrowdraganddrop) to true. It provides the way to drop the row above, below or child to the target row with respective to the target row position.

{% tab template="treegrid/row/row" %}

```html
<template>
<div id="app">
        <ejs-treegrid id='TreeGrid' :dataSource="data" :allowRowDragAndDrop='true' height='315' :treeColumnIndex='1' :rowDropSettings='rowDrop'
         :selectionSettings='selectionSettings'
         childMapping='subtasks' >
            <e-columns>
                    <e-column field='taskID' headerText='Task ID' :isPrimaryKey='true' textAlign='Right' width=90></e-column>
                    <e-column field='taskName' headerText='Task Name' textAlign='Left' width=180></e-column>
                    <e-column field='startDate' headerText='Start Date' textAlign='Right' format='yMd' width=90></e-column>
                    <e-column field='duration' headerText='Duration' textAlign='Right' width=80></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, RowDD } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data () {
    return {
      data: sampleData,
      selectionSettings: { type: 'Multiple' },
      rowDrop: { targetID: 'destTree' }
    };
  },
    provide: {
    treegrid: [RowDD]
  }
}
</script>

```

{% endtab %}

> * Selection feature must be enabled for row drag and drop.
> * For multiple row selection, the [`type`](../api/treegrid/selectionSettings/#type) property must be set to `multiple`.

### Drag and drop to another TreeGrid

To drag and drop between two TreeGrid, enable the [`allowRowDragAndDrop`](../api/treegrid/#allowrowdraganddrop) property and specify the target TreeGrid ID in [`targetID`](../api/treegrid/rowDropSettings/#targetid) property of rowDropSettings.

{% tab template="treegrid/row/row" %}

```html
<template>
<div id="app">
<div style="display: inline-block">
        <ejs-treegrid id='TreeGrid' :dataSource="data" :allowRowDragAndDrop='true' height='315' :treeColumnIndex='1' :rowDropSettings='rowDrop' :selectionSettings='selectionSettings' childMapping='subtasks' >
            <e-columns>
                <e-column field="taskID" headerText="Task ID" width="120" isPrimaryKey="true"></e-column>
                <e-column field="taskName" headerText="Task Name" width="220"></e-column>
                <e-column field='startDate' headerText='Start Date' textAlign='Right' format='yMd' width=120></e-column>
                <e-column field="duration" headerText="Duration" width="90"></e-column></e-columns>
        </ejs-treegrid>
        <ejs-treegrid id='DestTree' :allowRowDragAndDrop='true' height='315' :treeColumnIndex='1' :rowDropSettings='rowDrops' :selectionSettings='selectionSettings' childMapping='subtasks' >
            <e-columns>
                <e-column field="taskID" headerText="Task ID" width="120" isPrimaryKey="true"></e-column>
                <e-column field="taskName" headerText="Task Name" width="220"></e-column>
                <e-column field='startDate' headerText='Start Date' textAlign='Right' format='yMd' width=120></e-column>
                <e-column field="duration" headerText="Duration" width="90"></e-column>
            </e-columns>
        </ejs-treegrid>
        </div>
</div>
</template>
<script>
    import Vue from "vue";
    import {TreeGridPlugin, RowDD, Selection} from "@syncfusion/ej2-vue-treegrid";
    import { sampleData } from "./datasource.js";

    Vue.use(TreeGridPlugin);

    export default {
        data() {
            return {
                data: sampleData,
                selectionSettings: { type: 'Multiple' },
                rowDrop: { targetID: 'TreeGrid' },
                rowDrops: { targetID: 'DestTree' }
            };
        },
        provide: {
            treegrid: [RowDD, Selection]
        }
    }
</script>
```

{% endtab %}

### Drag and drop events

The following events are triggered while drag and drop the treegrid rows.

[`rowDragStartHelper`](../api/treegrid/#rowdragstarthelper) - Triggers when click the drag icon or treegrid row and this event is used to customize the drag element based on user criteria.<br/>
[`rowDragStart`](../api/treegrid/#rowdragstart) -Triggers when starts to drag the treegrid row. <br/>
[`rowDrag`](../api/treegrid/#rowdrag) - Triggers while dragging the treegrid row. <br/>
[`rowDrop`](../api/treegrid/#rowdrop) - Triggers when a drag element is dropped on the target element. <br/>