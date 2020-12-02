# Display spinner until list items are loaded

The features of the ListView component such as remote data-binding take more time to fetch data from corresponding dataSource/remote URL. In this case, you can use EJ2 `Spinner` to enhance the appearance of the UI. This section explains how to load a spinner component to groom the appearance.

Refer to the following code sample to render the spinner component.

```typescript
    createSpinner({
        target: this.spinnerEle.nativeElement
    });
    showSpinner(this.spinnerEle.nativeElement);
```

Here, the data is fetched from `Northwind` Service URL; it takes a few seconds to load the data. To enhance the UI, the spinner component has been rendered initially. After the data is loaded from remote URL, the spinner component will be hidden in ListView [`actionComplete`](https://ej2.syncfusion.com/vue/documentation/api/list-view/#actioncomplete) event.

{% tab template="listview/data-binding/remote-data", isDefaultActive=true %}

```html
<template>
 <div class="control-section">
    <div id="flat-list">
    <!-- ListView element -->
    <ejs-listview id='sample-list' :dataSource='data' :query='query' :fields='fields' :headerTitle='headerTitle' showHeader='true' :actionComplete='onComplete'></ejs-listview>
    </div>
    <div ref='spinnerEle' id="spinner" ></div>
  </div>
</template>
<style>
#sample-list {
    border: 1px solid #dddddd;
    border-radius: 3px;
    margin: auto;
}
#flat-list {
    width: 50%;
    padding: 10px;
    margin: auto;
}
</style>
<script>
import Vue from "vue";
import { ListViewPlugin } from "@syncfusion/ej2-vue-lists";
import { DataManager, Query } from '@syncfusion/ej2-data';
import { createSpinner, showSpinner, setSpinner } from '@syncfusion/ej2-vue-popups';

Vue.use(ListViewPlugin);
export default {
  data: function() {
     return {
      data: new DataManager({
        url: '//js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/',
        crossDomain: true
      }),
      query: new Query().from('Products').select('ProductID,ProductName').take(10),
      fields:  { id: 'ProductID', text: 'ProductName' },
      headerTitle: 'Products',
    };
  },
  mounted: function(){
     createSpinner({ target: this.$refs.spinnerEle });
    showSpinner(this.$refs.spinnerEle);
  },
  methods: {
    onComplete: function(){
      this.$refs.spinnerEle.style.display = "none";
    }
  }
}
</script>
```

{% endtab %}
