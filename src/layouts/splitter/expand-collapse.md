---
title: "Expand and Collapse"
component: "Splitter"
description: "This section explains about how to configure collapsible splitter panes, which helps to do expand and collapse action dynamically."
---

# Expand and Collapse

## Collapsible panes

The Splitter panes can be configured with built-in expand and collapse functionalities. By default, the collapsible behavior is disabled. Enable the [collapsible](../api/splitter/#collapsible) behavior in the paneSettings property to show or hide the expand or collapse icons in the panes. You can dynamically expand and collapse the panes by using the corresponding icons.

The following code shows how to enable collapsible behavior.

{% tab template="splitter/expand-collapse" %}

```html

<template>
<div id="app" class="col-lg-12 control-section default-splitter">
    <ejs-splitter id='splitter' ref='splitterObj'  width='600px' height='200px'>
        <e-panes>
            <e-pane :content='content1' size ='200px' :collapsible=true></e-pane>
            <e-pane :content='content2' size ='200px' :collapsible=true></e-pane>
            <e-pane :content='content3' size ='200px' :collapsible=true></e-pane>
        </e-panes>
    </ejs-splitter>
</div>
</template>
<script>
import Vue from "vue";
import { SplitterPlugin } from '@syncfusion/ej2-vue-layouts';

Vue.use(SplitterPlugin);
var contentVue1 = Vue.component("contentTemp1", {
    template: `<div class="content"><h3 class="h3">PARIS </h3>Paris, the city of lights and love - this short guide is full of ideas for how to make the most of the romanticism...</div>`,
    data() {
        return {
            data: {}
        };
    }
});

var contentVue2 = Vue.component("contentTemp2", {
    template: `<div class="content"><h3 class="h3">CAMEMBERT </h3>The village in the Orne département of Normandy where the famous French cheese is originated from.</div>`,
    data() {
        return {
            data: {}
        };
    }
});

var contentVue3 = Vue.component("contentTemp3", {
    template: `<div class="content"><h3 class="h3">GRENOBLE </h3>The capital city of the French Alps and a major scientific center surrounded by many ski resorts, host of the Winter Olympics in 1968.</div>`,
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

## Programmatically control the expand and collapse action

The Splitter provides public method to control the expand and collapse behavior programmatically using the [expand](../api/splitter/#expand) and [collapse](../api/splitter/#collapse) methods. Refer to the following code example.

{% tab template="splitter/expand-collapse-method" %}

```html

<template>
<div id="app" class="col-lg-12 control-section default-splitter">
    <ejs-splitter id='splitter' ref='splitterObj'  width='600px' height='200px'>
        <e-panes>
            <e-pane :collapsible=true content='Left Pane' size ='200px'></e-pane>
            <e-pane :collapsible=true content='Middle Pane' size ='200px'></e-pane>
            <e-pane :collapsible=true content='Right Pane' size ='200px'></e-pane>
        </e-panes>
    </ejs-splitter>
    <div style="margin: 10px">
        <ejs-button id='expand' v-on:click.native="expandClick">Expand</ejs-button>
        <ejs-button id='collapse' v-on:click.native="collapseClick">Collapse</ejs-button>
    </div>
</div>

</template>
<script>
import Vue from "vue";
import { SplitterPlugin } from '@syncfusion/ej2-vue-layouts';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.use(SplitterPlugin);
Vue.use(ButtonPlugin);
export default {
    name: 'app',
    data () {
        return { }
    },
    methods: {
        expandClick : function() {
            this.$refs.splitterObj.expand(0);
        },
        collapseClick : function() {
            this.$refs.splitterObj.collapse(0);
        }
    }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";

#app {
    text-align: center;
    margin: 45px auto;
}
.content {
  justify-content: center;
  text-align: center;
  align-items: center;
  padding: 9px;
}
.e-splitter {
    margin: 0 auto;
}
.e-pane {
  text-align: center;
  align-items: center;
  display: grid;
}
#collapse {
  margin-left: 10px;
}
</style>

```

{% endtab %}

## Specify initial state to panes

You can render specific panes with collapsed state on page load. Specify a Boolean value to the [collapsed](../api/splitter/#collapsed) property to control this behavior. The following code explains how to collapse panes on rendering (the second panes renders with collapsed state).

{% tab template="splitter/collapsed" %}

```html

<template>
<div id="app" class="col-lg-12 control-section default-splitter">
    <ejs-splitter id='splitter' ref='splitterObj'  width='600px' height='200px'>
        <e-panes>
            <e-pane content='Left Pane' size ='200px' :collapsible=true></e-pane>
            <e-pane :collapsed=true content='Middle Pane' size ='200px' :collapsible=true></e-pane>
            <e-pane content='Right Pane' size ='200px' :collapsible=true></e-pane>
        </e-panes>
    </ejs-splitter>
</div>
</template>
<script>
import Vue from "vue";
import { SplitterPlugin } from '@syncfusion/ej2-vue-layouts';

Vue.use(SplitterPlugin);
export default {
    name: 'app',
    data () {
        return { }
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
  padding: 9px;
}

.e-splitter {
    margin: 0 auto;
}

.e-pane {
  text-align: center;
  align-items: center;
  display: grid;
}
</style>

```

{% endtab %}

## See Also

* [Resizable split panes](./resizing/)