---
title: " Chart Legend | Vue "

component: "Chart"

description: "Chart legend provides information about the series rendered in the chart.It has different alignment, shapes and customization properties. "
---

# Legend

Legend provides information about the series rendered in the chart which can be customized  using legend properties.

## Position and Alignment

By using the [`position`](../api/chart/legendSettings/#position) property, you can position the legend
at left, right, top or bottom of the chart. The legend is positioned at the bottom of the chart, by default.

{% tab template="chart/axis/category" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :legendSettings='legendSettings'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='silver' name='Silver'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='bronze' name='Bronze'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, Legend } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { country: "USA", gold: 50, silver: 70, bronze: 45 },
                { country: "China", gold: 40, silver: 60, bronze: 55 },
                { country: "Japan", gold: 70, silver: 60, bronze: 50 },
                { country: "Australia", gold: 60, silver: 56, bronze: 40 },
                { country: "France", gold: 50, silver: 45, bronze: 35 },
                { country: "Germany", gold: 40, silver: 30, bronze: 22 },
                { country: "Italy", gold: 40, silver: 35, bronze: 37 },
                { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
              ],
        primaryXAxis: {
           valueType: 'Category',
           title: 'Countries'
        },
        legendSettings: {
                visible: true,
                position: 'Top'
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, Legend ]
  }
};
</script>
<style>
 #container {
     height: 350px;
 }
</style>
```

{% endtab %}

* Custom position helps you to position the legend anywhere in the chart using x, y coordinates.

{% tab template="chart/axis/category" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :legendSettings='legendSettings'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='silver' name='Silver'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='bronze' name='Bronze'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, Legend } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { country: "USA", gold: 50, silver: 70, bronze: 45 },
                { country: "China", gold: 40, silver: 60, bronze: 55 },
                { country: "Japan", gold: 70, silver: 60, bronze: 50 },
                { country: "Australia", gold: 60, silver: 56, bronze: 40 },
                { country: "France", gold: 50, silver: 45, bronze: 35 },
                { country: "Germany", gold: 40, silver: 30, bronze: 22 },
                { country: "Italy", gold: 40, silver: 35, bronze: 37 },
                { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
              ],
        primaryXAxis: {
           valueType: 'Category',
           title: 'Countries'
        },
        legendSettings: {
                visible: true,
                position: 'Custom',
                location: { x: 200, y: 40 }
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, Legend ]
  }
};
</script>
<style>
#container {
     height: 350px;
 }
</style>
```

{% endtab %}

<!-- markdownlint-disable MD036 -->

**Legend Alignment**

<!-- markdownlint-disable MD036 -->

You can align the legend as `center`, `far` or `near` to the chart using
[`alignment`](../api/chart/legendSettings/#alignment) property.

{% tab template="chart/axis/category" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :legendSettings='legendSettings'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='silver' name='Silver'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='bronze' name='Bronze'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, Legend } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { country: "USA", gold: 50, silver: 70, bronze: 45 },
                { country: "China", gold: 40, silver: 60, bronze: 55 },
                { country: "Japan", gold: 70, silver: 60, bronze: 50 },
                { country: "Australia", gold: 60, silver: 56, bronze: 40 },
                { country: "France", gold: 50, silver: 45, bronze: 35 },
                { country: "Germany", gold: 40, silver: 30, bronze: 22 },
                { country: "Italy", gold: 40, silver: 35, bronze: 37 },
                { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
              ],
        primaryXAxis: {
           valueType: 'Category',
           title: 'Countries'
        },
        legendSettings: {
                visible: true, position: 'Top', alignment: 'Near'
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, Legend ]
  }
};
</script>
<style>
 #container {
     height: 350px;
 }
</style>
```

{% endtab %}

## Customization

To change the legend icon shape, you can use [`legendShape`](../api/chart/legendShape/#legendshape) property
in the [`series`](../api/chart/series/). By default legend icon shape is `seriesType`.

{% tab template="chart/axis/category" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :legendSettings='legendSettings'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold' legendShape='Circle'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='silver' name='Silver' legendShape='SeriesType'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='bronze' name='Bronze' legendShape='Rectangle'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, Legend } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { country: "USA", gold: 50, silver: 70, bronze: 45 },
                { country: "China", gold: 40, silver: 60, bronze: 55 },
                { country: "Japan", gold: 70, silver: 60, bronze: 50 },
                { country: "Australia", gold: 60, silver: 56, bronze: 40 },
                { country: "France", gold: 50, silver: 45, bronze: 35 },
                { country: "Germany", gold: 40, silver: 30, bronze: 22 },
                { country: "Italy", gold: 40, silver: 35, bronze: 37 },
                { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
              ],
        primaryXAxis: {
           valueType: 'Category',
           title: 'Countries'
        },
        legendSettings: {
                visible: true
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, Legend ]
  }
};
</script>
<style>
 #container {
     height: 350px;
 }
</style>
```

