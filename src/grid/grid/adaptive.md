---
title: "Adaptive"
component: "Grid"
description: "Learn how to render the row elements, filter, sort, and edit dialogs adaptively in the Essential JS 2 DataGrid control."
---

# Adaptive View

The Grid user interface (UI) was redesigned to provide an optimal viewing experience and improve usability on small screens. This interface will render the filter, sort, and edit dialogs adaptively and have an option to render the grid row elements in the vertical direction.

## Render adaptive dialogs

When we enable the [`enableAdaptiveUI`](../api/grid/#enableadaptiveui) property, the grid will render the filter, sort, and edit dialogs in full screen for a better user experience. This behavior is demonstrated in the below demo.

{% tab template="grid/adaptive" %}

```html
<template>
    <div id="app">
    <div class="e-adaptive-demo e-bigger">
      <div class="e-mobile-layout">
        <div class="e-mobile-content">
        <ejs-grid ref='grid' id='adaptivebrowser' :dataSource="data" height='100%' :enableAdaptiveUI='true' :allowPaging='true' :allowSorting='true'      :allowFiltering='true' :editSettings='editSettings' :toolbar='toolbar' :filterSettings='filterSettings' :load='load'>
                <e-columns>
                    <e-column field='SNO' headerText='S NO' width='150' :isPrimaryKey='true' :validationRules='orderidrules'></e-column>
                    <e-column field='Model' headerText='Model Name' width='200' editType='dropdownedit' :validationRules='customeridrules'></e-column>
                    <e-column field='Developer' headerText='Developer' width='200' :validationRules='customeridrules' :filter='menuFilter'></e-column>
                    <e-column field='ReleaseDate' headerText='Released Date' width='200' type='date' format='yMMM' editType='datepickeredit'></e-column>
                    <e-column field='AndroidVersion' headerText='Android Version' width='200' :validationRules='customeridrules' :filter='checkboxFilter'></e-column>
                </e-columns>
            </ejs-grid>
            </div>
            </div>
            <br></br>
            <div class="datalink">Source:
              <a href="https://en.wikipedia.org/wiki/List_of_Android_smartphones"
                target="_blank">Wikipedia: List of Android smartphones</a>
              </div>
            </div>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Filter, Sort, Edit, Toolbar, Page } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js'
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      orderidrules: { required: true, number: true },
      customeridrules: { required: true },
      editSettings: { allowAdding: true, allowEditing: true, allowDeleting: true, mode: 'Dialog' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel', 'Search'],
      filterSettings: { type: 'Excel' },
      menuFilter: {
        type : 'Menu'
      },
      checkboxFilter: {
        type : 'CheckBox'
      }
    };
  },
  methods: {
    load: function() {
        (this.$refs.grid as any).$el.ej2_instances[0].adaptiveDlgTarget = document.getElementsByClassName('e-mobile-content')[0];
    }
  },
  provide: {
    grid: [Filter, Sort, Edit, Toolbar, Page]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
 .e-grid .custom {
    background-color: #f48fb1 !important;/* csslint allow: important */
    color: white;
  }

  .e-grid .custom {
    background-color: #fce4ec;
    color: white;
  }

  /* The device with borders */
  .e-mobile-layout {
    position: relative;
    width: 360px;
    height: 640px;
    margin: auto;
    border: 16px #f4f4f4 solid;
    border-top-width: 60px;
    border-bottom-width: 60px;
    border-radius: 36px;
    box-shadow: 0 0px 2px rgb(144 144 144), 0 0px 10px rgb(0 0 0 / 16%);
  }

  /* The horizontal line on the top of the device */
  .e-mobile-layout:before {
    content: '';
    display: block;
    width: 60px;
    height: 5px;
    position: absolute;
    top: -30px;
    left: 50%;
    transform: translate(-50%, -50%);
    background: #ebebeb;
    border-radius: 10px;
  }

  /* The circle on the bottom of the device */
  .e-mobile-layout:after {
    content: '';
    display: block;
    width: 35px;
    height: 35px;
    position: absolute;
    left: 50%;
    bottom: -65px;
    transform: translate(-50%, -50%);
    background: #e8e8e8;
    border-radius: 50%;
  }

  /* The screen (or content) of the device */
  .e-mobile-layout .e-mobile-content {
    overflow-x: hidden;
    height: 100%;
    background: white;
    border: 0px solid #dddddd;
  }

  .highcontrast .e-mobile-layout {
    border: 16px #000000 solid;
    border-top-width: 60px;
    border-bottom-width: 60px;
    box-shadow: -1px 2px white, -2px -2px white, 2px -2px white, 2px 1px white;
  }

  .e-responsive-dialog {
    box-shadow: none;
    border: 1px solid #dddddd;
  }

  /* Render the mobile pager by default */
  @media (max-width: 3840px) {
    .e-adaptive-demo .e-pager {
    padding: 13px 0;
  }

  .e-adaptive-demo .e-pager div.e-parentmsgbar {
    box-sizing: border-box;
    display: inline-block;
    float: initial;
    padding-bottom: 0;
    padding-right: 0;
    padding-top: 0;
    text-align: center;
    vertical-align: top;
    width: calc(60% - 48px);
  }

  .e-adaptive-demo .e-pager .e-pagesizes {
    display: none;
  }

  .e-adaptive-demo .e-pager .e-pagecountmsg {
    display: none;
  }

  .e-adaptive-demo .e-pager .e-pagercontainer {
    display: none;
  }

  .e-adaptive-demo .e-pager .e-icons {
    font-size: 11px;
  }

  .e-adaptive-demo .e-pager .e-mfirst,
  .e-adaptive-demo .e-pager .e-mprev,
  .e-adaptive-demo .e-pager .e-mnext,
  .e-adaptive-demo .e-pager .e-mlast {
    border: 0;
    box-sizing: border-box;
    display: inline-block;
    padding: 1% 5%;
  }

  .e-adaptive-demo .e-pager .e-mfirst {
    margin-right: 4px;
    text-align: right;
    width: calc(10% + 11px);
  }
  .e-adaptive-demo .e-pager .e-mprev {
    margin: 0 4px;
    text-align: right;
    width: 10%;
  }

  .e-adaptive-demo .e-pager .e-mnext {
    margin: 0 4px;
    text-align: left;
    width: 10%;
  }

  .e-adaptive-demo .e-pager .e-mlast {
    margin-left: 4px;
    text-align: left;
    width: calc(10% + 11px);
  }

  .e-adaptive-demo .e-bigger .e-pager,
  .e-adaptive-demo .e-pager.e-bigger {
    padding: 19px 0;
  }

  .e-adaptive-demo .e-bigger .e-pager.e-rtl div.e-parentmsgbar,
  .e-adaptive-demo .e-pager.e-bigger.e-rtl div.e-parentmsgbar {
    margin-right: 0;
  }

  .e-adaptive-demo .e-bigger .e-pager div.e-parentmsgbar,
  .e-adaptive-demo .e-pager.e-bigger div.e-parentmsgbar {
    padding: 0;
  }
  }
  
  .e-dlg-target.e-scroll-disabled {
    overflow: auto !important;
  }
</style>
```

{% endtab %}

## Vertical row rendering

The grid will render the row elements in vertical order while setting the [`rowRenderingMode`](../api/grid/rowRenderingMode/) property value as **Vertical**.

{% tab template="grid/adaptive" %}

```html
<template>
    <div id="app">
    <div class="e-adaptive-demo e-bigger">
      <div class="e-mobile-layout">
        <div class="e-mobile-content">
        <ejs-grid ref='grid' id='adaptivebrowser' :dataSource="data" height='100%' :enableAdaptiveUI='true' :allowPaging='true' :allowSorting='true' :allowFiltering='true' :editSettings='editSettings' :toolbar='toolbar' :filterSettings='filterSettings' :load='load'>
                <e-columns>
                    <e-column field='SNO' headerText='S NO' width='150' :isPrimaryKey='true' :validationRules='orderidrules'></e-column>
                    <e-column field='Model' headerText='Model Name' width='200' editType='dropdownedit' :validationRules='customeridrules'></e-column>
                    <e-column field='Developer' headerText='Developer' width='200' :validationRules='customeridrules' :filter='menuFilter'></e-column>
                    <e-column field='ReleaseDate' headerText='Released Date' width='200' type='date' format='yMMM' editType='datepickeredit'></e-column>
                    <e-column field='AndroidVersion' headerText='Android Version' width='200' :validationRules='customeridrules' :filter='checkboxFilter'></e-column>
                </e-columns>
                <e-aggregates>
                    <e-aggregate>
                        <e-columns>
                            <e-column type="Count" field="Model" :footerTemplate="sumTemplate" >
                            </e-column>
                        </e-columns>
                    </e-aggregate>
                </e-aggregates>
            </ejs-grid>
            </div>
            </div>
            <br></br>
            <div className="datalink">Source:
              <a href="https://en.wikipedia.org/wiki/List_of_Android_smartphones"
                target="_blank">Wikipedia: List of Android smartphones</a>
              </div>
            </div>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Filter, Sort, Edit, Toolbar, Page, Aggregate } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js'
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      orderidrules: { required: true, number: true },
      customeridrules: { required: true },
      editSettings: { allowAdding: true, allowEditing: true, allowDeleting: true, mode: 'Dialog' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel', 'Search'],
      filterSettings: { type: 'Excel' },
      rowMode: 'Vertical',
      menuFilter: {
        type : 'Menu'
      },
      checkboxFilter: {
        type : 'CheckBox'
      },
      sumTemplate: function() {
        return {
            template: Vue.component('sumTemplate', {
            template: `<span>Total Models: {{data.Count}}</span>`,
            data: function () {return {data: {data: {}}};}
            })
        }
      }
    };
  },
  methods: {
    load: function() {
        (this.$refs.grid as any).$el.ej2_instances[0].adaptiveDlgTarget = document.getElementsByClassName('e-mobile-content')[0];
    }
  },
  provide: {
    grid: [Filter, Sort, Edit, Toolbar, Page, Aggregate]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
 .e-grid .custom {
    background-color: #f48fb1 !important;/* csslint allow: important */
    color: white;
  }

  .e-grid .custom {
    background-color: #fce4ec;
    color: white;
  }

  /* The device with borders */
  .e-mobile-layout {
    position: relative;
    width: 360px;
    height: 640px;
    margin: auto;
    border: 16px #f4f4f4 solid;
    border-top-width: 60px;
    border-bottom-width: 60px;
    border-radius: 36px;
    box-shadow: 0 0px 2px rgb(144 144 144), 0 0px 10px rgb(0 0 0 / 16%);
  }

  /* The horizontal line on the top of the device */
  .e-mobile-layout:before {
    content: '';
    display: block;
    width: 60px;
    height: 5px;
    position: absolute;
    top: -30px;
    left: 50%;
    transform: translate(-50%, -50%);
    background: #ebebeb;
    border-radius: 10px;
  }

  /* The circle on the bottom of the device */
  .e-mobile-layout:after {
    content: '';
    display: block;
    width: 35px;
    height: 35px;
    position: absolute;
    left: 50%;
    bottom: -65px;
    transform: translate(-50%, -50%);
    background: #e8e8e8;
    border-radius: 50%;
  }

  /* The screen (or content) of the device */
  .e-mobile-layout .e-mobile-content {
    overflow-x: hidden;
    height: 100%;
    background: white;
    border: 0px solid #dddddd;
  }

  .highcontrast .e-mobile-layout {
    border: 16px #000000 solid;
    border-top-width: 60px;
    border-bottom-width: 60px;
    box-shadow: -1px 2px white, -2px -2px white, 2px -2px white, 2px 1px white;
  }

  .e-responsive-dialog {
    box-shadow: none;
    border: 1px solid #dddddd;
  }

  /* Render the mobile pager by default */
  @media (max-width: 3840px) {
    .e-adaptive-demo .e-pager {
    padding: 13px 0;
  }

  .e-adaptive-demo .e-pager div.e-parentmsgbar {
    box-sizing: border-box;
    display: inline-block;
    float: initial;
    padding-bottom: 0;
    padding-right: 0;
    padding-top: 0;
    text-align: center;
    vertical-align: top;
    width: calc(60% - 48px);
  }

  .e-adaptive-demo .e-pager .e-pagesizes {
    display: none;
  }

  .e-adaptive-demo .e-pager .e-pagecountmsg {
    display: none;
  }

  .e-adaptive-demo .e-pager .e-pagercontainer {
    display: none;
  }

  .e-adaptive-demo .e-pager .e-icons {
    font-size: 11px;
  }

  .e-adaptive-demo .e-pager .e-mfirst,
  .e-adaptive-demo .e-pager .e-mprev,
  .e-adaptive-demo .e-pager .e-mnext,
  .e-adaptive-demo .e-pager .e-mlast {
    border: 0;
    box-sizing: border-box;
    display: inline-block;
    padding: 1% 5%;
  }

  .e-adaptive-demo .e-pager .e-mfirst {
    margin-right: 4px;
    text-align: right;
    width: calc(10% + 11px);
  }
  .e-adaptive-demo .e-pager .e-mprev {
    margin: 0 4px;
    text-align: right;
    width: 10%;
  }

  .e-adaptive-demo .e-pager .e-mnext {
    margin: 0 4px;
    text-align: left;
    width: 10%;
  }

  .e-adaptive-demo .e-pager .e-mlast {
    margin-left: 4px;
    text-align: left;
    width: calc(10% + 11px);
  }

  .e-adaptive-demo .e-bigger .e-pager,
  .e-adaptive-demo .e-pager.e-bigger {
    padding: 19px 0;
  }

  .e-adaptive-demo .e-bigger .e-pager.e-rtl div.e-parentmsgbar,
  .e-adaptive-demo .e-pager.e-bigger.e-rtl div.e-parentmsgbar {
    margin-right: 0;
  }

  .e-adaptive-demo .e-bigger .e-pager div.e-parentmsgbar,
  .e-adaptive-demo .e-pager.e-bigger div.e-parentmsgbar {
    padding: 0;
  }
  }
  
  .e-dlg-target.e-scroll-disabled {
    overflow: auto !important;
  }
</style>
```

{% endtab %}

> * [`enableAdaptiveUI`](../api/grid/#enableadaptiveui) property must be enabled for vertical row rendering.

### Supported features by vertical row rendering

The following features are only supported in vertical row rendering:

* Paging
* Sorting
* Filtering
* Selection
* Dialog Editing
* Aggregate
* Infinite scroll
* Toolbar
