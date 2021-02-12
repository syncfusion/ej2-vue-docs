# Localization

Localization library allows you to localize the text content of the Syncfusion Vue UI component.

## Loading translations

To load translation object in your application use `load` function of `L10n` class.

{% tab template="common/intl" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' locale='de-DE' :allowGrouping='true' :allowPaging='true' :pageSettings='pageOptions' height='220px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=120></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=150></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
                <e-column field='ShipName' headerText='Ship Name' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { L10n, setCulture } from '@syncfusion/ej2-base';
import { GridPlugin, Page, Group } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

setCulture('de-DE');

L10n.load({
    'de-DE': {
        'grid': {
            'EmptyRecord': 'Keine Aufzeichnungen angezeigt',
            'GroupDropArea': 'Ziehen Sie einen Spaltenkopf hier, um die Gruppe ihre Spalte',
            'UnGroup': 'Klicken Sie hier, um die Gruppierung aufheben',
            'EmptyDataSourceError': 'DataSource darf bei der Erstauslastung nicht leer sein, da Spalten aus der dataSource im AutoGenerate Spaltenraster',
            'Item': 'Artikel',
            'Items': 'Artikel'
        },
        'pager':{
            'currentPageInfo': '{0} von {1} Seiten',
            'totalItemsInfo': '({0} Beiträge)',
            'firstPageTooltip': 'Zur ersten Seite',
            'lastPageTooltip': 'Zur letzten Seite',
            'nextPageTooltip': 'Zur nächsten Seite',
            'previousPageTooltip': 'Zurück zur letzten Seit',
            'nextPagerTooltip': 'Zum nächsten Pager',
            'previousPagerTooltip': 'Zum vorherigen Pager'
        }
    }
});

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      pageOptions: { pageSize: 7 }
    };
  },
  provide: {
    grid: [Page, Group]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>

```

{% endtab %}

## Changing current locale

Current locale can be changed for all the Essential JS 2 components in your application by invoking
 `setCulture` function with your desired culture name.

```typescript
import {L10n, setCulture} from '@syncfusion/ej2-base';
L10n.load({
    'fr-BE': {
       'Button': {
             'id': 'Numéro de commande',
             'date':'Date de commande'
         }
     }
});
setCulture('fr-BE');
```

>Note: Before changing a culture globally, ensure that locale text for the concerned culture is loaded through `L10n.load` function.
