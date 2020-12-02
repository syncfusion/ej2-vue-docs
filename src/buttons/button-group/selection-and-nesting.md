---
title: "ButtonGroup Selection and Nesting"
component: "ButtonGroup"
description: "ButtonGroup supports single selection, multiple selection, nesting with dropdownbutton and splitbutton components."
---

# Selection and Nesting

## Selection

### Single selection

ButtonGroup supports radio type selection in which only one button can be selected. This can be achieved by adding input element
along with `id` attribute with its corresponding label along with `for` attribute inside the target element. In this ButtonGroup,
the type of the input element should be `radio` and `e-btn` is added to the `label` element.

The following example illustrates the single selection behavior in ButtonGroup,

{% tab template="button-group/getting-started", isDefaultActive=true %}

```html

<template>
  <div id='app'>
    <div class='e-btn-group'>
        <input type="radio" id="radioleft" name="align" value="left"/>
        <label class="e-btn" for="radioleft">Left</label>
        <input type="radio" id="radiomiddle" name="align" value="middle"/>
        <label class="e-btn" for="radiomiddle">Center</label>
        <input type="radio" id="radioright" name="align" value="right"/>
        <label class="e-btn" for="radioright">Right</label>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';

export default {
  name: 'app'
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
  #app {
   margin: 20px;
  }

  .e-btn-group {
    margin: 25px 5px 20px 20px;
   }
</style>

```

{% endtab %}

### Multiple selection

ButtonGroup supports checkbox type selection in which multiple button can be selected. This can be achieved by adding input element
with its corresponding label. In this ButtonGroup, the type of the input element should be `checkbox` and `e-btn` is added to
the `label` element.

The following example illustrates the multiple selection behaviour in ButtonGroup,

{% tab template="button-group/getting-started" %}

```html

<template>
  <div id='app'>
    <div class='e-btn-group'>
        <input type="checkbox" id="checkbold" name="font" value="bold"/>
        <label class="e-btn" for="checkbold">Bold</label>
        <input type="checkbox" id="checkitalic" name="font" value="italic" />
        <label class="e-btn" for="checkitalic">Italic</label>
        <input type="checkbox" id="checkline" name="font" value="underline"/>
        <label class="e-btn" for="checkline">Underline</label>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';

export default {
  name: 'app'
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
  #app {
   margin: 20px;
  }

  .e-btn-group {
    margin: 25px 5px 20px 20px;
  }
</style>

```

{% endtab %}

## Nesting

Nesting with other components can be possible in ButtonGroup. The following components can be nested in ButtonGroup.
* DropDownButton
* SplitButton

For nesting support, [`SplitButton dependencies`](./../split-button/getting-started#dependencies) should be configured and it should be added in
`system.config.js`.

### DropDownButton

To initialize DropDownButton component refer [`DropDownButton Getting Started documentation`](./../drop-down-button/getting-started).

In the following example, DropDownButton component is added by importing `DropDownButtonPlugin` from `ej2-vue-splitbuttons`.

{% tab template= "button-group/getting-started" %}

```html

<template>
  <div id='app'>
    <div class="e-btn-group">
        <div class='e-btn-group'>
            <ejs-button >HTML</ejs-button>
            <ejs-button >CSS</ejs-button>
            <ejs-button >Javascript</ejs-button>
            <ejs-dropdownbutton :items='items'>More</ejs-dropdownbutton>
        </div>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
import { DropDownButtonPlugin } from "@syncfusion/ej2-vue-splitbuttons";

Vue.use(ButtonPlugin);
Vue.use(DropDownButtonPlugin);

export default {
  name: 'app',
  data () {
        return {
            items:[
            {
                text: 'Learn SQL'
            },
            {
                text: 'Learn PHP'
            },
            {
                text: 'Learn Bootstrap'
            }]
        };
    }
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
  #app {
   margin: 20px;
  }

</style>

```

{% endtab %}

### SplitButton

To initialize SplitButton component refer [`SplitButton Getting Started documentation`](./../split-button/getting-started).

In the following example, SplitButton component is added by importing `SplitButtonPlugin` from `ej2-vue-splitbuttons`.

{% tab template= "button-group/getting-started" %}

```html

<template>
  <div id='app'>
    <div class="e-btn-group e-vertical">
        <div class='e-btn-group'>
            <ejs-button content='Cut'></ejs-button>
            <ejs-button content='Copy'></ejs-button>
            <ejs-splitbutton :items='items' content='Paste'></ejs-splitbutton>
        </div>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { SplitButtonPlugin  } from "@syncfusion/ej2-vue-splitbuttons";
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.use(ButtonPlugin);
Vue.use(SplitButtonPlugin );

export default {
  name: 'app',
  data () {
        return {
            items:[
            {
                text: 'Paste'
            },
            {
                text: 'Paste Text'
            },
            {
                text: 'Paste Special'
            }]
        };
    }
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
  #app {
   margin: 20px;
  }

</style>

```

{% endtab %}

## See Also

* [Show ButtonGroup selected state on initial render](./how-to/show-buttongroup-selected-state-on-initial-render)