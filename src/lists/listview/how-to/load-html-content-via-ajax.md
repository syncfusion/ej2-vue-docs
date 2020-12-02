# Load HTML content via AJAX

We can set external `HTML` page content as [`template`](https://ej2.syncfusion.com/vue/documentation/api/list-view/#template) for our `ListView` component by making use of `AJAX` call.

```typescript

let ajax = new Ajax('./template.html', 'GET', false);
ajax.onSuccess = (e)=>{
    this.template = e;
}

ajax.send();

```

In the below sample, we have rendered smartphone settings template from external `HTML` file.

{% tab template="listview/ajax", isDefaultActive=true %}

```html
<template>
   <div id="sample">
    <ejs-listview id='element' :dataSource='data' headerTitle='Settings' showHeader='true' :template='template'>
    </ejs-listview>
  </div>
</template>
<style>
  #element {
    display: block;
    max-width: 300px;
    margin: auto;
    border: 1px solid #dddddd;
    border-radius: 3px;
}

#element .e-list-header {
    background: rgb(2, 120, 215);
    color: white;
    font-size: 19px;
    font-weight: 500;
}

#element.e-listview .e-list-item {
    padding: 10px 16px;
    height: 61px;

}

#element .e-list-item-header {
    font-size: 15px;
    font-weight: 500;
    line-height: 20px;
    height: 20px;
}

#element .e-list-content {
    line-height: 20px;
    height: 20px;
    font-size: 10px;
    font-style: italic;
    margin-top: -2px;
}
</style>
<script>
import Vue from "vue";
import { ListViewPlugin } from "@syncfusion/ej2-vue-lists";
import { Ajax } from '@syncfusion/ej2-base';

Vue.use(ListViewPlugin);

export default {
  data: function() {
    return {
      data: [
    { name: 'Network & Internet', id: '0', description: 'Wi-Fi, mobile, data usage, hotspot' },
    { name: 'Connected devices', id: '1', description: 'Bluetooth, cast, NFC' },
    { name: 'Battery', id: '2', description: '18% -4h 12m left' },
    { name: 'Display', id: '3', description: 'Wallpaper, sleep, font size' },
    { name: 'Sound', id: '4', description: 'Volume, vibration, Do Not Disturb' },
    { name: 'Storage', id: '5', description: '52% used - 15.48 GB free' }
],
    template:{}
    };
  },
  created: function() {
    let ajax = new Ajax('./template.html', 'GET', false);
    ajax.onSuccess = (e)=>{
    this.template = e;
    };
    ajax.send();
  }
}
</script>
```

{% endtab %}