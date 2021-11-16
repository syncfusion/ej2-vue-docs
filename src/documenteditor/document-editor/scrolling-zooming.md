---
title: "Scrolling"
component: "DocumentEditor"
description: "Learn scrolling and zooming can be customized in JavaScript document editor."
---

# Scrolling

The Document Editor renders the document as page by page. You can scroll through the pages by mouse wheel or touch interactions. You can also scroll through the page by using ‘scrollToPage()’ method of Document Editor instance. Refer to the following code example.

{% tab template="document-editor/scrolling-zooming", isDefaultActive=false %}

{% raw %}

```html
<template>
      <div id="app">
          <ejs-documenteditor ref="documenteditor" height="370px" style="width: 100%;"></ejs-documenteditor>
      </div>
</template>
<script>
    import Vue from 'vue'
    import { DocumentEditorPlugin } from '@syncfusion/ej2-vue-documenteditor';

    Vue.use(DocumentEditorPlugin);

    export default {
        data: function() {
            return {
            };
        },
        mounted: function() {
                let defaultDocument: object = {
                    "sections": [
                        {
                            "blocks": [
                                {
                                    "paragraphFormat": {
                                        "styleName": "Normal"
                                    },
                                    "inlines": [
                                        {
                                            "text": "First page"
                                        }
                                    ]
                                }
                            ],
                            "headersFooters": {},
                        },
                        {
                            "blocks": [
                                {
                                    "paragraphFormat": {
                                        "styleName": "Normal"
                                    },
                                    "inlines": [
                                        {
                                            "text": "Second page"
                                        }
                                    ]
                                }
                            ],
                            "headersFooters": {},
                        }
                    ],
                    "characterFormat": {},
                    "paragraphFormat": {},
                    "background": {
                        "color": "#FFFFFFFF"
                    },
                    "styles": [
                        {
                            "type": "Paragraph",
                            "name": "Normal",
                            "next": "Normal"
                        },
                        {
                            "type": "Character",
                            "name": "Default Paragraph Font"
                        }
                    ]
            }
            this.$refs.documenteditor.open(JSON.stringify(defaultDocument));
            //Scroll to specified page.
            this.$refs.documenteditor.scrollToPage(2);
        }
    }
</script>
<style>
      @import "../../node_modules/@syncfusion/ej2-vue-documenteditor/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}

> Calling this method brings the specified page into view but doesn’t move selection. Hence this method will work by default. That is, it works even if selection is not enabled.

In case, if you wish to move the selection to any page in Document Editor and bring it into view, you can use ‘goToPage()’ method of selection instance. Refer to the following code example.

{% tab template="document-editor/scrolling-zooming", isDefaultActive=false %}

{% raw %}

```html
<template>
      <div id="app">
          <ejs-documenteditor ref="documenteditor" :enableSelection='true' :isReadOnly=false height="370px" style="width: 100%;"></ejs-documenteditor>
      </div>
</template>
<script>
    import Vue from 'vue'
    import { DocumentEditorPlugin, Selection } from '@syncfusion/ej2-vue-documenteditor';

    Vue.use(DocumentEditorPlugin);

    export default {
        data: function() {
            return {
            };
        },
        provide: {
            DocumentEditor : [Selection]
        },
        mounted: function() {
            let defaultDocument: object = {
                "sections": [
                    {
                        "blocks": [
                            {
                                "paragraphFormat": {
                                    "styleName": "Normal"
                                },
                                "inlines": [
                                    {
                                        "text": "First page"
                                    }
                                ]
                            }
                        ],
                        "headersFooters": {},
                    },
                    {
                        "blocks": [
                            {
                                "paragraphFormat": {
                                    "styleName": "Normal"
                                },
                                "inlines": [
                                    {
                                        "text": "Second page"
                                    }
                                ]
                            }
                        ],
                        "headersFooters": {},
                    },
                    {
                        "blocks": [
                            {
                                "paragraphFormat": {
                                    "styleName": "Normal"
                                },
                                "inlines": [
                                    {
                                        "text": "Third page"
                                    }
                                ]
                            }
                        ],
                        "headersFooters": {},
                    }
                ],
                "characterFormat": {},
                "paragraphFormat": {},
                "background": {
                    "color": "#FFFFFFFF"
                },
                "styles": [
                    {
                        "type": "Paragraph",
                        "name": "Normal",
                        "next": "Normal"
                    },
                    {
                        "type": "Character",
                        "name": "Default Paragraph Font"
                    }
                ]
            }
            this.$refs.documenteditor.open(JSON.stringify(defaultDocument));
            //Navigate to specified page.
            this.$refs.documenteditor.ej2Instances.selection.goToPage(3);
        }
    }
