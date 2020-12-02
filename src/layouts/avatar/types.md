---
title: "Avatar Types and Styles"
component: "Avatar"
description: "Avatar, a CSS component supports many types of media formats used like image, SVG, initials, font icon & word for various application scenarios."
---

# Types and Styles

This section explains different types of avatar.

## Avatar size

The Essential JS 2 Avatar has the following predefined sizes that can be used with the `.e-avatar` class to change the appearance of the avatar.

| Class Name         | Description
| :-------------:    |:-------------:
| e-avatar-xlarge    | Displays xlarge size avatar.
| e-avatar-large     | Displays apply large size avatar.
| e-avatar           | Displays apply default size avatar.
| e-avatar-small     | Displays apply small size avatar.
| e-avatar-xsmall    | Displays apply xsmall size avatar.

{% tab template="avatar/size", isDefaultActive=true %}

```html
<template>
    <div id='element'>
        <span class="e-avatar e-avatar-xlarge"></span>
        <span class="e-avatar e-avatar-large"></span>
        <span class="e-avatar"></span>
        <span class="e-avatar e-avatar-small"></span>
        <span class="e-avatar e-avatar-xsmall"></span>
    </div>
</template>
<script>
import Vue from "vue";

export default {
  data() {
    return {};
  }
}
</script>
<style>
    @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-layouts/styles/material.css";
    #element {
        display: block;
        width: 300px;
        margin: 100px auto;
        border-radius: 3px;
    }

    .e-avatar {
        background-image: url(./pic01.png);
    }

</style>

```

{% endtab %}

## Avatar types

The types of Essential JS 2 avatar are:

* Default
* Circle

### Default

The default style of the avatar is rectangular shape with rounded corners, which can be applied from adding the modifier
class `.e-avatar` to the target element.

{% tab template="avatar/default", isDefaultActive=true %}

```html
<template>
    <div id='element'>
        <span class="e-avatar e-avatar-xlarge">RT</span>
        <span class="e-avatar e-avatar-large">RT</span>
        <span class="e-avatar">RT</span>
        <span class="e-avatar e-avatar-small">RT</span>
        <span class="e-avatar e-avatar-xsmall">RT</span>
    </div>
</template>
<script>
import Vue from "vue";

export default {
  data() {
    return {};
  }
}
</script>
<style>
    @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-layouts/styles/material.css";
    #element {
        display: block;
        width: 260px;
        margin: 100px auto;
        border-radius: 3px;
    }

</style>

```

{% endtab %}

### Circle

The circle avatar style can be applied by adding the modifier class `.e-avatar-circle` to the target element.

{% tab template="avatar/circle", isDefaultActive=true %}

```html
<template>
    <div id='element'>
        <span class="e-avatar e-avatar-xlarge e-avatar-circle">SJ</span>
        <span class="e-avatar e-avatar-large e-avatar-circle">SJ</span>
        <span class="e-avatar e-avatar-circle">SJ</span>
        <span class="e-avatar e-avatar-small e-avatar-circle">SJ</span>
        <span class="e-avatar e-avatar-xsmall e-avatar-circle">SJ</span>
    </div>
</template>
<script>
import Vue from "vue";

export default {
  data() {
    return {};
  }
}
</script>
<style>
    @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-layouts/styles/material.css";
    #element {
        display: block;
        width: 300px;
        margin: 100px auto;
        border-radius: 3px;
    }

</style>

```

{% endtab %}