{% endtab %}

**Legend Size**

By default, legend takes 20% - 25% of the chart's height horizontally, when it is placed on top or bottom position and 20% - 25% of the
chart's width vertically, when placed on left or right position of the chart. You can change this default legend size by using the
[`width`](../api/chart/legendSettings/#width) and [`height`](../api/chart/legendSettings/#height) property of the `legendSettings`.

{% tab template="chart/axis/category" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :legendSettings='legendSettings'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold' legendShape='Circle'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='silver' name='Silver' legendShape='SeriesType'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='bronze' name='Bronze' legendShape='Rectangle'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, Legend } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { country: "USA", gold: 50, silver: 70, bronze: 45 },
                { country: "China", gold: 40, silver: 60, bronze: 55 },
                { country: "Japan", gold: 70, silver: 60, bronze: 50 },
                { country: "Australia", gold: 60, silver: 56, bronze: 40 },
                { country: "France", gold: 50, silver: 45, bronze: 35 },
                { country: "Germany", gold: 40, silver: 30, bronze: 22 },
                { country: "Italy", gold: 40, silver: 35, bronze: 37 },
                { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
              ],
        primaryXAxis: {
           valueType: 'Category',
           title: 'Countries'
        },
        legendSettings: {
              visible: true, height: '100', width: '500'
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, Legend ]
  }
};
</script>
<style>
 #container {
     height: 350px;
 }
</style>
```

{% endtab %}

**Legend Item Size**

You can customize the size of the legend items by using the [`shapeHeight`](../api/chart/legendSettings/#shapeheight)
and [`shapeWidth`](../api/chart/legendSettings/#shapewidth) property.

{% tab template="chart/axis/category" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :legendSettings='legendSettings'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold' legendShape='Circle'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='silver' name='Silver' legendShape='Circle'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='bronze' name='Bronze' legendShape='Circle'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, Legend } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { country: "USA", gold: 50, silver: 70, bronze: 45 },
                { country: "China", gold: 40, silver: 60, bronze: 55 },
                { country: "Japan", gold: 70, silver: 60, bronze: 50 },
                { country: "Australia", gold: 60, silver: 56, bronze: 40 },
                { country: "France", gold: 50, silver: 45, bronze: 35 },
                { country: "Germany", gold: 40, silver: 30, bronze: 22 },
                { country: "Italy", gold: 40, silver: 35, bronze: 37 },
                { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
              ],
        primaryXAxis: {
           valueType: 'Category',
           title: 'Countries'
        },
        legendSettings: {
              visible: true, shapeHeight: 15, shapeWidth: 15
        }
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, Legend ]
  }
};
</script>
<style>
 #container {
     height: 350px;
 }
</style>
```

{% endtab %}

**Paging for Legend**

Paging will be enabled by default, when the legend items exceeds the legend bounds. You can view each legend
items by navigating between the pages using navigation buttons.

