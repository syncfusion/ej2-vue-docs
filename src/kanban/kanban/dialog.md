---
title: "Add, Edit and Remove (CRUD) a Card in Kanban"
component: "Kanban"
description: "This section explains how to add, edit, and remove a card using built-in dialog, custom fields, and template in a Kanban."
---

# Card Editing

The Kanban provides built-in support to add, edit and delete a card using dialog module. User can edit a card using the following ways.

* Built-in dialog module
* Custom Fields
* Dialog template

## Default Dialog

When double-click on the cards, the dialog is opened with below fields to edit a card. This dialog contains `Delete`, `Save` and `Cancel` buttons.

* To edit a card, modify the card details and click the `Save` button.
* To delete a card, click `Delete` button.
* Click on the `Cancel` button to cancel the editing action.

The dialog displays with the following fields which mapped to dialog fields by default.

Key | Type | Text
-----|-----|----
cardSettings.headerField | Input | ID
keyField | DropDown | -
cardSettings.contentField | TextArea | -
cardSettings.priority(If applicable) | Numeric | -
swimlaneSettings.keyField(If applicable) | DropDown | -

{% tab template="kanban/getting-started-key-field", iframeHeight="588px" %}

```html
<template>
  <div id="app">
       <ejs-kanban id="kanban" keyField="Status" :dataSource="kanbanData"
        :cardSettings="cardSettings">
          <e-columns>
            <e-column headerText="To Do" keyField="Open"></e-column>
            <e-column headerText="In Progress" keyField="InProgress"></e-column>
            <e-column headerText="Testing" keyField="Testing"></e-column>
            <e-column headerText="Done" keyField="Close"></e-column>
          </e-columns>
        </ejs-kanban>
  </div>
</template>

<script>
import Vue from "vue";
import { KanbanPlugin } from '@syncfusion/ej2-vue-kanban';
import { extend } from '@syncfusion/ej2-base';
import { kanbanData } from './datasource.js';
Vue.use(KanbanPlugin);
export default {
  data: function() {
    return {
      kanbanData: extend([], kanbanData, null, true),
      cardSettings: {
        contentField: "Summary",
        headerField: "Id",
      }
    };
  },
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-layouts/styles/material.css';
@import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-vue-kanban/styles/material.css';
</style>

```

{% endtab %}

## Custom Fields

You can change the default fields of dialog using `fields` property inside the `dialogSettings` property. The `key` property used to map the dataSource value and rendered the corresponding component based on specified `type` property.

The following types are available in dialog fields.

* String
* Numeric
* TextArea
* DropDown
* TextBox
* Input

> If `type` is not defined in the fields, then it renders as the HTML input element in dialog.

{% tab template="kanban/custom-dialog", iframeHeight="588px" %}

```html
<template>
  <div id="app">
       <ejs-kanban id="kanban" keyField="Status" :dataSource="kanbanData"
        :cardSettings="cardSettings" :dialogSettings="dialogSettings">
          <e-columns>
            <e-column headerText="To Do" keyField="Open"></e-column>
            <e-column headerText="In Progress" keyField="InProgress"></e-column>
            <e-column headerText="Testing" keyField="Testing"></e-column>
            <e-column headerText="Done" keyField="Close"></e-column>
          </e-columns>
        </ejs-kanban>
  </div>
</template>

<script>
import Vue from "vue";
import { KanbanPlugin } from '@syncfusion/ej2-vue-kanban';
import { extend } from '@syncfusion/ej2-base';
import { kanbanData } from './datasource.js';
Vue.use(KanbanPlugin);
export default {
  data: function() {
    return {
      kanbanData: extend([], kanbanData, null, true),
      cardSettings: {
        contentField: "Summary",
        headerField: "Id",
      },
      dialogSettings: {
        fields: [
                { text: 'ID', key: 'Id', type: 'Input' },
                { key: 'Category', type: 'DropDown' },
                { key: 'Title', type: 'Input' },
                { key: 'Size', type: 'Input' },
                { key: 'Description', type: 'TextArea' }
            ]
        }
    };
  },
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-layouts/styles/material.css';
@import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-vue-kanban/styles/material.css';
</style>

```

