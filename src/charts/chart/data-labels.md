---
title: " Chart DataLabel | Vue "

component: "Chart"

description: "Data labels are names of the data points that are displayed on the x-axis of a chart and also used to highlight important data points"
---

# Data Labels

Data label can be added to a chart series by enabling the [`visible`](../api/chart/dataLabelSettings/#visible)
option in the dataLabel. By default, the labels will arrange smartly without overlapping.

{% tab template="chart/data-marker/datalabel" %}

```html
<template>
    <div id="app">
         <ejs-chart id= "container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
            <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' name='Warmest' :marker='marker'></e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, DataLabel } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
              { x: 'Jan', y: -7.1 }, { x: 'Feb', y: -3.7 },
              { x: 'Mar', y: 2 }, { x: 'Apr', y: 6.3 },
              { x: 'May', y: 13.3 }, { x: 'Jun', y: 18.0 },
              { x: 'Jul', y: 19.8 }, { x: 'Aug', y: 18.1 },
              { x: 'Sep', y: 13.1 }, { x: 'Oct', y: 4.1 },
              { x: 'Nov', y: -3.8 }, { x: 'Dec', y: -6.8 }
              ],
        primaryXAxis: {
           valueType: 'Category'
        },
        marker: {
                    //Data label for chart series
                    dataLabel: { visible: true }
                },
      title: "Alaska Weather Statistics - 2016"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, DataLabel]
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

>Note: To use datalabel feature, we need to inject `DataLabel` into the `provide`.

## Position

Using [`position`](../api/chart/dataLabelSettings/#position) property, you can place the label either on
`Top`, `Middle`,`Bottom` or `Outer` (outer is applicable for column and bar type series).

{% tab template="chart/data-marker/datalabel" %}

```html
<template>
    <div id="app">
         <ejs-chart id= "container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' name='Warmest' :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, DataLabel } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
              { x: 'Jan', y: -7.1 }, { x: 'Feb', y: -3.7 },
              { x: 'Mar', y: 2 }, { x: 'Apr', y: 6.3 },
              { x: 'May', y: 13.3 }, { x: 'Jun', y: 18.0 },
              { x: 'Jul', y: 19.8 }, { x: 'Aug', y: 18.1 },
              { x: 'Sep', y: 13.1 }, { x: 'Oct', y: 4.1 },
              { x: 'Nov', y: -3.8 }, { x: 'Dec', y: -6.8 }
              ],
        primaryXAxis: {
           valueType: 'Category'
        },
        marker: {
                  dataLabel: { visible: true, position: 'Middle' }
                },
      title: "Alaska Weather Statistics - 2016"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, DataLabel]
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

>Note: The position `Outer` is applicable for column and bar type series.

## Datalabel template

Label content can be formatted by using the template option. Inside the template, you can add the placeholder text
`${point.x}` and `${point.y}` to display corresponding data points x & y value.
Using [`template`](../api/chart/dataLabelSettings/#template) property, you can set data label template
in chart.

{% tab template="chart/data-marker/datalabel" %}

```html
<template>
    <div id="app">
         <ejs-chart id= "container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' name='Warmest' :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, DataLabel } from "@syncfusion/ej2-vue-charts";
    let contentVue = Vue.component("contentTemplate", {
  template: `<div><div>{{data.point.x}}</div><div>{{data.point.y}}</div></div>`,
  data() {
    return {
      data: {}
    };
  }
});
let contentTemplate = function() {
  return { template: contentVue };
};

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
              { x: 'Jan', y: -7.1 }, { x: 'Feb', y: -3.7 },
              { x: 'Mar', y: 2 }, { x: 'Apr', y: 6.3 },
              { x: 'May', y: 13.3 }, { x: 'Jun', y: 18.0 },
              { x: 'Jul', y: 19.8 }, { x: 'Aug', y: 18.1 },
              { x: 'Sep', y: 13.1 }, { x: 'Oct', y: 4.1 },
              { x: 'Nov', y: -3.8 }, { x: 'Dec', y: -6.8 }
              ],
        primaryXAxis: {
           valueType: 'Category'
        },
        marker: { dataLabel: { visible: true, position: 'Middle',
                  template: contentTemplate } },
      title: "Alaska Weather Statistics - 2016"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, DataLabel]
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

## Text Mapping

Text from the data source can be mapped using `name` property.

{% tab template="chart/data-marker/datalabel" %}

```html
<template>
    <div id="app">
         <ejs-chart id= "container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' name='Warmest' :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, DataLabel } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData:[{ x: 'Jan', y: 12, text: 'January : 12°C' }, { x: 'Feb', y: 8, text: 'February : 8°C' },
                  { x: 'Mar', y: 11, text: 'March : 11°C' }, { x: 'Apr', y: 6, text: 'April : 6°C' }],
        primaryXAxis: {
           valueType: 'Category'
        },
        marker: { dataLabel: { visible: true, name: 'text'} },
      title: "Alaska Weather Statistics - 2016"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, DataLabel]
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

## Margin

`margin` for data label can be applied to using `left`, `right`, `bottom` and `top` properties.

