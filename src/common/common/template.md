# Template

The Syncfusion Vue UI components support native Vue templates using single file components and Vue.component().

The two ways to configure template support are:

* Single File Components (.vue file)
* Vue.component()

## Single file components

* Define the template in a template.vue file, and create an empty object `data` in the **data option** of the template.vue file.

* Pass arguments as properties of a data object.

Refer to the following code snippet of template.vue file.

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

* Import the template.vue file in the corresponding app.vue file as specified in the following code snippet.

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

* Template function is assigned to the template property of the Syncfusion Vue component.

Refer to the following code snippet of App.vue file.

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

The template is initialized with `Vue.component()` where template is provided with the template option.
* The template is initialized with `Vue.component()` where template is provided with the template option.

* Pass arguments as properties of a data object.

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

* Template function is assigned to the template property of the Syncfusion Vue component.

* Refer to the following code snippet of App.vue file.

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

## Template sample

{% tab template="common/template", isDefaultActive=true %}

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