{% tab template="chart/axis/legend" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' :legendSettings='legendSettings'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='December 2007' width=2 :marker='marker'> </e-series>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y1' name='December 2008' width=2 :marker='marker1'> </e-series>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y2' name='December 2009' width=2 :marker='marker2'> </e-series>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y3' name='December 2010' width=2 :marker='marker3'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Category, Legend } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
              { x: 'WW', y: 12, y1: 22, y2: 38.3, y3: 50 },
              { x: 'EU', y: 9.9, y1: 26, y2: 45.2, y3: 63.6 },
              { x: 'APAC', y: 4.4, y1: 9.3, y2: 18.2, y3: 20.9 },
              { x: 'LATAM', y: 6.4, y1: 28, y2: 46.7, y3: 65.1 },
              { x: 'MEA', y: 30, y1: 45.7, y2: 61.5, y3: 73 },
              { x: 'NA', y: 25.3, y1: 35.9, y2: 64, y3: 81.4 }
              ],
        primaryXAxis: {
           title: 'Countries',
           valueType: 'Category', interval: 1,
           labelIntersectAction : 'Rotate45'
        },
        primaryYAxis: {
           title: 'Penetration (%)',
            rangePadding: 'None', labelFormat: '{value}%',
            minimum: 0, maximum: 90
        },
        legendSettings: {
            padding: 10, shapePadding: 10,
            visible: true, border: {
                width: 2, color: 'grey'
            },
            width: '200'
        },
        marker: {
                    visible: true,
                    width: 10, height: 10,
                    shape: 'Diamond'
                },
        marker1: {
                    visible: true,
                    width: 10, height: 10,
                    shape: 'Pentagon'
                },
        marker2: {
                    visible: true,
                    width: 10, height: 10,
                    shape: 'Triangle',
                },
        marker3: {
                    visible: true,
                    width: 10, height: 10,
                    shape: 'Circle'
                }
      title: "FB Penetration of Internet Audience"
    };
  },
  provide: {
    chart: [LineSeries, Category, Legend ]
  }
};
</script>
<style>
 #container {
     height: 350px;
 }
</style>
```

{% endtab %}

## Series Selection on Legend

By default, legend click enables you to collapse the series visibility.  On other hand, if you need to select
a series through legend click, disable the
[`toggleVisibility`](../api/chart/legendSettings/#togglevisibility).

{% tab template="chart/axis/category" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :legendSettings='legendSettings' selectionMode='Point' >
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold' legendShape='Circle'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='silver' name='Silver' legendShape='Circle'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='bronze' name='Bronze' legendShape='Circle'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, Legend, Selection } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { country: "USA", gold: 50, silver: 70, bronze: 45 },
                { country: "China", gold: 40, silver: 60, bronze: 55 },
                { country: "Japan", gold: 70, silver: 60, bronze: 50 },
                { country: "Australia", gold: 60, silver: 56, bronze: 40 },
                { country: "France", gold: 50, silver: 45, bronze: 35 },
                { country: "Germany", gold: 40, silver: 30, bronze: 22 },
                { country: "Italy", gold: 40, silver: 35, bronze: 37 },
                { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
              ],
        primaryXAxis: {
           valueType: 'Category',
           title: 'Countries'
        },
        legendSettings: {
             visible: true, toggleVisibility: false
        }
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, Legend, Selection ]
  }
};
</script>
<style>
 #container {
     height: 350px;
 }
</style>
```

{% endtab %}

## Enable Animation

You can customize the animation while clicking legend by setting enableAnimation as true or false using `enableAnimation` property in chart.

{% tab template="chart/axis/category" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :enableAnimation='enableAnimation' :legendSettings='legendSettings'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold' legendShape='Circle'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='silver' name='Silver' legendShape='Circle'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='bronze' name='Bronze' legendShape='Circle'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, Legend } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { country: "USA", gold: 50, silver: 70, bronze: 45 },
                { country: "China", gold: 40, silver: 60, bronze: 55 },
                { country: "Japan", gold: 70, silver: 60, bronze: 50 },
                { country: "Australia", gold: 60, silver: 56, bronze: 40 },
                { country: "France", gold: 50, silver: 45, bronze: 35 },
                { country: "Germany", gold: 40, silver: 30, bronze: 22 },
                { country: "Italy", gold: 40, silver: 35, bronze: 37 },
                { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
              ],
        primaryXAxis: {
           valueType: 'Category',
           title: 'Countries'
        },
        legendSettings: {
             visible: true, toggleVisibility: true
        }
      title: "Olympic Medals",
      enableAnimation: true
    };
  },
  provide: {
    chart: [ColumnSeries, Category, Legend ]
  }
};
</script>
<style>
#container {
     height: 350px;
 }
