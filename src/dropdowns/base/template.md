# Template

The Essential JS 2 for Vue Components support native Vue Templates, using Single File Components and Vue.component().

The Template support can be configured by these two ways given below.

* Single File Components (.vue file)
* Vue.component()

## Single File Components

* Define the template in a template.vue file, and create an empty object `data` in the **data option** of the template.vue file.

* For passing arguments, pass as property of data object.

Refer below code snippet of template.vue file

```html
// template.vue

<template>
  <div class="button">
    <ejs-button  :content="`${data.ShipCountry}`"></ejs-button>
  </div>
</template>

<script>

export default {
  data () {
    return {
        data: {}
    }
  }
}
</script>
```

* Import the template.vue file in your corresponding app.vue file as specified in the following code snippet.

```html
import buttonTemplate from './template.vue'
```

* Create a template function which returns an object {  key: 'template',  value: 'importedTemplate' }.

```html
cTemplate: function(e) {
   return {
       template: buttonTemplate
   };
}
```

* Template function is assigned to the template property of the Essential JS2 Vue Component.

Refer the below code snippet of App.vue file.

```html
// App.vue

<template>
  <div id="app">
      <ejs-grid ref="grid" :dataSource="ds">
                <e-columns>
                    <e-column headerText='Ship Country' width='150' textAlign='Center' :template='cTemplate' />
                    <e-column field="OrderID" headerText="Order ID" width=120 textAlign="Right" />
                    <e-column field="CustomerName" headerText="Customer Name" width=150 />
                </e-columns>
            </ejs-grid>
  </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { empData } from "./data";
import buttonTemplate from "./template.vue";

Vue.use(GridPlugin);

export default {
  data() {
    return {
      ds: empData,
      cTemplate: function(e) {
        return {
          template: buttonTemplate
        };
      }
    };
  }
};
</script>

<style>
@import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>

```

## Vue.component()

* The Template is initialized with `Vue.component()` where template is provided in the template option.
Create an empty object `data` in the data option for passing arguments.

* For passing arguments, pass as property of data object.

```html
var demoTemplate = Vue.component("demo", {
  template: "<ejs-button :content="`${data.ShipCountry}`"></ejs-button>",
  data() {
    return {
      data: {}
    };
  }
});
```

* Create a template function which returns an object {  key: 'template',  value: 'importedTemplate' }.

```html
cTemplate: function(e) {
   return {
       template: demoTemplate
   };
}
```

* Template function is assigned to the template property of the Essential JS2 Vue Component.

* Refer the below code snippet of App.vue file.

```html
// App.vue

<template>
  <div id="app">
      <ejs-grid ref="grid" :dataSource="ds">
                <e-columns>
                    <e-column headerText='Ship Country' width='150' textAlign='Center' :template='cTemplate' />
                    <e-column field="OrderID" headerText="Order ID" width=120 textAlign="Right" />
                    <e-column field="CustomerName" headerText="Customer Name" width=150 />
                </e-columns>
            </ejs-grid>
  </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { empData } from "./data";

Vue.use(GridPlugin);

var demoTemplate = Vue.component("demo", {
  template: "<ejs-button>{{data.ShipCountry}}</ejs-button>",
  data() {
    return {
      data: {}
    };
  }
});

export default {
  data() {
    return {
      ds: empData,
      cTemplate: function(e) {
        return {
          template: demoTemplate
        };
      }
    };
  }
};
</script>

<style>
@import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>

```

## Template Sample

{% tab template="base/template", isDefaultActive=true %}

```html
<template>
  <div id="grid">
    <ejs-grid ref="grid" :dataSource="ds">
      <e-columns>
        <e-column field="OrderID" headerText="Order ID" width=120 textAlign="Right" />
        <e-column field="CustomerName" headerText="Customer Name" width=150 />
        <e-column field="ShipCountry" headerText="Ship Country" width=150 :template='cTemplate'  />
      </e-columns>
    </ejs-grid>
  </div>
</template>
<script>
import Vue from 'vue';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
import { GridPlugin } from "@syncfusion/ej2-vue-grids";

Vue.use(GridPlugin);
Vue.use(ButtonPlugin);


var demoTemplate = Vue.component("demo", {
  template: '<ejs-button :content="`${data.ShipCountry}`"></ejs-button>',
  data() {
    return {
      data: {}
    };
  }
});

var empData = [{
      OrderID: 10248,
      ShipCountry: "France",
      CustomerName: "Paul Henriot"
    },
    {
      OrderID: 10249,
      ShipCountry: "Germany",
      CustomerName: "Karin Josephs"
    },
    {
      OrderID: 10250,
      ShipCountry: "Brazil",
      CustomerName: "Mario Pontes"
    },
    {
      OrderID: 10251,
      ShipCountry: "France",
      CustomerName: "Mary Saveley"
    }];

export default {
  data () {
    return {
      ds: empData,
      cTemplate: function (e) {
        return {
          template: demoTemplate
        };
      }
    }
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  #app {
    color: #008cff;
    height: 40px;
    left: 45%;
    position: absolute;
    top: 45%;
    width: 30%;
  }
</style>
```

{% endtab %}