{% tab template="chart/data-marker/datalabel" %}

```html
<template>
    <div id="app">
         <ejs-chart id= "container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' name='Warmest' :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, DataLabel } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
              { x: 'Jan', y: -7.1 }, { x: 'Feb', y: -3.7 },
              { x: 'Mar', y: 2 }, { x: 'Apr', y: 6.3 },
              { x: 'May', y: 13.3 }, { x: 'Jun', y: 18.0 },
              { x: 'Jul', y: 19.8 }, { x: 'Aug', y: 18.1 },
              { x: 'Sep', y: 13.1 }, { x: 'Oct', y: 4.1 },
              { x: 'Nov', y: -3.8 }, { x: 'Dec', y: -6.8 }
              ],
        primaryXAxis: {
           valueType: 'Category'
        },
        marker: { dataLabel: { visible: true,border:{width: 1, color : 'red'},
                        margin:{
                            left:5,
                            right:5,
                            top:5,
                            bottom:5
                        } }
        },
      title: "Alaska Weather Statistics - 2016"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, DataLabel]
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

## DataLabel Rotation

Using `angle` property, you can rotate the data label by its given angle.

{% tab template="chart/data-marker/marker" %}

```html
<template>
    <div id="app">
         <ejs-chart id= "container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' name='Warmest' :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, DataLabel } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
              { x: 'Jan', y: -7.1 }, { x: 'Feb', y: -3.7 },
              { x: 'Mar', y: 2 }, { x: 'Apr', y: 6.3 },
              { x: 'May', y: 13.3 }, { x: 'Jun', y: 18.0 },
              { x: 'Jul', y: 19.8 }, { x: 'Aug', y: 18.1 },
              { x: 'Sep', y: 13.1 }, { x: 'Oct', y: 4.1 },
              { x: 'Nov', y: -3.8 }, { x: 'Dec', y: -6.8 }
              ],
        primaryXAxis: {
           valueType: 'Category'
        },
        marker: { dataLabel: { visible: true,border:{width: 1, color : 'red'},
                        margin:{
                            left:5,
                            right:5,
                            top:5,
                            bottom:5
                        }, angle: 45, enableRotation: true }
        },
      title: "Alaska Weather Statistics - 2016"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, DataLabel]
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

`stroke` and `border` of data label can be customized using `fill` and `border` properties. Rounded corners
can be customized using `rx` and `ry` properties.

{% tab template="chart/data-marker/datalabel" %}

```html
<template>
    <div id="app">
         <ejs-chart id= "container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' name='Warmest' :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, DataLabel } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
              { x: 'Jan', y: -7.1 }, { x: 'Feb', y: -3.7 },
              { x: 'Mar', y: 2 }, { x: 'Apr', y: 6.3 },
              { x: 'May', y: 13.3 }, { x: 'Jun', y: 18.0 },
              { x: 'Jul', y: 19.8 }, { x: 'Aug', y: 18.1 },
              { x: 'Sep', y: 13.1 }, { x: 'Oct', y: 4.1 },
              { x: 'Nov', y: -3.8 }, { x: 'Dec', y: -6.8 }
              ],
        primaryXAxis: {
           valueType: 'Category'
        },
        marker:{ dataLabel: { visible: true,
                        border:{width: 2, color : 'red'},
                        rx:10, ry: 10
                    }
        },
      title: "Alaska Weather Statistics - 2016"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, DataLabel]
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

>Note: `rx` and `ry` properties requires `border` values not to be null.

## Customizing Specific Point

You can also customize the specific marker and label using
[`pointRender`](../api/chart/iPointRenderEventArgs/) and
[`textRender`](../api/chart/iTextRenderEventArgs/) event.
 `pointRender` event allows you to change the shape, color and border for a point, whereas the `textRender` event
allows you to change the text for the point.

{% tab template="chart/data-marker/datalabel" %}

```html
<template>
    <div id="app">
         <ejs-chart id= "container" :title='title' :primaryXAxis='primaryXAxis' :pointRender='pointRender' :textRender='textRender'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' name='Warmest' :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, DataLabel } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
              { x: 'Jan', y: -7.1 }, { x: 'Feb', y: -3.7 },
              { x: 'Mar', y: 2 }, { x: 'Apr', y: 6.3 },
              { x: 'May', y: 13.3 }, { x: 'Jun', y: 18.0 },
              { x: 'Jul', y: 19.8 }, { x: 'Aug', y: 18.1 },
              { x: 'Sep', y: 13.1 }, { x: 'Oct', y: 4.1 },
              { x: 'Nov', y: -3.8 }, { x: 'Dec', y: -6.8 }
              ],
        primaryXAxis: {
           valueType: 'Category'
        },
        marker:{ dataLabel: { visible: true } },
      title: "Alaska Weather Statistics - 2016"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, DataLabel]
  },
  methods: {
      pointRender: function(args) {
       if (args.point.index === 6) {
                args.fill = 'red'
        }
  },
   textRender: function(args) {
      if (args.point.index === 6) {
                args.text = 'Maximum Temperature';
                args.color = 'red';
            }
  }
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
