# Icons Library

The Syncfusion Vue library provides the set of `base64` formatted font icons, that can be utilized in the web application.

## Steps to use icon library

1. Add the class name `e-icons` to the HTML element which needs to render the icon. This class contains the font-family and common property of font icons.

2. Add the icon class with corresponding icon content from the [available icons](#available-icons). For example, the below code snippet represents the search icon class.

    ```css
    .e-search:before{
        content:'\e993';
    }
    ```

3. Add `e-search` class name to the HTML element along with `e-icons` class.

    ```html
    <span class="e-icons e-search"></span>
    ```

    The below code snippet represents the complete example of icon usage.

    ```html
    <!doctype html>
    <html>
        <head>
            <title>Essential JS 2 </title>
            <meta name="viewport" content="width=device-width, initial-scale=1.0" charset="utf-8"  />
            <link href="./node_modules/@syncfusion/ej2/material.css" rel="stylesheet" />
            <style>
                .e-search:before{
                    content:'\e993';
                }
                .e-upload:before{
                    content: '\e725';
                }
                .e-font:before{
                    content: '\e34c';
                }
            </style>
        </head>
        <body>
            <div class="icons">
                <ul>
                    <li><span class="e-icons e-search"></span></li>
                    <li><span class="e-icons e-settings"></span></li>
                    <li><span class="e-icons e-upload"></span></li>
                    <li><span class="e-icons e-font"></span></li>
                </ul>
            </div>
        </body>
    </html>
    ```

## Customization

* The Syncfusion icon library can customize its color and size by overriding the `e-icons` class.

    ```html
    <!doctype html>
    <html>
        <head>
            <title>Essential JS 2 </title>
            <meta name="viewport" content="width=device-width, initial-scale=1.0" charset="utf-8"  />
            <link href="./node_modules/@syncfusion/ej2/material.css" rel="stylesheet" />
            <style>
                .e-icons{
                    color: #00ffff;
                    font-size: 26px;
                }
                .e-search:before{
                    content: '\e993';
                }
                .e-upload:before{
                    content: '\e725';
                }
                .e-font:before{
                    content: '\e34c';
                }
            </style>
        </head>

        <body>
            <div class="icons">
                <ul>
                    <li><span class="e-icons e-search"></span></li>
                    <li><span class="e-icons e-settings"></span></li>
                    <li><span class="e-icons e-upload"></span></li>
                    <li><span class="e-icons e-font"></span></li>
                </ul>
            </div>
        </body>
    </html>
    ```

## Available Icons

The complete package of Essential JS 2 icons is listed in the following table. The corresponding icon content can be referred in the content section.

<!-- markdownlint-disable MD033 -->

### Material

<iframe class="doc-sample-frame" src="https://ej2.syncfusion.com/products/icons/material/demo.html" style="height:1000px;"></iframe>

### Fabric

<iframe class="doc-sample-frame" src="https://ej2.syncfusion.com/products/icons/fabric/demo.html" style="height:1000px;"></iframe>

### Bootstrap

<iframe class="doc-sample-frame" src="https://ej2.syncfusion.com/products/icons/bootstrap/demo.html" style="height:1000px;"></iframe>

### Bootstrap 4

<iframe class="doc-sample-frame" src="https://ej2.syncfusion.com/products/icons/bootstrap4/demo.html" style="height:1000px;"></iframe>

### High Contrast

<iframe class="doc-sample-frame" src="https://ej2.syncfusion.com/products/icons/highcontrast/demo.html" style="height:1000px;"></iframe>