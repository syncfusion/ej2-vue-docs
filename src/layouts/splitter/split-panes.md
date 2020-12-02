---
title: "Split Panes"
component: "Splitter"
description: "This section explain about split panes behaviours."
---

# Split Panes

This section explain about split panes behaviours.

## Horizontal layout

By default, splitter will render in horizontal orientation. Splitter container will be splitted as panes in horizontal flow direction with vertical separator.

{% tab template="splitter/split-panes" %}

```html

<template>
<div id="app" class="col-lg-12 control-section default-splitter">
    <ejs-splitter id='default-splitter' width='600px' height='230px'>
        <e-panes>
            <e-pane :content ='content1' size ='200px'></e-pane>
            <e-pane :content ='content2' size ='200px'></e-pane>
            <e-pane :content ='content3' size ='200px'></e-pane>
        </e-panes>
    </ejs-splitter>
</div>
</template>

<script>
import Vue from "vue";
import { SplitterPlugin } from '@syncfusion/ej2-vue-layouts';

Vue.use(SplitterPlugin);
var contentVue1 = Vue.component("contentTemp1", {
    template: `<div class="content">
                    <h3 class="h3">Grid </h3>
                    The ASP.NET DataGrid component, or DataTable is a feature-rich component used to display data in a tabular format.
                </div>`,
    data() {
        return {
            data: {}
        };
    }
});

var contentVue2 = Vue.component("contentTemp2", {
    template: `<div class="content">
                    <h3 class="h3">Schedule </h3>
                    The ASP.NET Scheduler, a.k.a. event calendar, facilitates almost all calendar features, thus allowing users to manage their time efficiently
                </div>`,
    data() {
        return {
            data: {}
        };
    }
});

var contentVue3 = Vue.component("contentTemp3", {
    template: `<div class="content">
                    <h3 class="h3">Chart </h3>
                    ASP.NET charts, a well-crafted easy-to-use charting package, is used to add beautiful charts in web and mobile applications
              </div>`,
    data() {
        return {
            data: {}
        };
    }
});

export default {
  name: 'app',
    data () {
    return {
    content1: function (){
        return { template: contentVue1 }
    },
    content2: function (){
        return { template: contentVue2 }
    },
    content3: function (){
        return { template: contentVue3 }
    }
    }
  }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";

#app {
    margin: 65px auto;
}
.content {
    padding: 10px;
}

.e-splitter {
    margin: 0 auto;
}
</style>

```

{% endtab %}

## Vertical layout

