# Types

The ChipList control has the following types.

* Input Chip
* Choice Chip
* Filter Chip
* Action Chip

## Input Chip

Input Chip holds information in compact form. It converts user input into chips.

{% tab template="chips/default", isDefaultActive=true %}

```html
<template>
    <ejs-chiplist id="chip">
        <e-chips>
            <e-chip text="Andrew"></e-chip>
            <e-chip text="Janet"></e-chip>  
            <e-chip text="Laura"></e-chip>
            <e-chip text="Margaret"></e-chip>
        </e-chips>
    </ejs-chiplist>
</template>

<script>
import Vue from 'vue';
import { ChipListPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.use(ChipListPlugin);

export default {}
</script>

```

{% endtab %}

## Choice Chip

Choice Chip allows you to select a single chip from the set of ChipList/ChipCollection. It can be enabled by setting the `selection` property to `Single`.

{% tab template="chips/default", isDefaultActive=true %}

```html
<template>
    <ejs-chiplist id="chip" selection="Single">
        <e-chips>
            <e-chip text="Small"></e-chip>
            <e-chip text="Medium"></e-chip>
            <e-chip text="Large"></e-chip>
            <e-chip text="Extra Large"></e-chip>
        </e-chips>
    </ejs-chiplist>
</template>

<script>
import Vue from 'vue';
import { ChipListPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.use(ChipListPlugin);

export default {}
</script>

```

{% endtab %}

## Filter Chip

Filter Chip allows you to select a multiple chip from the set of ChipList/ChipCollection. It can be enabled by setting the `selection` property to `Multiple`.

{% tab template="chips/default", isDefaultActive=true %}

```html
<template>
    <ejs-chiplist id="chip" selection="Multiple">
        <e-chips>
            <e-chip text="Chai"></e-chip>
            <e-chip text="Chang"></e-chip>
            <e-chip text="Aniseed Syrup"></e-chip>
            <e-chip text="Ikura"></e-chip>
        </e-chips>
    </ejs-chiplist>
</template>

<script>
import Vue from 'vue';
import { ChipListPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.use(ChipListPlugin);

export default {}
</script>

```

{% endtab %}

## Action Chip

The Action Chip triggers the event like click or delete, which helps doing action based on the event.

{% tab template="chips/default", isDefaultActive=true %}

```html
<template>
    <ejs-chiplist id="chip" v-on:click.native="chipclick">
        <e-chips>
            <e-chip text="Send a text"></e-chip>
            <e-chip text="Set a remainder"></e-chip>
            <e-chip text="Read my emails"></e-chip>
            <e-chip text="Set alarm"></e-chip>
        </e-chips>
    </ejs-chiplist>
</template>

<script>
import Vue from 'vue';
import { ChipListPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.use(ChipListPlugin);

export default {
  methods: {
    chipclick: function(e) {
      alert('you have clicked ' + e.target.textContent);
    }
  }
}
</script>

```

{% endtab %}

### Deletable Chip

Deletable Chip allows you to delete a chip from ChipList/ChipCollection. It can be enabled by setting the `enableDelete` property to `true`.

{% tab template="chips/default", isDefaultActive=true %}

```html
<template>
    <ejs-chiplist id="chip" enableDelete="true">
        <e-chips>
            <e-chip text="Send a text"></e-chip>
            <e-chip text="Set a remainder"></e-chip>
            <e-chip text="Read my emails"></e-chip>
            <e-chip text="Set alarm"></e-chip>
        </e-chips>
    </ejs-chiplist>
</template>

<script>
import Vue from 'vue';
import { ChipListPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.use(ChipListPlugin);

export default {
  methods: {
    chipclick: function(e) {
      alert('you have clicked ' + e.target.textContent);
    }
  }
}
</script>

```

{% endtab %}