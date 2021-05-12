---
title: "Data binding"
component: "TreeGrid"
description: "Learn how to bind local and remote data in the Essential JS 2 TreeGrid control."
---

# Data binding

The TreeGrid uses `DataManager`, which supports both RESTful JSON data services binding and local JavaScript object array binding. The [`dataSource`](../api/treegrid#dataSource) property can be assigned either with the instance of `DataManager` or JavaScript object array collection.
It supports two kinds of data binding method:
* Local data
* Remote data

## Local Data

In Local Data binding, data source for rendering the TreeGrid control is retrieved from the same application locally.

Two types of Data binding are possible with the TreeGrid control.

* Hierarchical Datasource binding
* Self-Referential Data binding (Flat Data)

To bind local data to the treegrid, you can assign a JavaScript object array to the [`dataSource`](../api/treegrid#datasource) property. The local data source can also be provided as an instance of the `DataManager`.

> By default, `DataManager` uses `JsonAdaptor` for local data-binding.

### Hierarchy data source binding

The [`childMapping`](../api/treegrid#childMapping) property is used to map the child records in hierarchy data source.

The following code example shows you how to bind the hierarchical local data into the TreeGrid control.

{% tab template="treegrid/data-binding/default", isDefaultActive=true %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width=70 textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width=200></e-column>
                <e-column field='startDate' headerText='Start Date' width=90 format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width=80 textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from './datasource.js';

Vue.use(TreeGridPlugin);

export default {
  data () {
    return {
      data: sampleData,
      pageSettings: { pageSize: 7 }
    };
  },
  provide: {
      treegrid: [ Page ]
    }
}
</script>

```

> * Remote data binding is not supported for Hierarchy Data.

{% endtab %}

### Self-Referential Data binding (Flat Data)

TreeGrid is rendered from Self-Referential data structures by providing two fields, ID field and parent ID field.

* **ID Field**: This field contains unique values used to identify nodes. Its name is assigned to the [`idMapping`](../api/treegrid#idMapping) property.
* **Parent ID Field**: This field contains values that indicate parent nodes. Its name is assigned to the [`parentIdMapping`](../api/treegrid#parentIdMapping) property.

{% tab template="treegrid/data-binding/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" idMapping='TaskID' parentIdMapping='parentID' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings'>
            <e-columns>
                <e-column field='TaskID' headerText='Task ID' width=90 textAlign='Right'></e-column>
                <e-column field='TaskName' headerText='Task Name' width=180></e-column>
                <e-column field='StartDate' headerText='Start Date' width=90 format="yMd" textAlign='Right'></e-column>
                <e-column field='Duration' headerText='Duration' width=80 textAlign='Right'></e-column>
                </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page } from "@syncfusion/ej2-vue-treegrid";
import { projectData } from './datasource.js';

Vue.use(TreeGridPlugin);

export default {
  data () {
    return {
      data: projectData,
      pageSettings: { pageSize: 7 }
    };
  },
  provide: {
      treegrid: [ Page ]
    },
}
</script>
```

{% endtab %}

> Herewith we have provided list of reserved properties and the purpose used in TreeGrid. We recommend to avoid these reserved properties for Internal purpose(To get rid of conflicts).

Reserved keywords | Purpose
-----|-----
childRecords | Specifies the childRecords of a parentData
hasChildRecords | Specifies whether the record contains child records
hasFilteredChildRecords | Specifies whether the record contains filtered child records
expanded | Specifies whether the child records are expanded
parentItem | Specifies the parentItem of childRecords
index | Specifies the index of current record
level | Specifies the hierarchy level of record
filterLevel | Specifies the hierarchy level of filtered record
parentIdMapping | Specifies the parentID
uniqueID | Specifies the unique ID of a record
parentUniqueID | Specifies the parent Unique ID of a record
checkboxState | Specifies the checkbox state of a record
isSummaryRow | Specifies the summary of a record
taskData | Specifies the main data
primaryParent | Specifies the Primary data

## Remote data

To bind remote data to TreeGrid component, assign service data as an instance of `DataManager` to the [`dataSource`](../api/treegrid#datasource) property. To interact with remote data source,  provide the endpoint `url` and define the [`hasChildMapping`](../api/treegrid#hasChildMapping) property of treegrid.

The [`hasChildMapping`](../api/treegrid/#haschildmapping) property maps the field name in data source, that denotes whether current record holds any child records. This is useful internally to show expand icon while binding child data on demand.

The TreeGrid provides `Load on Demand` support for rendering remote data. The Load on demand is considered in TreeGrid for the following actions.

* Expanding root nodes.
* Navigating pages, with paging enabled in TreeGrid.

When load on demand is enabled, all the root nodes are rendered in collapsed state at initial load.

When load on demand support is enabled in TreeGrid with paging, the current or active page’s root node alone will be rendered in collapsed state. On expanding the root node, the child nodes will be loaded from the remote server.

When a root node is expanded, its child nodes are rendered and are cached locally, such that on consecutive expand/collapse actions on root node, the child nodes are loaded from the cache instead from the remote server.

Similarly, if the user navigates to a new page, the root nodes of that specific page, will be rendered with request to the remote server.

>Remote Data Binding supports only Self-Referential Data and by default the `pageSizeMode` for Remote Data is `Root` mode. i.e only root node’s count will be shown in pager while using Remote Data

{% tab template="treegrid/data-binding/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" idMapping='TaskID' parentIdMapping='ParentID' :treeColumnIndex='1' :allowPaging='true'>
            <e-columns>
                <e-column field='TaskID' headerText='Task ID' width=90 textAlign='Right'></e-column>
                <e-column field='TaskName' headerText='Task Name' width=180></e-column>
                <e-column field='StartDate' headerText='Start Date' width=90 format="yMd" textAlign='Right'></e-column>
                <e-column field='Duration' headerText='Duration' width=80 textAlign='Right'></e-column>
                </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page } from "@syncfusion/ej2-vue-treegrid";
import { DataManager, WebApiAdaptor } from "@syncfusion/ej2-data";

Vue.use(TreeGridPlugin);

export default {
   data() {
    let SERVICE_URI ="https://ej2services.syncfusion.com/production/web-services/api/SelfReferenceData";
    return {
      data: new DataManager({
        url: SERVICE_URI,
        adaptor: new WebApiAdaptor(),
        crossDomain: true
      })
    };
  }
  provide: {
      treegrid: [ Page ]
    },
}
</script>
```

{% endtab %}

> By default, `DataManager` uses `ODataAdaptor` for remote data-binding.
> Based on the RESTful web services, set the corresponding adaptor to DataManager. Refer [`here`](https://ej2.syncfusion.com/documentation/data/adaptors/?no-cache=1) for more details.
> Filtering and searching server-side data operations are not supported in load on demand

### LoadChildOnDemand

While binding remote data to Tree Grid component, by default Tree Grid renders parent rows in collapsed state. Tree Grid provides option to load the child records also during the initial rendering itself for remote data binding by setting [`loadChildOnDemand`](https://ej2.syncfusion.com/vue/documentation/api/treegrid/#loadchildondemand) as true.

When [`loadChildOnDemand`](https://ej2.syncfusion.com/vue/documentation/api/treegrid/#loadchildondemand) is enabled parent records are rendered in expanded state.

The following code example describes the behavior of the loadChildOnDemand feature of Tree Grid.

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' idMapping='TaskID' parentIdMapping='parentID' :treeColumnIndex='1' :allowPaging='true' :loadChildOnDemand='true' height='270px'>
        <e-columns>
        <e-column field='TaskID'  :isPrimaryKey='true'  headerText='Task ID'  width=90 textAlign='Right'></e-column>
        <e-column field='TaskName' headerText='Task Name' width=180></e-column>
        <e-column field='StartDate' headerText='Start Date' editType= 'datepickeredit' type= 'date' format= 'yMd' textAlign='Right' width=170></e-column>
        <e-column field='EndDate' headerText='End Date' editType= 'datepickeredit' type= 'date' format= 'yMd' textAlign='Right' width=170></e-column>
        <e-column field='Priority' headerText='Priority' width=110></e-column>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page } from "@syncfusion/ej2-vue-treegrid";
import { DataManager, UrlAdaptor } from '@syncfusion/ej2-data';

Vue.use(TreeGridPlugin);


export default {
  data() {
    return {
      data: new DataManager({
        url: "Home/DataSource",
        updateUrl: "Home/Update",
        insertUrl: "Home/Insert",
        removeUrl: "Home/Delete",
        batchUrl: "Home/Remove",
        adaptor: new UrlAdaptor
      })
    };
  },
    provide: {
    treegrid: [ Page ]
  }
}

</script>

```

>Also while using **loadChildOnDemand** we need to handle the child records on server end and it is applicable to CRUD operations also.

The following code example describes handling of child records at server end.

```typescript

public ActionResult UrlDatasource(DataManagerRequest dm)
{
    if (TreeData.tree.Count == 0)
          TreeData.GetTree();
    IEnumerable DataSource = TreeData.tree;

    DataOperations operation = new DataOperations();
    if (dm.Where != null && dm.Where.Count > 0)
    {
        DataSource = operation.PerformFiltering(DataSource, dm.Where, "and");  //perform filtering
    }
    if (dm.Sorted != null && dm.Sorted.Count > 0)
    {
        DataSource = operation.PerformSorting(DataSource, dm.Sorted);  //perform sorting
    }
    var count = DataSource.ToList<TreeData>().Count();
    if (dm.Skip != 0)
    {
        DataSource = operation.PerformSkip(DataSource, dm.Skip);   //Paging
    }
    if (dm.Take != 0)
    {
        DataSource = operation.PerformTake(DataSource, dm.Take);
    }
    if (dm.Where != null)
    {  
        DataSource = CollectChildRecords(DataSource, dm);    // method to collect child records
    }

    return dm.RequiresCounts ? Json(new { result = DataSource, count = count }) : Json(DataSource);
}

 public IEnumerable CollectChildRecords(IEnumerable datasource, DataManagerRequest dm)
 {
     DataOperations operation = new DataOperations();
     IEnumerable DataSource = TreeData.tree;     // use the total DataSource here
     string IdMapping = "TaskID";     // define your IdMapping field name here
     int[] TaskIds = new int[0];
     foreach (var rec in datasource)
     {
        int taskid = (int)rec.GetType().GetProperty(IdMapping).GetValue(rec);
        TaskIds = TaskIds.Concat(new int[] { taskid }).ToArray();   //get the Parentrecord Ids based on IdMapping Field  
     }
    IEnumerable ChildRecords = null;
     foreach (int id in TaskIds)
     {
        dm.Where[0].value = id;
        IEnumerable records = operation.PerformFiltering(DataSource, dm.Where, dm.Where[0].Operator);   //perform filtering to collect the childrecords based on Ids
        ChildRecords = ChildRecords == null || (ChildRecords.AsQueryable().Count() == 0) ? records : ((IEnumerable<object>)ChildRecords).Concat((IEnumerable<object>)records);  //concate the childrecords with dataSource  
     }
     if (ChildRecords != null)
     {
        ChildRecords = CollectChildRecords(ChildRecords, dm);     // repeat the operation for inner level child
        if (dm.Sorted != null && dm.Sorted.Count > 0) // perform Sorting
        {
            ChildRecords = operation.PerformSorting(ChildRecords, dm.Sorted);
        }
        datasource = ((IEnumerable<object>)datasource).Concat((IEnumerable<object>)ChildRecords);    //concate the childrecords with dataSource  
     }
    return datasource;
 }

```

### Offline Mode

On remote data binding, all treegrid actions such as paging, loading child on-demand, will be processed on server-side. To avoid postback, set the treegrid to load all data on initialization and make the actions process in client-side. To enable this behavior, use the `offline` property of `DataManager`.

{% tab template="treegrid/data-binding/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" idMapping='TaskID' parentIdMapping='ParentItem' hasChildMapping='isParent' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings'>
            <e-columns>
                <e-column field='TaskID' headerText='Task ID' width=90 textAlign='Right'></e-column>
                <e-column field='TaskName' headerText='Task Name' width=180></e-column>
                <e-column field='StartDate' headerText='Start Date' width=90 format="yMd" textAlign='Right'></e-column>
                <e-column field='Duration' headerText='Duration' width=80 textAlign='Right'></e-column>
                </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page } from "@syncfusion/ej2-vue-treegrid";
import { DataManager, WebApiAdaptor } from "@syncfusion/ej2-data";

Vue.use(TreeGridPlugin);

export default {
  data () {
      let SERVICE_URI: string =
      "https://ej2services.syncfusion.com/production/web-services/api/SelfReferenceData";
    return {
      data: new DataManager({
        url: SERVICE_URI,
        adaptor: new WebApiAdaptor(),
        offline: true
      }),
      pageSettings: { pageCount: 4 }
    };
  },
  provide: {
      treegrid: [ Page ]
    },
}
</script>

```

{% endtab %}

### Custom Adaptor

You can create your own adaptor by extending the built-in adaptors. The following demonstrates custom adaptor approach and how to add a serial number for the records by overriding the built-in response processing using the `processResponse` method of the `WebApiAdaptor`.

{% tab template="treegrid/data-binding/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" idMapping='TaskID' parentIdMapping='ParentItem' hasChildMapping='isParent' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings'>
            <e-columns>
                <e-column field='Sno' headerText='SNO' width='90' textAlign='Right'></e-column>
                <e-column field='TaskName' headerText='Task Name' width='180'></e-column>
                <e-column field='StartDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='Duration' headerText='Duration' width='80' textAlign='Right'></e-column>
                </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page } from "@syncfusion/ej2-vue-treegrid";
import { DataManager, WebApiAdaptor } from "@syncfusion/ej2-data";

Vue.use(TreeGridPlugin);

class SerialNoAdaptor extends WebApiAdaptor {
    public processResponse(): Object[] {
        let i: number = 0;
        // calling base class processResponse function
        let original: Object[] = super.processResponse.apply(this, arguments);
        // adding serial number
        original.forEach((item: Object) => item['Sno'] = ++i);
        return original;
    }
}

export default {
  data () {
      let SERVICE_URI: string =
      "https://ej2services.syncfusion.com/production/web-services/api/SelfReferenceData";
    return {
      data: new DataManager({
        url: SERVICE_URI,
        adaptor: new SerialNoAdaptor(),
        offline: true
      }),
      pageSettings: { pageCount: 4 }
    };
  },
  provide: {
      treegrid: [ Page ]
    },
}
</script>

```

{% endtab %}

### Sending additional parameters to the server

To add a custom parameter to the data request, use the `addParams` method of `Query` class. Assign the `Query` object with additional parameters to the treegrid [`query`](../api/treegrid#query) property.

{% tab template="treegrid/data-binding/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" idMapping='TaskID' parentIdMapping='ParentItem' :query='query' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings'>
            <e-columns>
                <e-column field='TaskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='TaskName' headerText='Task Name' width='180'></e-column>
                <e-column field='StartDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='Duration' headerText='Duration' width='80' textAlign='Right'></e-column>
                </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page } from "@syncfusion/ej2-vue-treegrid";
import { DataManager, WebApiAdaptor , Query } from "@syncfusion/ej2-data";

Vue.use(TreeGridPlugin);

export default {
  data () {
      let SERVICE_URI: string =
      "https://ej2services.syncfusion.com/production/web-services/api/SelfReferenceData";
    return {
      data: new DataManager({
        url: SERVICE_URI,
        adaptor: new WebApiAdaptor(),
      }),
      pageSettings: { pageCount: 4 }
      query: new Query().addParams('ej2treegrid', 'true');
    };
  },
  provide: {
      treegrid: [ Page ]
    },
}
</script>

```

{% endtab %}

### Handling HTTP error

During server interaction from the treegrid, some server-side exceptions may occur, and you can acquire those error messages or exception details
in client-side using the [`actionFailure`](../api/treegrid#actionfailure) event.

The argument passed to the [`actionFailure`](../api/treegrid#actionfailure) event contains the error details returned from the server.

{% tab template="treegrid/data-binding/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid ref=treegrid :dataSource="data" idMapping='TaskID' parentIdMapping='parentItem':treeColumnIndex='1' :actionFailure='actionFailure'>
            <e-columns>
                <e-column field='TaskID' headerText='Task ID' width=90 textAlign='Right'></e-column>
                <e-column field='TaskName' headerText='Task Name' width=180></e-column>
                <e-column field='StartDate' headerText='Start Date' width=90 format="yMd" textAlign='Right'></e-column>
                <e-column field='Duration' headerText='Duration' width=80 textAlign='Right'></e-column>
                </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page } from "@syncfusion/ej2-vue-treegrid";
import { DataManager, WebApiAdaptor } from "@syncfusion/ej2-data";

Vue.use(TreeGridPlugin);

export default {
  data () {
      let SERVICE_URI: string =
      "http://some.com/invalidUrl";
    return {
      data: new DataManager({
        url: SERVICE_URI,
        adaptor: new WebApiAdaptor(),
        offline: true
      }),
      pageSettings: { pageCount: 4 }
    };
  },
  provide: {
      treegrid: [ Page ]
    },
   methods:{
       actionFailure: function() {
       let span = document.createElement('span');
       let treegrid = document.getElementsByClassName("e-treegrid")[0].ej2_instances[0];
       treegrid.element.parentNode.insertBefore(span, treegrid.element);
       span.style.color = '#FF0000'
       span.innerHTML = 'Server exception: 404 Not found';
    }
  }
}
</script>

```

{% endtab %}

> The [`actionFailure`](../api/treegrid#actionfailure) event will be triggered not only for the server errors, but
also when there is an exception while processing the treegrid actions.

## Binding with Ajax

You can use TreeGrid [`dataSource`](../api/treegrid#datasource) property to bind the data source to TreeGrid from external Ajax request. In the below code we have fetched the data source from the server with the help of Ajax request and provided that to [`dataSource`](../api/treegrid#datasource) property by using `onSuccess` event of the Ajax.

{% tab template="treegrid/data-binding/default" %}

```html
<template>
  <div id="app">
    <ejs-button v-on:click.native="btnClick">Bind Data</ejs-button>
        <ejs-treegrid ref=treegrid :dataSource="data" idMapping='TaskID' parentIdMapping='ParentItem'  :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings'>
            <e-columns>
                <e-column field='TaskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='TaskName' headerText='Task Name' width='100'></e-column>
                <e-column field='Duration' headerText='Duration' width='80' textAlign='Right'></e-column>
                </e-columns>
                <e-column field='Progress' headerText='Progress' width='80' textAlign='Right'></e-column>
                </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page } from "@syncfusion/ej2-vue-treegrid";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { Ajax } from '@syncfusion/ej2-base';

Vue.use(TreeGridPlugin);
Vue.use(ButtonPlugin);

export default {
  data () {
    return {
      data: {},
      pageSettings: { pageCount: 4 }
    };
  },
  provide: {
      treegrid: [ Page ]
    },
   methods:{
         btnClick: function (args){
        let treegrid = document.getElementsByClassName("e-treegrid")[0].ej2_instances[0]; // TreeGrid instance
        let ajax = new Ajax ("https://ej2services.syncfusion.com/production/web-services/api/SelfReferenceData", "GET");treegrid.showSpinner();
        ajax.send();
        ajax.onSuccess = function (result) {
        treegrid.hideSpinner();
        treegrid.dataSource = JSON.parse(result);
        };
      }
  }
}
</script>

```

{% endtab %}

> * If you bind the dataSource from this way, then it acts like a local dataSource. So you cannot perform any server side crud actions.