---
title: "Header and Content"
component: "Card"
description: "This section explains how to create the Card control with header, title, subtitle, images, and content."
---

# Header and Content

## Header

The Card can be created with header title, sub title and images. For adding header you need to create `div` element with the class
`e-card-header` added.

Card provides below elements and corresponding class definitions to include header.

Elements   | Description
------------ | -------------
Caption | It is the wrapper element to include title and sub-title.
Image | It supports to include header images with the specified dimensions.

Class   | Description
------------ | -------------
`e-card-header-caption` | To group the title and subtitle within the header which acts as wrapper.
`e-card-header-title` |  Main title text with in the header.
`e-card-sub-title` | A sub-title within the header.
`e-card-header-image` | To include heading image within the header.
`e-card-corner` | To add rounded corner for the image.

### Title and Subtitle

For adding header to the Card , you need to create wrapper `div` element with `e-card-header-caption` class.

* Place the `div` element with `e-card-header-title` class inside the header caption for adding main title.

* Place the div element with `e-card-sub-title` class inside the header caption element for adding sub-title.

### Image

Card header has an option for adding images in the header. It is aligned with either before or after the header based on the HTML element
positioned in the header structure.

* The header image can be added by creating a `div` element with `e-card-header-image` class which can be placed before or after the header
caption wrapper element.

{% tab template="card/header-content/image", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div style="margin: 50px;">
        <div tabindex="0" class="e-card">
            <div class="e-card-header">
                <div class="e-card-header-image football e-card-corner"></div>
                <div class="e-card-header-caption">
                    <div class="e-card-header-title"> Laura Callahan</div>
                    <div class="e-card-sub-title">Sales Coordinator and Representative</div>
                </div>
            </div>
        </div>
        </div>
        <div style="margin-left: 50px;margin-top:30px">
        <div tabindex="0" class="e-card">
            <div class="e-card-header">
                <div class="e-card-header-caption">
                    <div class="e-card-header-title"> Laura Callahan</div>
                    <div class="e-card-sub-title">Sales Coordinator and Representative</div>
                </div>
                <div class="e-card-header-image football"></div>
            </div>
        </div>
        </div>
  </div>
</template>
<script>
import Vue from 'vue';

export default {
  name: 'app',
}
</script>
<style>
  @import '../../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css';

.e-card .e-card-header .e-card-header-image.football {
    background-image: url('./football.png');
}

.e-card {
    width: 300px
}
</style>
```

{% endtab %}

## Content

Content in Card holds texts, images, links and all possible HTML elements. Its adaptable within the Card root element.

* Create a `div` element with the class `e-card-content`.
* Place content `div` element in the Card root element or within any Card inner elements.

{% tab template="card/header-content/content", isDefaultActive=true %}

```html
<template>
  <div id="app">
     <div tabindex="0" class="e-card">
            <div class="e-card-header">
                <div class="e-card-header-image football"></div>
                <div class="e-card-header-caption">
                    <div class="e-card-header-title"> Laura Callahan</div>
                    <div class="e-card-sub-title">Sales Coordinator and Representative</div>
                </div>
            </div>
            <div class="e-card-content">
                Laura received a BA in psychology from the University of Washington. She has also completed a course in business French. She reads and writes French.
            </div>
        </div>
  </div>
</template>
<script>
import Vue from 'vue';
export default {
  name: 'app',
}
</script>
<style>
  @import '../../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css';

.e-card .e-card-header .e-card-header-image.football {
    background-image: url('./football.png');
}

.e-card {
    width: 300px
}
</style>
```

{% endtab %}