</style>
```

{% endtab %}

## Collapsing Legend Item

By default, series name will be displayed as legend. To skip the legend for a particular series, you can give empty string to the series name.

{% tab template="chart/axis/category" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :legendSettings='legendSettings'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold' legendShape='Circle'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='silver' name='Silver' legendShape='Circle'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='bronze' name='Bronze' legendShape='Circle'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, Legend } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { country: "USA", gold: 50, silver: 70, bronze: 45 },
                { country: "China", gold: 40, silver: 60, bronze: 55 },
                { country: "Japan", gold: 70, silver: 60, bronze: 50 },
                { country: "Australia", gold: 60, silver: 56, bronze: 40 },
                { country: "France", gold: 50, silver: 45, bronze: 35 },
                { country: "Germany", gold: 40, silver: 30, bronze: 22 },
                { country: "Italy", gold: 40, silver: 35, bronze: 37 },
                { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
              ],
        primaryXAxis: {
           valueType: 'Category',
           title: 'Countries'
        },
        legendSettings: {
             visible: true, toggleVisibility: true
        }
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, Legend ]
  }
};
</script>
<style>
  #container {
     height: 350px;
 }
</style>
```

{% endtab %}

## Legend Title

You can set title for legend using `title` property in `legendSettings`. You can also customize the `fontStyle`, `size`, `fontWeight`, `color`, `textAlignment`, `fontFamily`, `opacity` and `textOverflow` of legend title. `titlePosition` is used to set the legend position in `Top`, `Left` and `Right` position. `maximumTitleWidth` is used to set the width of the legend title. By default, it will be `100px`.

{% tab template="chart/axis/category" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :legendSettings='legendSettings'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='silver' name='Silver'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='bronze' name='Bronze'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, Legend } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { country: "USA", gold: 50, silver: 70, bronze: 45 },
                { country: "China", gold: 40, silver: 60, bronze: 55 },
                { country: "Japan", gold: 70, silver: 60, bronze: 50 },
                { country: "Australia", gold: 60, silver: 56, bronze: 40 },
                { country: "France", gold: 50, silver: 45, bronze: 35 },
                { country: "Germany", gold: 40, silver: 30, bronze: 22 },
                { country: "Italy", gold: 40, silver: 35, bronze: 37 },
                { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
              ],
        primaryXAxis: {
           valueType: 'Category',
        },
        legendSettings: {
                visible: true, title: 'Countries'
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, Legend ]
  }
};
</script>
<style>
 #container {
     height: 350px;
 }
</style>
```

{% endtab %}

## Arrow Page Navigation

By default, the page number will be enabled while legend paging. Now, you can disable that page number and also you can get left and right arrows for page navigation. You have to set `false` value to `enablePages` to get this support.

{% tab template="chart/axis/legend" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' :legendSettings='legendSettings'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='December 2007' width=2 :marker='marker'> </e-series>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y1' name='December 2008' width=2 :marker='marker1'> </e-series>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y2' name='December 2009' width=2 :marker='marker2'> </e-series>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y3' name='December 2010' width=2 :marker='marker3'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Category, Legend } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
              { x: 'WW', y: 12, y1: 22, y2: 38.3, y3: 50 },
              { x: 'EU', y: 9.9, y1: 26, y2: 45.2, y3: 63.6 },
              { x: 'APAC', y: 4.4, y1: 9.3, y2: 18.2, y3: 20.9 },
              { x: 'LATAM', y: 6.4, y1: 28, y2: 46.7, y3: 65.1 },
              { x: 'MEA', y: 30, y1: 45.7, y2: 61.5, y3: 73 },
              { x: 'NA', y: 25.3, y1: 35.9, y2: 64, y3: 81.4 }
              ],
        primaryXAxis: {
           title: 'Countries',
           valueType: 'Category', interval: 1,
           labelIntersectAction : 'Rotate45'
        },
        primaryYAxis: {
           title: 'Penetration (%)',
            rangePadding: 'None', labelFormat: '{value}%',
            minimum: 0, maximum: 90
        },
        legendSettings: {
            width: '180',
            enablePages: false
        },
        marker: {
                    visible: true,
                    width: 10, height: 10,
                    shape: 'Diamond'
                },
        marker1: {
                    visible: true,
                    width: 10, height: 10,
                    shape: 'Pentagon'
                },
        marker2: {
                    visible: true,
                    width: 10, height: 10,
                    shape: 'Triangle',
                },
        marker3: {
                    visible: true,
                    width: 10, height: 10,
                    shape: 'Circle'
                }
      title: "FB Penetration of Internet Audience"
    };
  },
  provide: {
    chart: [LineSeries, Category, Legend ]
  }
};
</script>
<style>
 #container {
     height: 350px;
 }
</style>
```

{% endtab %}

>Note: To use legend feature, we need to inject `Legend` into the `Provide`.