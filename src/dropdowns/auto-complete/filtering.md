---
title: "Autocomplete Filtering"
component: "AutoComplete"
description: "This section for Syncfusion vue autocomplete control explains the built-in filtering support with a rich set of filtering configurations."
---

# Filtering

The AutoComplete has built-in support to filter data items. The filter operation starts
as soon as you start typing characters in the component.

To filter the Vue AutoComplete items, you can check on this video:

`youtube:7YycZgH89lk`

## Change the filter type

Determines on which filter type, the component needs to be considered on search action.
The available [`filterType`](../api/auto-complete/#filtertype) and its supported data types are

| Filter Type | Description | Supported Types |
|------|------|-------------|
| StartsWith | Checks whether a value begins with the specified value. | String |
| EndsWith | Checks whether a value ends with specified value. | String |
| Contains | Checks whether a value contains with specified value. | String |

The following examples shows the data filtering is done with StartsWith type.

{% tab template="auto-complete/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <div class='autocomplete'>
          <ejs-autocomplete :dataSource='data' :fields='fields' sortOrder='sortOrder' :filterType='filterType' :query='query' :placeholder="waterMark" ></ejs-autocomplete>
        </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { AutoCompletePlugin } from '@syncfusion/ej2-vue-dropdowns';
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

Vue.use(AutoCompletePlugin);

var remoteData = new DataManager({
    url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
    adaptor: new ODataV4Adaptor,
    crossDomain: true
});

export default {
  name: 'app',
   data () {
    return {
      waterMark : 'Find a customer',
      data: remoteData,
      fields: { value: 'ContactName' },
      query: new Query().select(['ContactName']),
      sortOrder: 'Ascending',
      filterType: 'StartsWith'
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  #app {
    color: #008cff;
    height: 40px;
    position: absolute;
    top: 10%;
    width: 90%;
  }

  .autocomplete {
    width: 30%;
    margin: 0 auto;
  }

</style>
```

{% endtab %}

## Filter item count

You can specify the filter suggestion item count through [`suggestionCount`](../api/auto-complete/#suggestioncount) property of AutoComplete.
The following example, to restrict the suggestion list item counts as 5.

{% tab template="auto-complete/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <div class='autocomplete'>
      <ejs-autocomplete :dataSource='data' :fields='fields' sortOrder='sortOrder'
      :query='query' :suggestionCount='suggestionCount' :placeholder="waterMark"></ejs-autocomplete>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { AutoCompletePlugin } from '@syncfusion/ej2-vue-dropdowns';
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

Vue.use(AutoCompletePlugin);

var remoteData = new DataManager({
    url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
    adaptor: new ODataV4Adaptor,
    crossDomain: true
});

export default {
  name: 'app',
   data () {
    return {
      waterMark : 'Find a customer',
      data: remoteData,
      fields: { value: 'ContactName' },
      query: new Query().select(['ContactName', 'CustomerID']),
      sortOrder: 'Ascending',
      suggestionCount: 5
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
   #app {
    color: #008cff;
    height: 40px;
    position: absolute;
    top: 10%;
    width: 90%;
  }

  .autocomplete {
    width: 30%;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Limit the minimum filter character

You can set the limit for the character count to filter the data on the AutoComplete.
This can be done by set the [`minLength`](../api/auto-complete/#minlength) property to AutoComplete.

In the following example, the remote request doesn't fetch the search data, until the
search key contains three characters.

{% tab template="auto-complete/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <div class='autocomplete'>
      <ejs-autocomplete :dataSource='data' :fields='fields' sortOrder='sortOrder'
      :query='query' :filterType='filterType' :minLength='minLength'
      :placeholder="waterMark"></ejs-autocomplete>
      </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { AutoCompletePlugin } from '@syncfusion/ej2-vue-dropdowns';
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

Vue.use(AutoCompletePlugin);

var remoteData = new DataManager({
    url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
    adaptor: new ODataV4Adaptor,
    crossDomain: true
});

export default {
  name: 'app',
   data () {
    return {
      waterMark : 'Find a customer',
      data: remoteData,
      fields: { value: 'ContactName' },
      query: new Query().select(['ContactName', 'CustomerID']),
      sortOrder: 'Ascending',
      filterType: 'StartsWith',
      minLength: 3
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  #app {
    color: #008cff;
    height: 40px;
    position: absolute;
    top: 10%;
    width: 90%;
  }

  .autocomplete {
    width: 30%;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Case sensitive filtering

Data items can be filtered either with or without case sensitivity using the `DataManager`.
This can be done by setting the [`ignoreCase`](../api/auto-complete/#ignorecase) property of AutoComplete.

The following sample depicts how to filter the data with case-sensitive.

{% tab template="auto-complete/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='autocomplete'>
        <ejs-autocomplete :dataSource='data' :fields='fields' sortOrder='sortOrder' :query='query' :filterType='filterType' :ignoreCase='ignoreCase' :placeholder="waterMark" ></ejs-autocomplete>
      </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { AutoCompletePlugin } from '@syncfusion/ej2-vue-dropdowns';
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

Vue.use(AutoCompletePlugin);

var remoteData = new DataManager({
    url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
    adaptor: new ODataV4Adaptor,
    crossDomain: true
});

export default {
  name: 'app',
   data () {
    return {
      waterMark : 'Find a customer',
      data: remoteData,
      fields: { value: 'ContactName' },
      query: new Query().select(['ContactName']),
      sortOrder: 'Ascending',
      filterType: 'StartsWith',
      ignoreCase: false
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  #app {
    color: #008cff;
    height: 40px;
    position: absolute;
    top: 10%;
    width: 90%;
  }

  .autocomplete {
    width: 30%;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Diacritics Filtering

An AutoComplete supports diacritics filtering which will ignore the diacritics and makes
it easier to filter the results in international characters lists when the [`ignoreAccent`](../api/auto-complete/#ignoreaccent)
is enabled.

In the following sample,data with diacritics are bound as dataSource for AutoComplete.

{% tab template="auto-complete/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
     <div class='autocomplete'>
        <ejs-autocomplete :dataSource='data' :ignoreAccent='ignoreAccent'
        :placeholder="waterMark" ></ejs-autocomplete>
      </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { AutoCompletePlugin } from '@syncfusion/ej2-vue-dropdowns';

Vue.use(AutoCompletePlugin);

export default {
  name: 'app',
   data () {
    return {
      data: [
                'Aeróbics',
                'Aeróbics en Agua',
                'Aerografía',
                'Aeromodelaje',
                'Águilas',
                'Ajedrez',
                'Ala Delta',
                'Álbumes de Música',
                'Alusivos',
                'Análisis de Escritura a Mano'
            ],
            ignoreAccent: true,
            waterMark: 'e.g: aero'

    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  #app {
    color: #008cff;
    height: 40px;
    position: absolute;
    top: 10%;
    width: 90%;
  }

  .autocomplete {
    width: 30%;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## See Also

* [How to achieve autofill while filtering](./how-to/autofill/)
* [How to group the data using header](./grouping/)
* [How to highlight the search data](./how-to/custom-search/)