{% endtab %}

### Custom Fields label

By default, the fields `key` mapping value is considered as a `label` and you can change this label by using `text` property.

{% tab template="kanban/label", iframeHeight="588px" %}

```html
<template>
  <div id="app">
       <ejs-kanban id="kanban" keyField="Status" :dataSource="kanbanData"
        :cardSettings="cardSettings" :dialogSettings="dialogSettings">
          <e-columns>
            <e-column headerText="To Do" keyField="Open"></e-column>
            <e-column headerText="In Progress" keyField="InProgress"></e-column>
            <e-column headerText="Testing" keyField="Testing"></e-column>
            <e-column headerText="Done" keyField="Close"></e-column>
          </e-columns>
        </ejs-kanban>
  </div>
</template>

<script>
import Vue from "vue";
import { KanbanPlugin } from '@syncfusion/ej2-vue-kanban';
import { extend } from '@syncfusion/ej2-base';
import { kanbanData } from './datasource.js';
Vue.use(KanbanPlugin);
export default {
  data: function() {
    return {
      kanbanData: extend([], kanbanData, null, true),
      cardSettings: {
        contentField: "Summary",
        headerField: "Id",
      },
      dialogSettings: {
        fields: [
            { text: 'ID', key: 'Id', type: 'Input' },
            { key: 'Status', type: 'DropDown' },
            { key: 'Estimate', type: 'Numeric' },
            { key: 'Summary', type: 'TextArea' }
        ]
      }
    };
  },
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-layouts/styles/material.css';
@import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-vue-kanban/styles/material.css';
</style>

```

{% endtab %}

### Fields Validation

The dialog fields can be validated while click on the `Save` button. This can be achieved by using `validationRules` property.

{% tab template="kanban/fields-validation", iframeHeight="588px" %}

```html
<template>
  <div id="app">
       <ejs-kanban id="kanban" keyField="Status" :dataSource="kanbanData"
        :cardSettings="cardSettings" :dialogSettings="dialogSettings">
          <e-columns>
            <e-column headerText="To Do" keyField="Open"></e-column>
            <e-column headerText="In Progress" keyField="InProgress"></e-column>
            <e-column headerText="Testing" keyField="Testing"></e-column>
            <e-column headerText="Done" keyField="Close"></e-column>
          </e-columns>
        </ejs-kanban>
  </div>
</template>

<script>
import Vue from "vue";
import { KanbanPlugin } from '@syncfusion/ej2-vue-kanban';
import { extend } from '@syncfusion/ej2-base';
import { kanbanData } from './datasource.js';
Vue.use(KanbanPlugin);
export default {
  data: function() {
    return {
      kanbanData: extend([], kanbanData, null, true),
      cardSettings: {
        contentField: "Summary",
        headerField: "Id",
      },
      dialogSettings: {
        fields: [
            { text: 'ID', key: 'Id', type: 'Input' },
            { key: 'Status', type: 'DropDown' },
            { key: 'Estimate', type: 'Numeric', validationRules: { range: [0, 1000] } },
            { key: 'Summary', type: 'TextArea', validationRules: { required: true } }
        ]
      }
    };
  },
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-layouts/styles/material.css';
@import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-vue-kanban/styles/material.css';
</style>

```

{% endtab %}

## Dialog Template

Using the dialog template, you can render your own dialog by defining the `template` property. Initialize the template as SCRIPT element Id or HTML string which holds the template and map it to the template property.

{% tab template="kanban/dialog-template", iframeHeight="588px" %}

```html
<template>
  <div id="app">
       <ejs-kanban id="kanban" keyField="Status" :dataSource="kanbanData"
        :cardSettings="cardSettings" :dialogSettings="dialogSettings">
          <e-columns>
            <e-column headerText="To Do" keyField="Open"></e-column>
            <e-column headerText="In Progress" keyField="InProgress"></e-column>
            <e-column headerText="Testing" keyField="Testing"></e-column>
            <e-column headerText="Done" keyField="Close"></e-column>
          </e-columns>
        </ejs-kanban>
  </div>
</template>

<script>
import Vue from "vue";
import { KanbanPlugin } from '@syncfusion/ej2-vue-kanban';
import { extend } from '@syncfusion/ej2-base';
import { kanbanData } from './datasource.js';
Vue.use(KanbanPlugin);

var ContentTemplate = Vue.component("dialogTemplate", {
  template: `<div>
