# Render ListView with hyper link navigation

We can use `anchor` tag along with `href` attribute in our ListView [`template`](https://ej2.syncfusion.com/vue/documentation/api/list-view/#template) property for navigation.

```typescript

var listVue = Vue.component("demo", {
  template: `<a target='_blank' v-bind:href='data.url'>{{data.name}}</a>`,
  data() {
    return {
      data: {}
    };
  }
});

```

In the below sample, we have rendered `ListView` with search engines URL.

{% tab template="listview/checklist", isDefaultActive=true %}

```html
<template>
   <div id="sample">
    <ejs-listview id='List' :dataSource='data' headerTitle='Search engines' showHeader='true' :template='anchortemplate'>
    </ejs-listview>
  </div>
</template>
<style>
 #List {
        max-width: 300px;
        margin: auto;
        border: 1px solid #dddddd;
        border-radius: 3px;
    }
    #List a {
      text-decoration: none;
    }
    #List .e-list-header {
        background: rgb(2, 120, 215);
        color: white;
        font-size: 19px;
        font-weight: 500;
    }
</style>
<script>
import Vue from "vue";
import { ListViewPlugin } from "@syncfusion/ej2-vue-lists";

Vue.use(ListViewPlugin);

var listVue = Vue.component("demo", {
  template: `<a target='_blank' v-bind:href='data.url'>{{data.name}}</a>`,
  data() {
    return {
      data: {}
    };
  }
});

export default {
  data: function() {
       return {
      data: [
        {name: 'Google', url: 'https://www.google.com'},
        {name: 'Bing', url: 'https://www.bing.com' },
        {name: 'Yahoo', url: 'https://www.yahoo.com'},
        {name: 'Ask.com', url: 'https://www.ask.com'},
        {name: 'AOL.com', url: 'https://www.aol.com'},
    ],
    anchortemplate: function () {
        return { template : listVue};
    },
    };
  },
}
</script>
```

{% endtab %}
