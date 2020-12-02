---
title: "Globalization"
component: "Splitter"
description: "This section explains the globalization support of Syncfusion Splitter component."
---

# Globalization

## RTL

Specifies the direction of the Splitter component using the enableRtl property. For writing systems that require it like Arabic, Hebrew, etc., the direction can be switched to right-to-left.

The following code shows how to enable RTL behavior.

{% tab template="splitter/rtl" %}

``` html
<template>
    <div id="app" class="col-lg-12 control-section default-splitter">
        <ejs-splitter id='splitter' height='200px' enableRtl='true'>
            <e-panes>
                <e-pane content='Left Pane' size='200px'></e-pane>
                <e-pane content='Middle Pane' size='200px'></e-pane>
                <e-pane content='Right Pane' size='200px'></e-pane>
            </e-panes>
        </ejs-splitter>
    </div>
</template>
<script>
    import Vue from "vue";
    import { SplitterPlugin} from '@syncfusion/ej2-vue-layouts';
    Vue.use(SplitterPlugin);
    export default {
        name: 'app',
        data() {
            return {}
        }
    }
</script>

<style>
.e-pane {
    align-items: center;
    padding: 9px;
    display: flex;
}
    @import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";
</style>
```

{% endtab %}

## See Also

* [Different Layouts](./different-layouts)