</script>
<style>
 @import "../../node_modules/@syncfusion/ej2-vue-documenteditor/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}

## Zooming

You can scale the contents in Document Editor ranging from 10% to 500% of the actual size. You can achieve this using mouse or touch interactions. You can also use ‘zoomFactor’ property of Document Editor instance. The value can be specified in a range from 0.1 to 5. Refer to the following code example.

```html
<template>
      <div id="app">
          <ejs-documenteditor ref="documenteditor" style="width: 100%;height: 100%;"></ejs-documenteditor>
      </div>
</template>
<script>
    import Vue from 'vue'
    import { DocumentEditorPlugin } from '@syncfusion/ej2-vue-documenteditor';

    Vue.use(DocumentEditorPlugin);

    export default {
        data: function() {
            return {
            };
        },
        mounted: function() {
            //Set zoom factor.
            this.$refs.documenteditor.zoomFactor = 3;
        }
    }
</script>
<style>
      @import "../../node_modules/@syncfusion/ej2-vue-documenteditor/styles/material.css";
</style>
```

## Page Fit Type

Apart from specifying the zoom factor as value, the Document Editor provides option to specify page fit options such as fit to full page or fit to page width. You can set this option using ‘fitPage’ method of Document Editor instance. Refer to the following code example.

```html
<template>
      <div id="app">
          <ejs-documenteditor ref="documenteditor" height="370px" style="width: 100%;"></ejs-documenteditor>
      </div>
</template>
<script>
    import Vue from 'vue'
    import { DocumentEditorPlugin } from '@syncfusion/ej2-vue-documenteditor';

    Vue.use(DocumentEditorPlugin);

    export default {
        data: function() {
            return {
            };
        },
        mounted: function() {
            //Set zoom factor to fit page width.
            this.$refs.documenteditor.fitPage('FitPageWidth');
        }
    }
</script>
<style>
 @import "../../node_modules/@syncfusion/ej2-vue-documenteditor/styles/material.css";
</style>
```

## Zoom option using UI

The following code example shows how to provide zoom options in Document Editor.

{% tab template="document-editor/scrolling-zooming", isDefaultActive=false %}

{% raw %}

