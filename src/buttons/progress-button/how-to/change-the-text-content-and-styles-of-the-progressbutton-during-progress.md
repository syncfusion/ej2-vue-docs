---
title: "Change the text content and styles of the ProgressButton during progress"
component: "ProgressButton"
description: "Vue ProgressButton how to section, change text content and styles, hide spinner, customize progress."
---

# Change the text content and styles of the ProgressButton during progress

You can change the text content and styles of the ProgressButton during progress by changing the text content and the [`cssClass`](../../api/progress-button#cssClass) property at the [`begin`](../../api/progress-button#begin) and [`end`](../../api/progress-button#end) events.

{% tab template="progress-button/custom-progress", isDefaultActive=true %}

```html
<template>
 <ejs-progressbutton ref="progressbutton" :content="content"  duration=4000 :enableProgress="true" :cssClass="cssClass" :begin ="begin" :end="end"></ejs-progressbutton>
</template>

<script>
import Vue from 'vue';
import { ProgressButtonPlugin } from "@syncfusion/ej2-vue-splitbuttons";
import { enableRipple} from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ProgressButtonPlugin);

export default {
methods: {
    begin: function(args) {
        this.$refs.progressbutton.content = 'Uploading...';
        this.$refs.progressbutton.cssClass = 'e-hide-spinner e-info';
    },
    end: function(args) {
        this.$refs.progressbutton.content = 'Success...';
        this.$refs.progressbutton.cssClass = 'e-hide-spinner e-success';
       setTimeout(()=>{
             this.$refs.progressbutton.content = 'Upload';
             this.$refs.progressbutton.cssClass = 'e-hide-spinner';
        }, 500)
   }
},
    data () {
        return {
           content: "Upload",
           cssClass:   "e-hide-spinner"
    };
  }
}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
</style>
```

{% endtab %}