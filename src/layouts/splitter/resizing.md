---
title: "Resize"
component: "Splitter"
description: "This section explain about split panes resizing behaviors."
---

# Resize

By default, resizing will be enable for split panes. Resizing gripper element will be add to the separator to makes the resize easy.

> Horizontal splitter will allows to resize in horizontal directions.
> Vertical splitter will allows to resize in vertical directions.

While resizing, previous and next panes will be adjust its dimensions automatically.

## Min and Max validation

Splitter allows you to set the minimum and maximum sizes for each pane. Resizing will not be occur over the [minimum](../api/splitter/paneProperties/#min) and [maximum](../api/splitter/paneProperties/#max) values.

{% tab template="splitter/resize-min-max" %}

```html

<template>
<div id="app" class="col-lg-12 control-section default-splitter">
    <ejs-splitter id='splitter' ref='splitterObj'  width='600px' height='200px'>
        <e-panes>
            <e-pane :content='content1' size ='200px' min='20%' max='40%'></e-pane>
            <e-pane :content='content2' size ='200px' min='30%' max='60%'></e-pane>
            <e-pane :content='content3' size ='200px'></e-pane>
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

## Prevent resizing

You can disable the resizing for the pane by setting `false` to the [`resizable`](../api/splitter/panePropertiesModel/#resizable) API within [paneSettings](../api/splitter/#panesettings).

> Splitter resizing will be enabled only when the target of the adjacent pane's `resizable` api should also be in `true` state.

{% tab template="splitter/resize-min-max" %}

```html

<template>
<div id="app" class="col-lg-12 control-section default-splitter">
    <ejs-splitter id='splitter' ref='splitterObj'  width='600px' height='200px'>
        <e-panes>
            <e-pane :content='content1' size ='200px' min='20%' max='40%' :resizable ='resize'></e-pane>
            <e-pane :content='content2' size ='200px' min='30%' max='60%'></e-pane>
            <e-pane :content='content3' size ='200px'></e-pane>
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
        },
        resize: false
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

## Refresh content on resizing

While resizing the panes, you can refresh the pane contents by using either [`resizeStart`](../api/splitter/#resizestart), [`resizing`](../api/splitter/#resizestart) or [`resizeStop`](../api/splitter/#resizestart) events.

## Customize the resize grip and cursor

You can customize the resize gripper icon and cursor in css level.

{% tab template="splitter/resize-min-max" %}

```html

<template>
<div id="app" class="col-lg-12 control-section default-splitter">
    <ejs-splitter id='splitter' ref='splitterObj'  width='600px' height='200px'>
        <e-panes>
            <e-pane :content='content1' size ='200px' min='20%' max='40%'></e-pane>
            <e-pane :content='content2' size ='200px' min='20%' max='60%'></e-pane>
            <e-pane :content='content3' size = '200px'></e-pane>
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

.default-splitter .e-splitter .e-split-bar .e-resize-handler:before {
  content: "\e934";
  font-family: 'e-icons';
  font-size: 11px;
  transform: rotate(90deg);
}

.e-splitter .e-split-bar.e-split-bar-horizontal.e-resizable-split-bar,
.e-splitter .e-split-bar.e-split-bar-horizontal.e-resizable-split-bar::after {
  cursor: e-resize;
}
</style>

```

{% endtab %}

## See Also

* [Collapsible panes](./expand-collapse/)