```html
<template>
        <div id="app">
            <ejs-documenteditor ref="documenteditor" v-bind:selectionChange='onSelectionChange' v-bind:viewChange='onViewChange' v-bind:documentChange='onDocumentChange' :enableSelection='true' :isReadOnly=false height="370px" style="width: 100%;></ejs-documenteditor>
            <div id="documenteditor_statusbar">
                <label style="margin-top: 6px;margin-right: 2px">Page </label>
                <div class="single-line e-de-pagenumber-text" v-on:keydown='pageKeydownEvent' v-on:click='pagerClickEvent' id="editablePageNumber" style="font-size:12px;font-weight: 700;display: inline-flex;height: 17px;padding: 0px 4px;" contenteditable="false">
                    <label id="documenteditor_page_no" style="text-transform:capitalize;white-space:pre;overflow:hidden;user-select:none;cursor:text;height:17px;max-width:150px">{{currentPage}}</label>
                </div>
                <label id="documenteditor_pagecount_separator" style="margin-left:2px;letter-spacing: 1.05px">of</label>
                <label id="documenteditor_pagecount" style="margin-left:6px;letter-spacing: 1.05px">{{pageCount}}</label>
                <ejs-dropdownbutton ref="de_zoom" :items="zoomItems" class="e-de-statusbar-zoom" :content="zoomContent" v-bind:select="onZoom" title="Zoom level. Click or tap to open the Zoom options."></ejs-dropdownbutton>
            </div>
        </div>
</template>
<script>
    import Vue from 'vue'
    import { DocumentEditorPlugin, Selection } from '@syncfusion/ej2-vue-documenteditor';
    import { DropDownButtonPlugin } from '@syncfusion/ej2-vue-splitbuttons';

    Vue.use(DocumentEditorPlugin);
    Vue.use(DropDownButtonPlugin);

    export default {
        props: ['pageCount', 'currentPage', 'zoomContent'],
        data: function() {
            return {
                zoomContent: "100%",
                zoomItems: [
                {
                    text: '150%',
                },
                {
                    text: '125%',
                },
                {
                    text: '100%',
                },
                {
                    text: '75%',
                },
                {
                    text: '50%',
                },
                {
                    separator: true
                },
                {
                    text: 'Fit one page'
                },
                {
                    text: 'Fit page width',
                }],
                pageCount: 1,
                currentPage: 1
            };
        },
        provide: {
            //Inject require modules.
            DocumentEditor : [Selection]
        },
        methods :{
            onViewChange: function(args) {
                //Update page number on view change.
                this.currentPage =  args.startPage;
            },
            onSelectionChange : function(args) {
                //Get current page number.
                this.currentPage =  this.$refs.documenteditor.ej2Instances.selection.startPage;
            }
            onDocumentChange: function() {
                //Update page count.
                this.pageCount =  this.$refs.documenteditor.ej2Instances.pageCount;
                //Update zoom factor.
                this.zoomContent = Math.round(this.$refs.documenteditor.ej2Instances.zoomFactor * 100) + '%';
            },
            onZoom: function (args) {
                let zoomValue = args.item.text;
                if (zoomValue.match('Fit one page')) {
                    this.$refs.documenteditor.ej2Instances.fitPage('FitOnePage');
                } else if (zoomValue.match('Fit page width')) {
                    this.$refs.documenteditor.ej2Instances.fitPage('FitPageWidth');
                } else {
                    this.$refs.documenteditor.ej2Instances.zoomFactor = parseInt(zoomValue, 0) / 100;
                }
                this.zoomContent = Math.round(this.$refs.documenteditor.ej2Instances.zoomFactor * 100) + '%';
            },
            pageKeydownEvent: function (e) {
                if (e.which === 13) {
                    e.preventDefault();
                    let pageNumber = parseInt(document.getElementById("editablePageNumber").textContent, 0);
                    if (pageNumber > this.$refs.documenteditor.ej2Instances.pageCount) {
                        this.updatePageNumber();
                    } else {
                        this.$refs.documenteditor.ej2Instances.selection.goToPage(parseInt(document.getElementById("editablePageNumber").textContent, 0));
                    }
                    document.getElementById("editablePageNumber").contentEditable = 'false';
                    if (document.getElementById("editablePageNumber").textContent === '') {
                        this.updatePageNumber();
                    }
                }
                if (e.which > 64) {
                    e.preventDefault();
                }
            },
            pageBlurEvent: function () {
                if (document.getElementById("editablePageNumber").textContent === '' || parseInt(document.getElementById("editablePageNumber").textContent, 0) > this.$refs.documenteditor.ej2Instances.pageCountt) {
                    this.updatePageNumber();
                }
                document.getElementById("editablePageNumber").contentEditable = 'false';
            },
            pagerClickEvent: function () {
                document.getElementById("editablePageNumber").contentEditable = 'true';
                document.getElementById("editablePageNumber").focus();
                window.getSelection().selectAllChildren(document.getElementById("editablePageNumber"));
            },
            updatePageNumber: function () {
                this.currentPage = this.$refs.documenteditor.ej2Instances.selection.startPage.toString();
            }
        },
        mounted: function() {
            let defaultDocument: object = {
                "sections": [
                    {
                        "blocks": [
                            {
                                "paragraphFormat": {
                                    "styleName": "Normal"
                                },
                                "inlines": [
                                    {
                                        "text": "First page"
                                    }
                                ]
                            }
                        ],
                        "headersFooters": {},
                    },
                    {
                        "blocks": [
                            {
                                "paragraphFormat": {
                                    "styleName": "Normal"
                                },
                                "inlines": [
                                    {
                                        "text": "Second page"
                                    }
                                ]
                            }
                        ],
                        "headersFooters": {},
                    },
                    {
                        "blocks": [
                            {
                                "paragraphFormat": {
                                    "styleName": "Normal"
                                },
                                "inlines": [
                                    {
                                        "text": "Third page"
                                    }
                                ]
                            }
                        ],
                        "headersFooters": {},
                    }
                ],
                "characterFormat": {},
                "paragraphFormat": {},
                "background": {
                    "color": "#FFFFFFFF"
                },
                "styles": [
                    {
                        "type": "Paragraph",
                        "name": "Normal",
                        "next": "Normal"
                    },
                    {
                        "type": "Character",
                        "name": "Default Paragraph Font"
                    }
                ]
            }
            //Open default document in Document Editor.
            this.$refs.documenteditor.open(JSON.stringify(defaultDocument));
            document.getElementById('editablePageNumber').addEventListener('blur',this.pageBlurEvent);
        }
    }
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-documenteditor/styles/material.css";

    .single-line {
        cursor: text !important;
        outline: none;
    }

    .single-line:hover {
        border-color: #e4e4e4 !important;
    }

    [contenteditable="true"].single-line {
        white-space: nowrap;
        border-color: #e4e4e4 !important;
    }

    .e-de-pagenumber-text:hover {
        background-color: #f4f4f4 !important;
    }

    [contenteditable="true"].single-line * {
        white-space: nowrap;
    }

    .e-de-statusbar-zoom {
        float: right;
        text-align: center;
        padding: 2px;
        line-height: 19px;
        margin-top: 1px;
    }
</style>
```

{% endraw %}

{% endtab %}