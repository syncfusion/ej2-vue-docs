---
title: "Export"
component: "Diagram"
description: "Diagram exporting supports to export the diagram content as image/svg."
---

# Exporting

Diagram provides support to export its content as image/svg files.
The client-side method [`exportDiagram`](../api/diagram#exportDiagram) helps to export the diagram. The following code illustrates how to export the diagram as image.

>Note: To use Print and Export, you need to inject `PrintAndExport` in the diagram.

<!-- markdownlint-disable MD033 -->

```javascript
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            tool: DiagramTools.DrawOnce || DiagramTools.ZoomPan,
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        let options: IExportOptions = {};
        options.mode = 'Data';
        diagramInstance.exportDiagram(options);
    }
}
```

## Exporting options

Diagram provides support to export the desired region of the diagram to desired formats.

## File Name

[`FileName`](../api/diagram/iExportOptions#fileName-string) is the name of the file to be downloaded. By default, the file name is set to **Diagram**.

## Format

[`Format`](../api/diagram/iExportOptions#format-fileformat) is to specify the type/format of the exported file. By default, the diagram is exported as .jpg format. You can export diagram to the following formats:

* JPG
* PNG
* BMP
* SVG

```javascript
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            tool: DiagramTools.DrawOnce || DiagramTools.ZoomPan,
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        let options: IExportOptions = {};
        options.mode = 'Data';
        options.format = 'SVG';
        diagramInstance.exportDiagram(options);
    }
}
```

## Margin

[`Margin`](../api/diagram/iExportOptions#margin-marginmodel) specifies the amount of space that has to be left around the diagram.

<!-- markdownlint-disable MD033 -->

```javascript
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            tool: DiagramTools.DrawOnce || DiagramTools.ZoomPan,
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        let options: IExportOptions = {};
        options.mode = 'Data';
        options.margin = {
            left: 10,
            right: 10,
            top: 10,
            bottom: 10
        };
        options.fileName = 'format';
        options.format = 'SVG';
        diagramInstance.exportDiagram(options);
    }
}
```

## Mode

[`Mode`](../api/diagram/iExportOptions#mode-exportmodes) specifies whether the diagram is to be exported as files or as data (ImageURL/SVG). The exporting options are as follows:

* Data: Exports and downloads the diagram as image.
* Download: Exports the diagram as data of formats ImageURL/SVG.

For more information about the exporting modes, refer to Exporting Modes.

The following code example illustrates how to export the diagram as raw data.

```javascript
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            tool: DiagramTools.DrawOnce || DiagramTools.ZoomPan,
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        let options: IExportOptions = {};
        options.mode = 'Data';
        options.margin = {
            left: 10,
            right: 10,
            top: 10,
            bottom: 10
        };
        options.fileName = 'format';
        options.format = 'SVG';
        diagramInstance.exportDiagram(options);
    }
}
```

## Region

You can export any particular [`region`](../api/diagram/iExportOptions#region-diagramregions) of the diagram and the region is categorized as follows.

* Region that fits all nodes and connectors that are added to model.
* Region that fits all pages (single or multiple pages based on page settings).

For more information about region, refer to Regions.

The following code example illustrates how to export the region occupied by the diagram elements.

```javascript
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            tool: DiagramTools.DrawOnce || DiagramTools.ZoomPan,
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        let options: IExportOptions = {};
        options.mode = 'Data';
        options.margin = {
            left: 10,
            right: 10,
            top: 10,
            bottom: 10
        };
        options.fileName = 'format';
        options.format = 'SVG';
        options.region = 'Content';
        diagram.exportDiagram(options);
    }
}
```

## Custom bounds

Diagram provides support to export any specific region of the diagram by using [`bounds`](../api/diagram/iExportOptions#bounds-rect).

The following code example illustrates how to export the region occupied by the diagram elements.

```javascript
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            tool: DiagramTools.DrawOnce || DiagramTools.ZoomPan,
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        let options: IExportOptions = {};
        options.mode = 'Data';
        options.margin = {
            left: 10,
            right: 10,
            top: 10,
            bottom: 10
        };
        options.fileName = 'region';
        options.format = 'SVG';
        options.region = 'CustomBounds';
        options.bounds.x = 10;
        options.bounds.y = 10;
        options.bounds.height = 100;
        options.bounds.width = 100;
        diagramInstance.exportDiagram(options);
    }
}
```

## Export diagram with stretch option

Diagram provides support to export the diagram as image for [`stretch`](../api/diagram/iExportOptions#stretch-stretch) option. The exported images will be clearer but larger in file size.

The following code example illustrates how to export the region occupied by the diagram elements.

```javascript
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            tool: DiagramTools.DrawOnce || DiagramTools.ZoomPan,
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        let options: IExportOptions = {};
        options.mode = 'Data';
        options.margin = {
            left: 10,
            right: 10,
            top: 10,
            bottom: 10
        };
        options.fileName = 'region';
        options.format = 'SVG';
        options.region = 'Content';
        options.stretch = 'Stretch';
        diagram.exportDiagram(options);
    }
}
```

## Print

The client-side method [`print`](../api/diagram#print) helps to print the diagram as image.

| Name | Type | Description|
|-------- | -------- | -------- |
| region | enum | Sets the region of the diagram to be printed. |
| bounds | object | Prints any custom region of diagram. |
| stretch| enum | Resizes the diagram content to fill its allocated space and printed.|
| multiplePage | boolean | Prints the diagram into multiple pages. |
| pageWidth | number | Sets the page width of the diagram while printing the diagram into multiple pages. |
| pageHeight| number | Sets the page height of the diagram while printing the diagram into multiple pages.|
| pageOrientation | enum | Sets the orientation of the page. |

The following code example illustrates how to export the region occupied by the diagram elements.

```javascript
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            tool: DiagramTools.DrawOnce || DiagramTools.ZoomPan,
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        let options: IExportOptions = {};
        options.mode = 'Data';
        options.region = 'PageSettings';
        options.multiplePage = true;
        options.pageHeight = 300;
        options.pageWidth = 300;
        diagram.print(options);
    }
}
```