# Print and Export

## Print

To use the print functionality, we should inject the `Print` module using the `provide` section and set the [`allowPrint`](../api/treemap/#allowprint) property to **true**. The rendered treemap can be printed directly from the browser by calling the method [`print`](../api/treemap/#print).

{% tab template="treemap/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
    <button id="print" @click="clickPrint">Print</button>
        <ejs-treemap  ref="treemap" :allowPrint='allowPrint' :dataSource='dataSource' :weightValuePath='weightValuePath'
        :leafItemSettings='leafItemSettings'></ejs-treemap>
    </div>
</template>
<script>
import Vue from 'vue';
import { TreeMapPlugin, Print } from "@syncfusion/ej2-vue-treemap";
Vue.use(TreeMapPlugin);

export default {
  data: function() {
    return {
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
            labelFormat: '${State}<br>$${GDP} Trillion<br>(${percentage} %)',
            labelStyle: {
                color: '#000000'
            },
            border: {
                color: '#000000',
                width: 0.5
            },
            allowPrint: true
      }
    }
  },
  provide:{
    treemap:[Print]
  },
  methods: {
    clickPrint: function(args) {
         args.treemap.print();
   }
  }
}
</script>
```

{% endtab %}

## Export

### Image Export

To use the image export functionality, we should inject the `ImageExport` module using the `provide` section and set the [`allowImageExport`](../api/treemap/#allowimageexport) property to **true**. The rendered treemap can be exported as an image using the [`export`](../api/treemap/#export) method. The method requires two parameters: image type and file name. The treemap can be exported as an image in the following formats.

* JPEG
* PNG
* SVG

{% tab template="treemap/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
    <button id="export" @click="clickExport">Export</button>
        <ejs-treemap id="treemap" ref='treemap' :allowImageExport='allowImageExport' :dataSource='dataSource' :weightValuePath='weightValuePath' :leafItemSettings='leafItemSettings'></ejs-treemap>
    </div>
</template>
<script>
import Vue from 'vue';
import { TreeMapPlugin, ImageExport } from "@syncfusion/ej2-vue-treemap";
Vue.use(TreeMapPlugin);

export default {
  data: function() {
    return {
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
            labelFormat: '${State}<br>$${GDP} Trillion<br>(${percentage} %)',
            labelStyle: {
                color: '#000000'
            },
            border: {
                color: '#000000',
                width: 0.5
            },
            allowImageExport: true
      }
    }
  },
  provide:{
    treemap:[ImageExport]
  },
  methods: {
    clickExport: function(args) {
         args.treemap.export('PNG', 'TreeMap');
   }
  }
}
</script>
```

{% endtab %}

We can get the image file as base64 string for the JPEG and PNG formats. The treemap can be exported to image as a base64 string using the [`export`](../api/treemap/#export) method. There are four parameters required: image type, file name, orientation of the exported PDF document which must be set as **null** for image export and finally **allowDownload** which should be set as **false** to return base64 string.

{% tab template="treemap/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
    <button id="export" @click="clickExport">Export</button>
        <ejs-treemap id="treemap" ref='treemap' :allowImageExport='allowImageExport' :dataSource='dataSource' :weightValuePath='weightValuePath' :leafItemSettings='leafItemSettings'></ejs-treemap>
    </div>
</template>
<script>
import Vue from 'vue';
import { TreeMapPlugin, ImageExport } from "@syncfusion/ej2-vue-treemap";
Vue.use(TreeMapPlugin);

export default {
  data: function() {
    return {
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
            labelFormat: '${State}<br>$${GDP} Trillion<br>(${percentage} %)',
            labelStyle: {
                color: '#000000'
            },
            border: {
                color: '#000000',
                width: 0.5
            },
            allowImageExport: true
      }
    }
  },
  provide:{
    treemap:[ImageExport]
  },
  methods: {
    clickExport: function(args) {
         args.treemap.export('PNG', 'TreeMap', null,false
      ).then((data) => {
            var base64 = data;
            document.writeln(base64);
        });
   }
  }
}
</script>
```

{% endtab %}

### PDF Export

To use the PDF export functionality, we should inject the `PdfExport` module using the `provide` section and set the [`allowPdfExport`](../api/treemap/#allowpdfexport) property to **true**. The rendered treemap can be exported as PDF using the [`export`](../api/treemap/#export) method. The [`export`](../api/treemap/#export) method requires three parameters: file type, file name and orientation of the PDF document. The orientation setting is optional and "0" indicates portrait and "1" indicates landscape.

{% tab template="treemap/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
    <button id="export" @click="clickExport">export</button>
        <ejs-treemap id="treemap" ref='treemap' :allowPdfExport='allowPdfExport' :dataSource='dataSource' :weightValuePath='weightValuePath' :leafItemSettings='leafItemSettings'></ejs-treemap>
    </div>
</template>
<script>
import Vue from 'vue';
import { TreeMapPlugin, PdfExport } from "@syncfusion/ej2-vue-treemap";
Vue.use(TreeMapPlugin);

export default {
  data: function() {
    return {
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
            labelFormat: '${State}<br>$${GDP} Trillion<br>(${percentage} %)',
            labelStyle: {
                color: '#000000'
            },
            border: {
                color: '#000000',
                width: 0.5
            },
            allowPdfExport: true
      }
    }
  },
  provide:{
    treemap:[PdfExport]
  },
  methods: {
    clickExport: function(args) {
         args.treemap.export('PDF', 'TreeMap', 0);
   }
  }
}
</script>
```

{% endtab %}

>Note: The exporting of the treemap as base64 string is not supported in the PDF export.