By setting [`orientation`](../api/splitter/#orientation) API as `Vertical`, splitter will render in vertical orientation. Splitter container will be splitted as panes in vertical flow direction with horizontal separator.

{% tab template="splitter/panes-orientation" %}

```html

<template>
<div id="app" class="col-lg-12 control-section default-splitter">
    <ejs-splitter id='vertical-splitter' orientation = 'Vertical' width='600px' height='300px'>
        <e-panes>
            <e-pane :content ='content1' size ='100px'></e-pane>
            <e-pane :content ='content2' size ='100px'></e-pane>
            <e-pane :content ='content3'></e-pane>
        </e-panes>
    </ejs-splitter>
</div>
</template>

<script>
import Vue from "vue";
import { SplitterPlugin } from '@syncfusion/ej2-vue-layouts';

Vue.use(SplitterPlugin);
var contentVue1 = Vue.component("contentTemp1", {
    template: `<div class="content">
                    <h3 class="h3">Grid</h3>
                    The ASP.NET DataGrid component, or DataTable is a feature-rich component used to display data in a tabular format.
                </div>`,
    data() {
        return {
            data: {}
        };
    }
});

var contentVue2 = Vue.component("contentTemp2", {
    template: `<div class="content">
                    <h3 class="h3">Schedule </h3>
                    The ASP.NET Scheduler, a.k.a. event calendar, facilitates almost all calendar features, thus allowing users to manage their time efficiently
                </div>`,
    data() {
        return {
            data: {}
        };
    }
});

var contentVue3 = Vue.component("contentTemp3", {
    template: `<div class="content">
                    <h3 class="h3">Chart </h3>
                    ASP.NET charts, a well-crafted easy-to-use charting package, is used to add beautiful charts in web and mobile applications
              </div>`,
    data() {
        return {
            data: {}
        };
    }
});

export default {
  name: 'app',
    data () {
    return {
    content1: function (){
        return { template: contentVue1 }
    },
    content2: function (){
        return { template: contentVue2 }
    },
    content3: function (){
        return { template: contentVue3 }
    }
    }
  }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";

.content {
  padding: 8px;
}

.e-splitter {
    margin: 0 auto;
}
</style>

```

{% endtab %}

> You can also render multiple panes in splitter with both `Horizontal/Vertical` orientations.

## Separator

By default, pane separator will be render with `1px` width/height. You can customize the separator size by using [`separatorSize`](../api/splitter/#separatorsize) API.

> For horizontal orientation, it will be considered as separator width.
> For vertical orientation, it will be considered as separator height.

{% tab template="splitter/panes-separator" %}

```html

<template>
<div id="app" class="col-lg-12 control-section default-splitter">
    <ejs-splitter id='splitter' width='600px' height='235px' separatorSize= '5'>
        <e-panes>
            <e-pane :content ='content1' size ='200px'></e-pane>
            <e-pane :content ='content2' size ='200px'></e-pane>
            <e-pane :content ='content3' size ='200px'></e-pane>
        </e-panes>
    </ejs-splitter>
</div>
</template>

<script>
import Vue from "vue";
import { SplitterPlugin } from '@syncfusion/ej2-vue-layouts';

Vue.use(SplitterPlugin);
var contentVue1 = Vue.component("contentTemp1", {
    template: `<div class="content">
                    <h3 class="h3">PARIS </h3>
                    Paris, the city of lights and love - this short guide is full of ideas for how to make the most of the romanticism...
                </div>`,
    data() {
        return {
            data: {}
        };
    }
});

var contentVue2 = Vue.component("contentTemp2", {
    template: `<div class="content">
                    <h3 class="h3">CAMEMBERT </h3>
                    The village in the Orne département of Normandy where the famous French cheese is originated from.
                </div>`,
    data() {
        return {
            data: {}
        };
    }
});

var contentVue3 = Vue.component("contentTemp3", {
    template: `<div class="content">
                    <h3 class="h3">GRENOBLE </h3>
                    The capital city of the French Alps and a major scientific center surrounded by many ski resorts, host of the Winter Olympics in 1968.
                </div>`,
    data() {
        return {
            data: {}
        };
    }
});

export default {
  name: 'app',
    data () {
    return {
    content1: function (){
        return { template: contentVue1 }
    },
    content2: function (){
        return { template: contentVue2 }
    },
    content3: function (){
        return { template: contentVue3 }
    }
    }
  }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";

#app {
    margin: 65px auto;
}
.content {
    padding: 10px;
}

.e-splitter {
    margin: 0 auto;
}
</style>

```

{% endtab %}

## Nested Splitter

Splitter provides support to render the nested pane to achieve the complex layouts. You can use the same `<div>` element for splitter pane and nested splitter.

> Also you can render the nested splitter using direct child of the splitter pane. For this, nested splitter should have `100%` width and height to match with the parent pane dimensions.

{% tab template="splitter/nested-splitter" %}

```html

<template>
<div id="app" class="col-lg-12 control-section default-splitter">
    <ejs-splitter id='nested-splitter' width='600px' height='265px' :created='onCreate' >
        <e-panes>
            <e-pane :content ='content1' size ='200px'></e-pane>
            <e-pane :content ='content2' size ='200px'></e-pane>
            <e-pane :content ='content3' size ='200px'></e-pane>
        </e-panes>
    </ejs-splitter>
</div>
</template>
<script>
import Vue from "vue";
import { SplitterPlugin } from '@syncfusion/ej2-vue-layouts';
import {Splitter} from '@syncfusion/ej2-layouts';

Vue.use(SplitterPlugin);
var contentVue1 = Vue.component("contentTemp1", {
    template: `<div class="content">
                    <h3 class="h3">PARIS </h3>
                    Paris, the city of lights and love - this short guide is full of ideas for how to make the most of the romanticism...
                </div>`,
    data() {
        return {
            data: {}
        };
    }
});

var contentVue2 = Vue.component("contentTemp2", {
    template: `<div class="content">
                    <h3 class="h3">CAMEMBERT </h3>
                    The village in the Orne département of Normandy where the famous French cheese is originated from.
                </div>`,
    data() {
        return {
            data: {}
        };
    }
});

var contentVue3 = Vue.component("contentTemp3", {
    template: `<div>
                <div id ='vertical_splitter' class="vertical_splitter">
                    <div>
                        <div class="content">
                            <h3 class="h3">GRENOBLE </h3>
                            The capital city of the French Alps and a major scientific center surrounded by many ski resorts, host of the Winter Olympics in 1968.
                        </div>
                    </div>
                    <div>
                        <div class="content">
                            <h3 class="h3">Australia </h3>
                            Australia is a country and continent surrounded by the Indian and Pacific oceans
                        </div>
                    </div>
                </div>
            </div>`,
    data() {
        return {
            data: {}
        };
    }
});

export default {
  name: 'app',
    data () {
    return {
    content1: function (){
        return { template: contentVue1 }
    },
    content2: function (){
        return { template: contentVue2 }
    },
    content3: function (){
        return { template: contentVue3 }
    }
    }
  },
  methods: {
    onCreate: function () {
        this.splitterObj = new Splitter({
            paneSettings: [
                { size: '150px', min: '20%' },
                { size: '100px', min: '20%'}
            ],
            orientation: 'Vertical'
        });
        this.splitterObj.appendTo('#vertical_splitter');
    }
}
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";

#app {
    margin: 55px auto;
}
.content {
    padding: 5px;
}

.vertical_splitter.e-splitter.e-splitter-vertical  {
  border: none;
}

.e-splitter {
    margin: 0 auto;
}
</style>

```

{% endtab %}

## Add or remove pane

You can add or remove panes programmatically to the splitter, by using [addPane](../api/splitter#addpane) and [removePane](../api/splitter#removepane) methods.

### Add pane

You can add the panes dynamically in the splitter by passing [`paneProperties`](../api/splitter/panePropertiesModel) along with index to the [addPane](../api/splitter/#addpane) method

{% tab template="splitter/add-pane" %}

```html

<template>
<div id="app" class="col-lg-12 control-section default-splitter">
    <ejs-splitter id='splitter' ref='splitterObj'  width='700px' height='200px'>
        <e-panes>
            <e-pane content ='Pane 1' size ='300px'></e-pane>
            <e-pane content ='Pane 2' size ='300px'></e-pane>
        </e-panes>
    </ejs-splitter>
    <div class="addBtn">
      <button id='addButton' class="e-btn" v-on:click = 'addPane'>Add Pane</button>
    </div>
</div>
</template>
<script>
import Vue from "vue";
import { SplitterPlugin } from '@syncfusion/ej2-vue-layouts';
import { PanePropertiesModel } from '@syncfusion/ej2-layouts';

Vue.use(SplitterPlugin);

export default {
  name: 'app',
    data () {
    return {
    }
  },
  methods: {
    addPane: function () {
         this.$refs.splitterObj.$el.ej2_instances[0].addPane({
      size: '200px',
      content: 'New Pane',
      min: '30px',
      max: '250px',
      }, 1);
    }
}
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";

#app {
    margin: 65px auto;
}
#splitter1 div.e-pane-horizontal {
    padding: 5px;
}

.addBtn {
  margin-top: 20px;
  text-align: initial;
}
</style>

```

{% endtab %}

### Remove pane

You can remove the split panes dynamically by passing the pane index to [removePane](../api/splitter/#removepane) method.

{% tab template="splitter/remove-pane" %}

```html

<template>
<div id="app" class="col-lg-12 control-section default-splitter">
    <ejs-splitter id='splitter' ref='splitterObj'  width='700px' height='200px'>
        <e-panes>
            <e-pane content ='Pane 1' size ='300px'></e-pane>
            <e-pane content ='Pane 2' size ='300px'></e-pane>
            <e-pane content ='Pane 3' size ='300px'></e-pane>
        </e-panes>
    </ejs-splitter>
    <div class="removeBtn">
      <button id='removeButton' class="e-btn" v-on:click = 'removePane'>Remove Pane</button>
    </div>
</div>
</template>

<script>
import Vue from "vue";
import { SplitterPlugin } from '@syncfusion/ej2-vue-layouts';

Vue.use(SplitterPlugin);

export default {
    name: 'app',
        data () {
        return {
        }
    },
    methods: {
        removePane: function () {
            this.$refs.splitterObj.removePane(1);
        }
    }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";

#app {
    text-align: center;
    margin: 65px auto;
}
.content {
  justify-content: center;
  text-align: center;
  align-items: center;
}

.removeBtn {
  margin-top: 20px;
  text-align: initial;
}
</style>

```

{% endtab %}

## See Also

* [Resizable split panes](./resizing/)
* [Collapsible panes](./expand-collapse/)
* [Define size to a panes](./pane-sizing/)
* [Specify content to a panes](./pane-content/)