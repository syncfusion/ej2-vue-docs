---
title: " Print And Export in Vue Maps control | Syncfusion "

component: "Maps"

description: "Learn here all about Print And Export feature of Syncfusion Vue Maps control and more."
---

# Print and Export in Vue Maps control

## Print

The rendered Maps can be printed directly from the browser by calling the [`print`](../api/maps#print) method. To use the print functionality, **Print** module must be injected into the Maps using **provide** section and set the [`allowPrint`](../api/maps/mapsModel/#allowprint) property to **true**. The following code snippet demonstrates injecting the Print module into the Maps component.

```html
<template>
    <ejs-maps id='maps'></ejs-maps>
</template>
<script>
export default ({
    data() {
        return{ };
    },
provide: {
    maps: [Print]
}
</script>
});
```

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html

<template>
    <div id="app">
        <button id="print" @click="clickPrint">Print</button>
        <ejs-maps id='container' :allowPrint='allowPrint' ref="maps" height='450px' width='500px'>
            <e-layers>
                <e-layer :shapeData='shapeData' :dataLabelSettings='dataLabelSettings' :shapeSettings='shapeSettings' :tooltipSettings='tooltipSettings' ></e-layer>
            </e-layers>
        </ejs-maps>
    </div>
</template>
<script>
import Vue from 'vue';
import { MapsPlugin, MapsTooltip, DataLabel, Print } from '@syncfusion/ej2-vue-maps';
import { usMap } from './usa.js';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
Vue.use(MapsPlugin,ButtonPlugin);
export default {
data () {
    return {
        dataLabelSettings: {
            visible: true,
            labelPath: 'name',
            smartLabelMode: 'Trim'
        },
        shapeData: usMap,
        shapeSettings: {
            autofill: true
        },
        tooltipSettings: {
            visible: true,
            valuePath: 'name'
        },
        allowPrint: true
    }
},
provide: {
    maps: [MapsTooltip, DataLabel, Print]
},
methods: {
    clickPrint: function(args) {
        let map=document.getElementById('container');
        map.ej2_instances[0].print();
    }
}
}
</script>
```

{% endtab %}

## Export

### Image Export

To use the image export functionality in Maps, **ImageExport** module must be injected into the Maps using **provide** section and set the [`allowImageExport`](../api/maps/#allowimageexport) property to **true**.

```html
<template>
    <ejs-maps id='maps'></ejs-maps>
</template>
<script>
export default ({
    data() {
        return{ };
    },
provide: {
    maps: [ImageExport]
}
</script>
});
```

The rendered Maps can be exported as an image using the [`export`](../api/maps#export) method. The method requires two parameters: image type and file name. The Maps can be exported as an image in the following formats.

* JPEG
* PNG
* SVG

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <button id="export" @click="clickExport">Export</button>
        <ejs-maps  id='container' :allowImageExport='allowImageExport' ref='maps' height='450px' width='500px'>
            <e-layers>
                <e-layer :shapeData='shapeData' :markerSettings='markerSettings' :shapeSettings='shapeSettings'></e-layer>
            </e-layers>
        </ejs-maps>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, MapsTooltip, Marker, ImageExport} from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use( MapsPlugin );
export default {
data () {
    return {
        shapeData: world_map,
        shapeSettings: { fill: 'lightgrey', border: { color: 'black', width: 0.1 } },
        allowImageExport: true,
        markerSettings: [
            {
                animationDuration: 0,
                visible: true,
                dataSource: [
                    { longitude: 116.5703749, latitude: 40.4319077, name: 'The Great Wall of China, China ' },
                    { longitude: 35.4443622, latitude: 30.3284544, name: 'Petra, Jorden' },
                    { longitude: 78.0421552, latitude: 27.1750151, name: 'Taj Mahal, Agra, India' },
                    { longitude: 12.4922309, latitude: 41.8902102, name: 'The Roman Colosseum, Rome, Italy' },
                    { longitude: -88.5677826, latitude: 20.6842849, name: 'The Chichen Itza, Mexico' },
                    { longitude: -72.5449629, latitude: -13.1631412, name: 'Machu Picchu, Peru' },
                    { longitude: -43.2104872, latitude: -22.951916, name: 'Christ Redeemer, Rio de janeiro, Brazil'}
                ],
                shape: 'Balloon',
                fill: '#E13E40',
                height: 20,
                width: 15,
                tooltipSettings: {
                    visible: true,
                    valuePath: 'name'
                }
            }
        ]
    }
},
provide: {
    maps: [Marker, MapsTooltip, ImageExport]
},
methods: {
     clickExport: function(args) {
        let map = document.getElementById('container');
        map.ej2_instances[0].export("PNG", "Maps");
    }
}
};
</script>
```

{% endtab %}

### Exporting Maps as base 64 string of the file

The image can be exported as base64 string for the JPEG and PNG formats. The rendered Maps can be exported to image as a base64 string using the [`export`](../api/maps/#export) method. There are four parameters required: image type, file name, orientation of the exported PDF document which must be set as **null** for image export and finally **allowDownload** which should be set as **false** to return base64 string.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <button id="export" @click="clickExport">Export</button>
        <ejs-maps  id='container' :allowImageExport='allowImageExport' ref='maps' height='450px' width='500px'>
            <e-layers>
                <e-layer :shapeData='shapeData' :markerSettings='markerSettings' :shapeSettings='shapeSettings'></e-layer>
            </e-layers>
        </ejs-maps>
        <div id="data"></data>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, MapsTooltip, Marker, ImageExport} from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use( MapsPlugin );
export default {
data () {
    return {
        shapeData: world_map,
        shapeSettings: { fill: 'lightgrey', border: { color: 'black', width: 0.1 } },
        allowImageExport: true,
        markerSettings: [
            {
                animationDuration: 0,
                visible: true,
                dataSource: [
                    { longitude: 116.5703749, latitude: 40.4319077, name: 'The Great Wall of China, China ' },
                    { longitude: 35.4443622, latitude: 30.3284544, name: 'Petra, Jorden' },
                    { longitude: 78.0421552, latitude: 27.1750151, name: 'Taj Mahal, Agra, India' },
                    { longitude: 12.4922309, latitude: 41.8902102, name: 'The Roman Colosseum, Rome, Italy' },
                    { longitude: -88.5677826, latitude: 20.6842849, name: 'The Chichen Itza, Mexico' },
                    { longitude: -72.5449629, latitude: -13.1631412, name: 'Machu Picchu, Peru' },
                    { longitude: -43.2104872, latitude: -22.951916, name: 'Christ Redeemer, Rio de janeiro, Brazil'}
                ],
                shape: 'Balloon',
                fill: '#E13E40',
                height: 20,
                width: 15,
                tooltipSettings: {
                    visible: true,
                    valuePath: 'name'
                }
            }
        ]
    }
},
provide: {
    maps: [Marker, MapsTooltip, ImageExport]
},
methods: {
     clickExport: function(args) {
        let map=document.getElementById('container');
        map.ej2_instances[0].export("PNG","Maps",null,false).then((data) => {
            document.getElementById('data').innerHTML = data;
        });
    }
}
}
</script>
```

{% endtab %}

### PDF Export

To use the PDF export functionality in Maps, **PdfExport** module must be injected into the Maps using **provide** section and set the [`allowPdfExport`](../api/maps/mapsModel/#allowpdfexport) property to **true**.

```html
<template>
    <ejs-maps id='maps'></ejs-maps>
</template>
<script>
export default ({
    data() {
        return{ };
    },
provide: {
    maps: [PdfExport]
}
</script>
});
```

The rendered Maps can be exported as PDF using the [`export`](../api/maps#export) method. The [`export`](../api/maps#export) method requires three parameters: file type, file name and orientation of the PDF document. The orientation setting is optional and **0** indicates portrait and **1** indicates landscape.

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <button id="export" @click="clickExport">export</button>
        <ejs-maps  id='container' :allowPdfExport='allowPdfExport' ref='maps' height='450px' width='500px'>
            <e-layers>
                <e-layer :shapeData='shapeData' :markerSettings='markerSettings' :shapeSettings='shapeSettings'></e-layer>
            </e-layers>
        </ejs-maps>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, MapsTooltip, Marker, PdfExport} from '@syncfusion/ej2-vue-maps';
import { world_map } from './world-map.js';
Vue.use( MapsPlugin );
export default {
data () {
    return {
        shapeData: world_map,
        shapeSettings: { fill: 'lightgrey', border: { color: 'black', width: 0.1 } },
        allowPdfExport: true,
        markerSettings: [
            {
                animationDuration: 0,
                visible: true,
                dataSource: [
                    { longitude: 116.5703749, latitude: 40.4319077, name: 'The Great Wall of China, China ' },
                    { longitude: 35.4443622, latitude: 30.3284544, name: 'Petra, Jorden' },
                    { longitude: 78.0421552, latitude: 27.1750151, name: 'Taj Mahal, Agra, India' },
                    { longitude: 12.4922309, latitude: 41.8902102, name: 'The Roman Colosseum, Rome, Italy' },
                    { longitude: -88.5677826, latitude: 20.6842849, name: 'The Chichen Itza, Mexico' },
                    { longitude: -72.5449629, latitude: -13.1631412, name: 'Machu Picchu, Peru' },
                    { longitude: -43.2104872, latitude: -22.951916, name: 'Christ Redeemer, Rio de janeiro, Brazil'}
                ],
                shape: 'Balloon',
                fill: '#E13E40',
                height: 20,
                width: 15,
                tooltipSettings: {
                    visible: true,
                    valuePath: 'name'
                }
            }
        ]
    }
},
provide: {
    maps: [Marker, MapsTooltip, PdfExport]
},
methods: {
     clickExport: function(args) {
        let map=document.getElementById('container');
        map.ej2_instances[0].export("PDF", "Maps", 0);
    }
}
}
</script>
```

{% endtab %}

>The exporting of the Maps as base64 string is not supported for the PDF export.

### Export the tile Maps

The rendered Maps with providers such as OSM, Bing and Google static Maps can be exported using the [`export`](../api/maps/#export) method. It supports the following export formats.

* JPEG
* PNG
* PDF

{% tab template= "maps/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <button id="print" @click="clickPrint">Print</button>
        <button id="export" @click="clickExport">export</button>
        <ejs-maps  id='container' :allowPdfExport='allowPdfExport'
        :allowPrint='allowPrint' :allowImageExport='allowImageExport' ref='maps' :titleSettings='titleSettings'>
            <e-layers>
                <e-layer layerType='OSM'></e-layer>
            </e-layers>
        </ejs-maps>
    </div>
</template>

<script>
import Vue from 'vue';
import { MapsPlugin, ImageExport, PdfExport, Print } from '@syncfusion/ej2-vue-maps';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
import { enableRipple } from '@syncfusion/ej2-base';
Vue.use( MapsPlugin, ButtonPlugin);
enableRipple(true);
export default {
data () {
    return {
        titleSettings: {
            text: 'OSM'
        },
        allowImageExport: true,
        allowPdfExport: true,
        allowPrint: true
    }
},
provide: {
    maps: [ImageExport, PdfExport, Print]
},
methods: {
    clickExport: function(args) {
      this.$refs.maps.ej2Instances.export("PNG","GAUGE");
    },
    clickPrint:function(args){
        this.$refs.maps.ej2Instances.print();
    }
}
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';

</style>
```

{% endtab %}