<table>
        <tbody>
            <tr>
                <td class="e-label">ID</td>
                <td>
                  <div class="e-float-input e-control-wrapper">
                    <input id="Id" name="Id" type="text" class="e-field" v-model='data.Id' disabled />
                  </div>
                </td>
            </tr>
            <tr>
                <td class="e-label">Status</td>
                <td>
                  <ejs-dropdownlist id="Status" name="Status" class="e-field" v-model='data.Status' :dataSource="dataSource1" placeholder="Status"></ejs-dropdownlist>
                </td>
            </tr>
            <tr>
                <td class="e-label">Assignee</td>
                <td>
                  <ejs-dropdownlist id="Assignee" name="Assignee" v-model='data.Assignee' class="e-field" :dataSource="dataSource2" placeholder="Assignee"></ejs-dropdownlist>
                </td>
            </tr>
            <tr>
                <td class="e-label">Priority</td>
                <td>
                  <ejs-dropdownlist type="text" name="Priority" id="Priority" v-model='data.Priority' popupHeight="300px" class="e-field" placeholder="Priority" :dataSource="dataSource3"></ejs-dropdownlist>
                </td>
            </tr>
            <tr>
                <td class="e-label">Summary</td>
                <td>
                  <div class="e-float-input e-control-wrapper">
                    <textarea type="text" name="Summary" id="Summary" class="e-field" v-model='data.Summary'></textarea>
                  </div>
                </td>
            </tr>
        </tbody>
    </table>
    </div>`,
  data() {
    var statusData = [
      { text: "Open" },
      { text: "InProgress" },
      { text: "Testing" },
      { text: "Close" }
    ];
    var priorityData = ["Low", "Normal", "Critical", "Release Breaker", "High"];
    var assigneeData = [
      "Nancy Davloio",
      "Andrew Fuller",
      "Janet Leverling",
      "Steven walker",
      "Robert King",
      "Margaret hamilt",
      "Michael Suyama"
    ];
    return {
      dataSource1: statusData,
      dataSource2: assigneeData,
      dataSource3: priorityData,
      data: {}
    };
  }
});

export default {
  data: function() {
    return {
      kanbanData: extend([], kanbanData, null, true),
      cardSettings: {
        contentField: "Summary",
        headerField: "Id",
      },
      dialogSettings: {
        template: function() {
          return { template: ContentTemplate };
        }
      }
    };
  },
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-layouts/styles/material.css';
@import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-vue-kanban/styles/material.css';
</style>

```

{% endtab %}

## Prevent Dialog

The Kanban allows to prevent to open a dialog on card double-click by enabling `args.cancel` in `dialogOpen` event.

{% tab template="kanban/prevent-dialog", iframeHeight="588px" %}

```html
<template>
  <div id="app">
       <ejs-kanban id="kanban" keyField="Status" :dataSource="kanbanData"
        :cardSettings="cardSettings" :dialogOpen="dialogOpen">
          <e-columns>
            <e-column headerText="To Do" keyField="Open"></e-column>
            <e-column headerText="In Progress" keyField="InProgress"></e-column>
            <e-column headerText="Testing" keyField="Testing"></e-column>
            <e-column headerText="Done" keyField="Close"></e-column>
          </e-columns>
        </ejs-kanban>
  </div>
</template>

<script>
import Vue from "vue";
import { KanbanPlugin } from '@syncfusion/ej2-vue-kanban';
import { extend } from '@syncfusion/ej2-base';
import { kanbanData } from './datasource.js';
Vue.use(KanbanPlugin);
export default {
  data: function() {
    return {
      kanbanData: extend([], kanbanData, null, true),
      cardSettings: {
        contentField: "Summary",
        headerField: "Id",
      },
      dialogOpen: function (args) {
        args.cancel = true;
      }
    };
  },
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-layouts/styles/material.css';
@import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-vue-kanban/styles/material.css';
</style>

```

