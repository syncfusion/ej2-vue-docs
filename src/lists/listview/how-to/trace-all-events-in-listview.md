# Trace all events in ListView

The ListView component triggers events based on its actions. The events can be used as extension points to perform custom operations. Refer to the following steps to trace the ListView events:

1. Render the ListView with [dataSource](https://ej2.syncfusion.com/vue/documentation/api/list-view/#datasource), and bind the [`actionBegin`](https://ej2.syncfusion.com/vue/documentation/api/list-view/#actionbegin), [`actionComplete`](https://ej2.syncfusion.com/vue/documentation/api/list-view/#actioncomplete), and [`select`](https://ej2.syncfusion.com/vue/documentation/api/list-view/#select) events.

2. Perform custom operations in `actionBegin`, `actionComplete`, and select events.

3. Provide event log details for `actionBegin` and `actionComplete` events, and they will be displayed in the event trace panel when the ListView action starts and the dataSource bound successfully.

4. Get the selected item details from the [`SelectEventArgs`](../../api/list-view/selectEventArgs/) in the select event, and display the selected list item text in the event trace panel while selecting list items.

5. Use clear button to remove event trace information.

{% tab template="listview/checklist", isDefaultActive=true %}

```html
<template>
  <div id="sample">
    <div class="content-wrapper">
    <!-- ListView element -->
      <ejs-listview id='listview-def' ref='listviewInstance' :dataSource='data' width=250 :actionBegin='onBegin' :actionComplete='onComplete' :select='onSelect'>
      </ejs-listview>
    </div>
    <div id="list_event">
      <h4><b>Event Trace</b></h4>
      <div id="evt">
        <div class="eventarea" style="height:273px;overflow: auto">
          <span ref='EventLogEle' class="EventLog" id="EventLog" style="word-break: normal;"></span>
        </div>
        <div class="evtbtn">
          <ejs-button id="clear" @click.native='onClick'>Clear</ejs-button>
        </div>
      </div>
    </div>
  </div>
</template>
<style>
#EventLog b {
  color: #388e3c;
}

#listview-def {
  border: 1px solid #dcdcdc;
}
.content-wrapper {
  padding-left: 40px;
  padding-top: 36px;
}

.evtbtn {
  margin-top: 40px;
  margin-left: 70px;
}

/* csslint ignore:start */

hr {
  margin-top: 6px !important;
  margin-bottom: 6px !important;
}

/* csslint ignore:end */

#evt {
  border: 1px solid #dcdcdc;
  padding: 10px;
  min-width: 10px;
}

#sample {
  display: inline-flex;
}

.eventarea {
  min-width: 250px;
}

#list_event {
  margin-top: -25px;
  padding-left:40px;
  min-width: 200px;
}
</style>
<script>
import Vue from "vue";
import { ListViewPlugin } from "@syncfusion/ej2-vue-lists";
import {ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
Vue.use(ListViewPlugin);
Vue.use(ButtonPlugin);

export default {
  data: function() {
    return {
      data: [
  { text: "Hennessey Venom", id: "list-01" },
  { text: "Bugatti Chiron", id: "list-02" },
  { text: "Bugatti Veyron Super Sport", id: "list-03" },
  { text: "SSC Ultimate Aero", id: "list-04" },
  { text: "Koenigsegg CCR", id: "list-05" },
  { text: "McLaren F1", id: "list-06" },
  { text: "Aston Martin One- 77", id: "list-07" },
  { text: "Jaguar XJ220", id: "list-08" },
  { text: "McLaren P1", id: "list-09" },
  { text: "Ferrari LaFerrari", id: "list-10" }
]
    };
  },
  methods:{
    onBegin: function(){
     this.appendElement("<b>actionBegin </b> event is triggered<hr>");
    },
    onComplete: function(){
      this.appendElement("<b>actionComplete</b> is triggered <hr>");
    },
    onSelect: function(args){
    this.appendElement(args.text + "<b>&nbsp;&nbsp;is selected</b><hr>");
    },
    appendElement: function(html) {
     let span = document.createElement("span");
     span.innerHTML = html;
     let log = this.$refs.EventLogEle;
     log.insertBefore(span, log.firstChild);
    },
    onClick: function(event){
       this.$refs.EventLogEle.innerHTML = "";
    }
  }
}
</script>
```

{% endtab %}