# Leaf Item

The leaf item defines a visualized data element. Leaf item does not contain child nodes, but contains parent node if it specifies the levels in tree map. Leaf nodes can be customized.

## Leaf label

Label is represented by item name or value. Label will be appeared by specifying the [`labelPath`] property. You can customize the label style using the [`labelStyle`] property.

{% tab template="treemap/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
        <ejs-treemap id="treemap" :height='height' :dataSource='dataSource' :weightValuePath='weightValuePath' :leafItemSettings='leafItemSettings'></ejs-treemap>
    </div>
</template>
<script>
import Vue from 'vue';
import { TreeMapPlugin } from "@syncfusion/ej2-vue-treemap";
Vue.use(TreeMapPlugin);

export default {
  data: function() {
    return {
    height:'350px',
     dataSource: [
        {State:"United States", GDP:17946, percentage:11.08, Rank:1},
    {State:"China", GDP:10866, percentage: 28.42, Rank:2},
    {State:"Japan", GDP:4123, percentage:-30.78, Rank:3},
    {State:"Germany", GDP:3355, percentage:-5.19, Rank:4},
    {State:"United Kingdom", GDP:2848, percentage:8.28, Rank:5},
    {State:"France", GDP:2421, percentage:-9.69, Rank:6},
    {State:"India", GDP:2073, percentage:13.65, Rank:7},
    {State:"Italy", GDP:1814, percentage:-12.45, Rank:8},
    {State:"Brazil", GDP:1774, percentage:-27.88, Rank:9},
    {State:"Canada", GDP:1550, percentage:-15.02, Rank:10}
    ],
    weightValuePath: 'GDP',
    leafItemSettings: {
            labelPath: 'State',
            labelStyle: {
                color: '#000000'
            },
            border: {
                color: '#000000',
                width: 0.5
            }
        },
    }
  }
}
</script>
```

{% endtab %}

<!-- markdownlint-disable MD036 -->

### Label position and format

You can position the label using the [`labelPosition`] property and format the text by specifying data values using the [`labelFormat`] property.

{% tab template="treemap/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
        <ejs-treemap id="treemap" :height='height' :dataSource='dataSource' :weightValuePath='weightValuePath' :leafItemSettings='leafItemSettings'></ejs-treemap>
    </div>
</template>
<script>
import Vue from 'vue';
import { TreeMapPlugin } from "@syncfusion/ej2-vue-treemap";
Vue.use(TreeMapPlugin);

export default {
  data: function() {
    return {
    height:'350px',
     dataSource: [
        {State:"United States", GDP:17946, percentage:11.08, Rank:1},
    {State:"China", GDP:10866, percentage: 28.42, Rank:2},
    {State:"Japan", GDP:4123, percentage:-30.78, Rank:3},
    {State:"Germany", GDP:3355, percentage:-5.19, Rank:4},
    {State:"United Kingdom", GDP:2848, percentage:8.28, Rank:5},
    {State:"France", GDP:2421, percentage:-9.69, Rank:6},
    {State:"India", GDP:2073, percentage:13.65, Rank:7},
    {State:"Italy", GDP:1814, percentage:-12.45, Rank:8},
    {State:"Brazil", GDP:1774, percentage:-27.88, Rank:9},
    {State:"Canada", GDP:1550, percentage:-15.02, Rank:10}
    ],
    weightValuePath: 'GDP',
    leafItemSettings: {
            labelPath: 'State',
            labelPosition:'TopCenter',
            labelFormat: '${State}<br>$${GDP} Trillion<br>(${percentage}',
        },
    }
  }
}
</script>
```

{% endtab %}

<!-- markdownlint-disable MD036 -->

### Label template and position

You can display both text and image in leaf node using the [`template`] property, which can be placed anywhere in node using the [`templatePosition`] property.

{% tab template="treemap/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
        <ejs-treemap id="treemap" :height='height' :dataSource='dataSource' :weightValuePath='weightValuePath' :leafItemSettings='leafItemSettings'></ejs-treemap>
    </div>
</template>
<script>
import Vue from 'vue';
import { TreeMapPlugin } from "@syncfusion/ej2-vue-treemap";
Vue.use(TreeMapPlugin);

export default {
  data: function() {
    return {
    height:'350px',
     dataSource: [
       { Sport: "Swimming", Gold: 16, GameImage: 'Swimming.svg', ItemHeight: "180px", ItemWidth: '180px' },
    { Sport: "Athletics", Gold: 13, GameImage: 'Athletics.svg', ItemHeight: "70px", ItemWidth: '70px' },
    { Sport: "Gymnastics", Gold: 4, GameImage: 'Gymnastics.svg', ItemHeight: "80px", ItemWidth: '80px' },
    { Sport: "Cycling", Gold: 2, GameImage: 'Cycling.svg', ItemHeight: "50px", ItemWidth: '50px' },
    { Sport: "Wrestling", Gold: 2, GameImage: 'Wrestling.svg', ItemHeight: "60px", ItemWidth: '50px' },
    { Sport: "Basketball", Gold: 2, GameImage: 'Basketball.svg', ItemHeight: "50px", ItemWidth: '50px' },
    { Sport: "Boxing", Gold: 1, GameImage: 'Boxing.svg', ItemHeight: "40px", ItemWidth: '30px' },
    { Sport: "Tennis", Gold: 1, GameImage: 'Tennis.svg', ItemHeight: "40px", ItemWidth: '40px' },
    { Sport: "Judo", Gold: 1, GameImage: 'Judo.svg', ItemHeight: "40px", ItemWidth: '40px' },
    { Sport: "Rowing", Gold: 1, GameImage: 'Rowing.svg', ItemHeight: "40px", ItemWidth: '40px' },
    { Sport: "Shooting", Gold: 1, GameImage: 'Shooting.svg', ItemHeight: "40px", ItemWidth: '40px' },
    { Sport: "Triathlon", Gold: 1, GameImage: 'Triathlon.svg', ItemHeight: "40px", ItemWidth: '40px' },
    { Sport: "Water polo", Gold: 1, GameImage: 'Water polo.svg', ItemHeight: "40px", ItemWidth: '40px' }
    ],
    weightValuePath: 'Gold',
    leafItemSettings: {
            labelPath: 'Sport',
            fill: '#993399'
        },
    }
  }
}
</script>
```

{% endtab %}

<!-- markdownlint-disable MD036 -->

## Item gap

The [`gap`] property is used to separate an item from another item. Each item rectangle is split into equal space with specified gap.

{% tab template="treemap/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
        <ejs-treemap id="treemap" :height='height' :dataSource='dataSource' :weightValuePath='weightValuePath' :leafItemSettings='leafItemSettings'></ejs-treemap>
    </div>
</template>
<script>
import Vue from 'vue';
import { TreeMapPlugin } from "@syncfusion/ej2-vue-treemap";
Vue.use(TreeMapPlugin);

export default {
  data: function() {
    return {
    height:'350px',
     dataSource: [
        {State:"United States", GDP:17946, percentage:11.08, Rank:1},
    {State:"China", GDP:10866, percentage: 28.42, Rank:2},
    {State:"Japan", GDP:4123, percentage:-30.78, Rank:3},
    {State:"Germany", GDP:3355, percentage:-5.19, Rank:4},
    {State:"United Kingdom", GDP:2848, percentage:8.28, Rank:5},
    {State:"France", GDP:2421, percentage:-9.69, Rank:6},
    {State:"India", GDP:2073, percentage:13.65, Rank:7},
    {State:"Italy", GDP:1814, percentage:-12.45, Rank:8},
    {State:"Brazil", GDP:1774, percentage:-27.88, Rank:9},
    {State:"Canada", GDP:1550, percentage:-15.02, Rank:10}
    ],
    weightValuePath: 'GDP',
    leafItemSettings: {
        labelPath: 'State',
            gap:20
        },
    }
  }
}
</script>
```

{% endtab %}