{% endtab %}

## Persisting data in server

The modified card data can be persisted in the database using the RESTful web services. All the CRUD operations in the Kanban are done through [`DataManager`](../data). The `DataManager` has an option to bind all the CRUD related data in server-side.

> For your information, the ODataAdaptor persists data in the server as per OData protocol.

In the below section covers how to get the edited data details on the server-side using the [`UrlAdaptor`](../../data/adaptors.html#url-adaptor).

### URL adaptor

You can use the [`UrlAdaptor`](../../data/adaptors.html#url-adaptor) of `DataManager` when binding data source for remote data. In the initial load of Kanban, data are fetched from remote data and bound to the Kanban using `url` property of `DataManager`.

Using the `crudUrl` property, the controller action URL can be specified to perform all the CRUD operations at server-side using a single method instead of specifying separate controller action method for CRUD (create, update and delete) operations. The action parameter of `crudUrl` is used to get the corresponding CRUD action.

The following code example describes the above behaviour.

```typescript
<template>
  <div id="app">
       <ejs-kanban id="kanban" keyField="Status" :dataSource="kanbanData"
        :cardSettings="cardSettings">
          <e-columns>
            <e-column headerText="To Do" keyField="Open"></e-column>
            <e-column headerText="In Progress" keyField="InProgress"></e-column>
            <e-column headerText="Testing" keyField="Testing"></e-column>
            <e-column headerText="Done" keyField="Close"></e-column>
          </e-columns>
        </ejs-kanban>
  </div>
</template>

<script>
import Vue from "vue";
import { KanbanPlugin } from '@syncfusion/ej2-vue-kanban';
import { DataManager, UrlAdaptor } from "@syncfusion/ej2-data";
Vue.use(KanbanPlugin);
export default {
  data: function() {
    return {
        kanbanData: new DataManager({
            url: "DataSource",
            crudUrl: "UpdateData",
            adaptor: new UrlAdaptor
        });
        cardSettings: {
            contentField: "Summary",
            headerField: "Id",
        }
    };
  }
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-layouts/styles/material.css';
@import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-vue-kanban/styles/material.css';
</style>
```

The server-side controller code to handle the CRUD operations are as follows.

```typescript

private NORTHWNDEntities db = new NORTHWNDEntities();
public ActionResult DataSource() {
    var DataSource = db.Tasks.ToList();
    return Json(DataSource, JsonRequestBehavior.AllowGet);
}
public ActionResult UpdateData(EditParams param) {
    if (param.action == "insert" || (param.action == "batch" && param.added != null)) {
        if (param.action == "insert") {
            db.Tasks.Add(param.value);
        } else {
            foreach (var temp in param.added) {
                db.Tasks.Add(temp);
            }
        }
    }
    if (param.action == "update" || (param.action == "batch" && param.changed != null)) {
        if (param.action == "update") {
            Task old = db.Tasks.Where(o => o.Id == param.value.Id).SingleOrDefault();
            if (old != null) {
                db.Entry(old).CurrentValues.SetValues(param.value);
            }
        } else {
            foreach (var temp in param.changed) {
                Task old = db.Tasks.Where(o => o.Id == temp.Id).SingleOrDefault();
                if (old != null) {
                    db.Entry(old).CurrentValues.SetValues(temp);
                }
            }
        }
    }
    if (param.action == "remove" || (param.action == "batch" && param.deleted != null)) {
        if (param.action == "remove") {
            int key = Convert.ToInt32(param.key);
            db.Tasks.Remove(db.Tasks.Where(o => o.Id == key).SingleOrDefault());
        } else {
            foreach (var temp in param.deleted) {
                db.Tasks.Remove(db.Tasks.Where(o => o.Id == temp.Id).SingleOrDefault());
            }
        }
    }
    db.SaveChanges();
    var data = db.Tasks.ToList();
    return Json(data, JsonRequestBehavior.AllowGet);
}

public class EditParams {
    public string key { get; set; }
    public string action { get; set; }
    public List<Tasks> added { get; set; }
    public List<Tasks> changed { get; set; }
    public List<Tasks> deleted { get; set; }
    public Tasks value { get; set; }
}

```
