---
title: "Localization"
component: "PDF Viewer"
description: "Learn how to localize the text content used in our PDF Viewer based on culture settings"
---

# Localization

The text contents provided in the PDF Viewer can be localized using the collection of localized strings for different cultures. By default, the PDF Viewer is localized in “__en-US__”.

The following table shows the default text values used in PDF Viewer in 'en-US' culture:

|Keywords|Values|
|---|---|
|PdfViewer|PDF Viewer|
|Cancel|Cancel|
|Download file|Download file|
|Download|Download|
|Enter Password|This document is password protected. Please enter a password.|
|File Corrupted|File corrupted|
|File Corrupted Content|The file is corrupted and cannot be opened.|
|Fit Page|Fit page|
|Fit Width|Fit width|
|Automatic|Automatic|
|Go To First Page|Show first page|
|Invalid Password|Incorrect password. Please try again.|
|Next Page|Show next page|
|OK|OK|
|Open|Open file|
|Page Number|Current page number|
|Previous Page|Show previous page|
|Go To Last Page|Show last page|
|Zoom|Zoom|
|Zoom In|Zoom in|
|Zoom Out|Zoom out|
|Page Thumbnails|Page thumbnails|
|Bookmarks|Bookmarks|
|Print|Print file
|Password Protected|Password required|
|Copy|Copy|
|Text Selection|Text selection tool|
|Panning|Pan mode|
|Text Search|Find text|
|Find in document|Find in document|
|Match case|Match case|
|Apply|Apply|
|GoToPage|Go to page|
|No matches|Viewer has finished searching the document. No more matches were found|
|No Text Found|No Text Found|
|Undo|Undo|
|Redo|Redo|
|Annotation|Add or Edit annotations|
|Highlight|Highlight Text|
|Underline|Underline Text|
|Strikethrough|Strikethrough Text|
|Delete|Delete annotation|
|Opacity|Opacity|
|Color edit|Change Color|
|Opacity edit|Change Opacity|
|Highlight context|Highlight|
|Underline context|Underline|
|Strikethrough context|Strike through|
|Server error|Web-service is not listening. PDF Viewer depends on web-service for all it's features. Please start the web service to continue.|
|Open text|Open|
|First text|First Page|
|Previous text|Previous Page|
|Next text|Next Page|
|Last text|Last Page|
|Zoom in text|Zoom In|
|Zoom out text|Zoom Out|
|Selection text|Selection|
|Pan text|Pan|
|Print text|Print|
|Search text|Search|
|Annotation Edit text|Edit Annotation| Please start the web service to continue.|

The different locale value for the PDF Viewer can be specified using the locale property.

```html
<template>
    <div>
        <ejs-pdfviewer id="pdfviewer" :serviceUrl="serviceUrl" :documentPath="documentPath": locale='ar-AE' ></ejs-pdfviewer>
    </div>
</template>
<style>
#pdfviewer {
height: 640px;
}
</style>
<script>
import Vue from "vue";
import { PdfViewerPlugin, Toolbar, Magnification, Navigation, Annotation, LinkAnnotation, BookmarkView, ThumbnailView, Print, TextSelection, TextSearch, Annotation } from "@syncfusion/ej2-vue-pdfviewer";
import { L10n, setCulture  } from '@syncfusion/ej2-base';

Vue.use(PdfViewerPlugin);

export default Vue.extend({
    data: function() {
        return {
        serviceUrl:"https://ej2services.syncfusion.com/production/web-services/api/pdfviewer",
        documentPath:"PDF_Succinctly.pdf"
        }
    },
    provide: {
        PdfViewer: [Toolbar, Magnification, Navigation, LinkAnnotation, Annotation, BookmarkView, ThumbnailView, Print, TextSelection, TextSearch, Annotation]
    }
});
//PDF Viewer Arabic Sample Locale
L10n.load({
    'ar-AE': {
        'PdfViewer' : {
            'PdfViewer': 'قوات الدفاع الشعبي المشاهد',
            'Cancel' : 'إلغاء',
            'Download file' : 'تحميل الملف',
            'Download': 'تحميل',
            'Enter Password' : 'هذا المستند محمي بكلمة مرور. يرجى إدخال كلمة مرور.',
            'File Corrupted' : 'ملف تالف',
            'File Corrupted Content' : 'الملف تالف ولا يمكن فتحه.',
            'Fit Page' : 'لائق بدنيا الصفحة',
            'Fit Width' : 'لائق بدنيا عرض',
            'Automatic' : 'تلقائي',
            'Go To First Page' : 'عرض الصفحة الأولى',
            'Invalid Password' : 'كلمة سر خاطئة. حاول مرة اخرى.',
            'Next Page' : 'عرض الصفحة التالية',
            'OK': 'حسنا',
            'Open' : 'فتح الملف',
            'Page Number' : 'رقم الصفحة الحالية',
            'Previous Page' : 'عرض الصفحة السابقة',
            'Go To Last Page' : 'عرض الصفحة الأخيرة',
            'Zoom' : 'تكبير',
            'Zoom In' : 'تكبير في',
            'Zoom Out' : 'تكبير خارج',
            'Page Thumbnails': 'مصغرات الصفحة',
            'Bookmarks': 'المرجعية',
            'Print' : 'اطبع الملف',
            'Password Protected' : 'كلمة المرور مطلوبة',
            'Copy': 'نسخ',
            'Text Selection': 'أداة اختيار النص',
            'Panning': 'وضع عموم',
            'Text Search': 'بحث عن نص',
            'Find in document': 'ابحث في المستند',
            'Match case': 'حالة مباراة',
            'Apply': 'تطبيق',
            'GoToPage': 'انتقل إلى صفحة',
             // tslint:disable-next-line:max-line-length
            'No matches': 'انتهى العارض من البحث في المستند. لم يتم العثور على مزيد من التطابقات',
            'No Text Found': 'لم يتم العثور على نص',
            // tslint:disable-next-line:max-line-length
            'Server error': 'خدمة الانترنت لا يستمع. يعتمد قوات الدفاع الشعبي المشاهد على خدمة الويب لجميع ميزاته. يرجى بدء خدمة الويب للمتابعة.',
            'Undo' : 'فك',
            'Redo' : 'فعل ثانية',
            'Annotation': 'إضافة أو تعديل التعليقات التوضيحية',
            'Highlight': 'تسليط الضوء على النص',
            'Underline': 'تسطير النص',
            'Strikethrough': 'نص يتوسطه خط',
            'Delete': 'حذف التعليق التوضيحي',
            'Opacity': 'غموض',
            'Color edit': 'غير اللون',
            'Opacity edit': 'تغيير التعتيم',
            'Highlight context': 'تسليط الضوء',
            'Underline context': 'أكد',
            'Strikethrough context': 'يتوسطه',
            'Open text': 'افتح',
            'First text': 'الصفحة الأولى',
            'Previous text': 'الصفحة السابقة',
            'Next text': 'الصفحة التالية',
            'Last text': 'آخر صفحة',
            'Zoom in text': 'تكبير',
            'Zoom out text': 'تصغير',
            'Selection text': 'اختيار',
            'Pan text': 'مقلاة',
            'Print text': 'طباعة',
            'Search text': 'بحث',
            'Annotation Edit text': 'تحرير التعليق التوضيحي'
        }
    }
});
</script>
```
