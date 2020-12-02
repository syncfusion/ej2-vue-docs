# Filter list items in the ListView

The filtered data can be displayed in the ListView component depending upon on user inputs using the [`DataManager`](https://ej2.syncfusion.com/vue/documentation/data/getting-started/). Refer to the following steps to render the ListView with filtered data.

* Render a textbox to get input for filtering data.

* Render ListView with [`dataSource`](https://ej2.syncfusion.com/vue/documentation/api/list-view/#datasource), and set the [`sortOrder`](https://ej2.syncfusion.com/vue/documentation/api/list-view/#sortorder) property.

* Bind the `keyup` event for textbox to perform filtering operation. To filter list data, pass the list data source to the `DataManager`, manipulate the data using the [`executeLocal`](https://ej2.syncfusion.com/documentation/api/data/query/#executelocal) method, and then update filtered data as ListView dataSource.

{% tab template="listview/checklist", isDefaultActive=true %}

```html
<template>
  <div class="control-section">
    <div id = 'sample'>
      <input class="e-input" type="text" id='textbox' ref='textboxEle' placeholder="Filter" title="Type in a name" @keyup='onkeyup' />
      <!-- ListView element -->
      <ejs-listview id='list' ref='listObj' :dataSource='data' :fields='fields' sortOrder='Ascending'>
      </ejs-listview>
    </div>
  </div>
</template>
<style>
#list {
  box-shadow: 0 1px 4px #ddd;
  border-bottom: 1px solid #ddd;
}
#sample {
  height: 220px;
  margin: 0 auto;
  display: table;
}
</style>
<script>
import Vue from "vue";
import { ListViewPlugin } from "@syncfusion/ej2-vue-lists";
import { DataManager, Query, ODataV4Adaptor } from "@syncfusion/ej2-data";
Vue.use(ListViewPlugin);

export default {
  data: function() {
    return {
      data: [
        { text: "Hennessey Venom", id: "list-01" },
        { text: "Bugatti Chiron", id: "list-02" },
        { text: "Bugatti Veyron Super Sport", id: "list-03" },
        { text: "SSC Ultimate Aero", id: "list-04" },
        { text: "Koenigsegg CCR", id: "list-05" },
        { text: "McLaren F1", id: "list-06" }],
      fields: { text: "text", id: "id" },
    };
  },
  methods:{
   onkeyup: function(event){
      let keyupvalue = this.$refs.textboxEle.value;
      let data = new DataManager(this.data).executeLocal(new Query().where("text", "startswith", keyupvalue, true));
      if (!keyupvalue) {
        this.$refs.listObj.dataSource = this.data.slice();
      } else {
        this.$refs.listObj.dataSource = data;
      }
    }
  }
}
</script>
```

{% endtab %}

> In this demo, data has been filtered with starting character of the list items. You can also filter list items with ending character by passing the `endswith` in [where](https://ej2.syncfusion.com/documentation/api/data/query/#where) clause instead of `startswith`.