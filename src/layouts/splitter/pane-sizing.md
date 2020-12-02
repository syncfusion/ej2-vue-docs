---
title: "Pane Content"
component: "Splitter"
description: "This section explains about user can feed pane sizes."
---

# Pane Sizing

Splitter allows you to provide pane sizes either in `pixel` or `percentage` formats.

## Auto size panes

The splitter's panes are adjusted automatically during resizing if the size is not specified externally to panes, because the panes are designed based on flex layout by default. When add/remove or show/hide the panes, the panes are auto aligned within its container.

{% tab template="splitter/resize-min-max" %}

```html

<template>
<div id="app" class="col-lg-12 control-section default-splitter">
    <ejs-splitter id='splitter' ref='splitterObj'  width='600px' height='200px'>
        <e-panes>
            <e-pane :content='content1'></e-pane>
            <e-pane :content='content2'></e-pane>
            <e-pane :content='content3'></e-pane>
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

## Fixed pane

You can render the split panes with fixed size in both `horizontal` and `vertical` mode. Even if you provide fixed sizes to all the panes, the last pane is considered as a flexible pane.

> Last pane is flexible because the splitter needs one pane as flexible pane always, to adjust its remaining layout space.

{% tab template="splitter/resize-min-max" %}

```html

<template>
<div id="app" class="col-lg-12 control-section default-splitter">
    <ejs-splitter id='splitter' ref='splitterObj'  width='600px' height='200px'>
        <e-panes>
            <e-pane :content='content1' size ='200px'></e-pane>
            <e-pane :content='content2' size ='200px'></e-pane>
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
    template: `<div>Left pane</div>`,
    data() {
        return {
            data: {}
        };
    }
});

var contentVue2 = Vue.component("contentTemp2", {
    template: `<div>Middle pane</div>`,
    data() {
        return {
            data: {}
        };
    }
});

var contentVue3 = Vue.component("contentTemp3", {
    template: `<div>Right pane</div>`,
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
    text-align: center;
    margin: 65px auto;
}
.content {
  justify-content: center;
  text-align: center;
  align-items: center;
}

.e-splitter {
    margin: 0 auto;
}

.e-pane {
    align-items: center;
    display: grid;
}
</style>

```

{% endtab %}

{% tab template="splitter/resize-min-max" %}

```html

<template>
<div id="app" class="col-lg-12 control-section default-splitter">
    <ejs-splitter id='splitter' ref='splitterObj'  width='600px' height='200px'>
        <e-panes>
            <e-pane :content='content1' size ='30%'></e-pane>
            <e-pane :content='content2' size ='40%'></e-pane>
            <e-pane :content='content3' size ='30%'></e-pane>
        </e-panes>
    </ejs-splitter>
</div>
</template>
<script>
import Vue from "vue";
import { SplitterPlugin } from '@syncfusion/ej2-vue-layouts';

Vue.use(SplitterPlugin);
var contentVue1 = Vue.component("contentTemp1", {
    template: `<div>Left pane</div>`,
    data() {
        return {
            data: {}
        };
    }
});

var contentVue2 = Vue.component("contentTemp2", {
    template: `<div>Middle pane</div>`,
    data() {
        return {
            data: {}
        };
    }
});

var contentVue3 = Vue.component("contentTemp3", {
    template: `<div>Right pane</div>`,
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
    text-align: center;
    margin: 65px auto;
}
.content {
  justify-content: center;
  text-align: center;
  align-items: center;
}

.e-splitter {
    margin: 0 auto;
}

.e-pane {
    align-items: center;
    display: grid;
}
</style>

```

{% endtab %}