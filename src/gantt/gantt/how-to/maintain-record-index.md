---
title: "How To"
component: "Gantt"
description: "Learn how to update record index while drag and drop on server side in Gantt control."
---

# Updating row drag and dropped index position on server side

Row dropped record’s index position can be maintained in the Gantt chart by changing the database table index position using the `rowDrop` event. In this event, the `fromIndex` and `dropIndex` values can be passed to the server side using Ajax request. On the server side, the `insert` and `insertAtTop` methods are used to update the row index position. The following code snippets explain the solution.

```typescript

<template>
     <div>
        <ejs-gantt :dataSource="data" :allowRowDragAndDrop='true' :taskFields = "taskFields" :height = "height"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, RowDD, Edit, Selection } from "@syncfusion/ej2-vue-gantt";
import { DataManager, UrlAdaptor } from '@syncfusion/ej2-data';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: new DataManager({
                url: 'https://localhost:44379/Home/UrlDatasource',
                adaptor: new UrlAdaptor,
                crossDomain: true,
                batchUrl: 'https://localhost:44379/Home/BatchUpdate'
            }),
            height: '450px',
            taskFields: {
                id: 'TaskID',
                name: 'TaskName',
                startDate: 'StartDate',
                duration: 'Duration',
                progress: 'Progress',
                dependency: 'Predecessor',
                child: 'subtasks'
            },
            rowDrop: function(args) {
                var record = this.flatData[args.fromIndex][this.taskFields.id];
                var record2 = this.flatData[args.dropIndex][this.taskFields.id];
                var data: IGanttData = args.data[0];
                var uri = 'https://localhost:44379/Home/RowDropMethod';
                var dragdropdata = {
                   record: data[0].taskData,
                   position: args.dropIndex,
                   dragidMapping: record,
                   dropidMapping: record2
                };
                var ajax = new Ajax(
                {
                  url: uri,
                  type: 'POST',
                  contentType: "application/json",
                  data: JSON.stringify(dragdropdata),
                });
                ajax.send();
            }
        };
    },
    provide: {
      gantt: [ RowDD, Edit, Selection ]
  }
};
</script>

```

```typescript

public IActionResult RowDropMethod([FromBody]DragDropData value)
        {
            var data = new CRUDModel();
            copyRecord = true;
            if (value.position == "bottomSegment" || value.position == "topSegment")
            {
                {
                    var childCount = 0;
                    int parent1 = (int)value.record.parentID;
                    childCount += FindChildRecords(parent1);
                    if (childCount == 1)
                    {
                        var i = 0;
                        for (; i < DataList.Count; i++)
                        {
                            if (DataList[i].taskID == parent1)
                            {
                                DataList[i].isParent = false;
                                break;
                            }
                            if (DataList[i].taskID == value.record.taskID)
                            {
                                DataList[i].parentID = null;
                                break;
                            }


                        }
                    }
                }
                DataList.Remove(DataList.Where(ds => ds.taskID == value.dragidMapping).FirstOrDefault());
                var j = 0;
                for (; j < DataList.Count; j++)
                {
                    if (DataList[j].taskID == value.dropidMapping)
                    {
                        value.record.parentID = DataList[j].parentID;
                        break;
                    }
                }

                data.Value = value.record;
                if (value.position == "bottomSegment")
                {
                    this.Insert(data, value.dropidMapping);
                }
                else if (value.position == "topSegment")
                {
                    this.InsertAtTop(data, value.dropidMapping);
                }
            }
            else if (value.position == "middleSegment")
            {
                DataList.Remove(DataList.Where(ds => ds.taskID == value.dragidMapping).FirstOrDefault());
                value.record.parentID = value.dropidMapping;
                FindDropdata(value.dropidMapping);
                data.Value = value.record;
                this.Insert(data, value.dropidMapping);
            }
            copyRecord = false;
            return Json(new { updatedRecords = value.record });
        }

```