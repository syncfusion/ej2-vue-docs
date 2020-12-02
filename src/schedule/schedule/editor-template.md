---
title: "Editor Window and Quick Popup of Scheduler"
component: "Scheduler"
description: "This topic demonstrates how to customize the default event editor and quick pop-up using templates and also explains how to design the custom modal popup."
---

# Editor window and quick popups

Scheduler makes use of popups and dialog to display the required notifications, as well as includes an editor window with event fields for making the appointment creation and editing process easier. You can also easily customize the editor window and the fields present in it, and can also apply validations on those fields.

## Event editor

The editor window usually opens on the Scheduler, when a cell or event is double clicked. When a cell is double clicked, the detailed editor window opens in "Add new" mode, whereas when an event is double clicked, the same is opened in an "Edit" mode.

In mobile devices, you can open the detailed editor window in edit mode by clicking the edit icon on the popup, that opens on single tapping an event. You can also open it in add mode by single tapping a cell, which will display a `+` indication, clicking on it again will open the editor window.

> You can also prevent the editor window from opening, by rendering Scheduler in a `readonly` mode or by doing code customization within the `popupOpen` event.

### How to change the editor window header title and text of footer buttons

You can change the header title and the text of buttons displayed at the footer of the editor window by changing the appropriate localized word collection used in the Scheduler.

{% tab template="schedule/editor-window", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule :height='height' :width='width' :selectedDate='selectedDate' :views='views' :eventSettings='eventSettings'></ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { L10n } from '@syncfusion/ej2-base';
import { SchedulePlugin, Day, Week, TimelineViews, Month, Agenda } from '@syncfusion/ej2-vue-schedule';
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);

L10n.load({
    'en-US': {
        'schedule': {
            'saveButton': 'Add',
            'cancelButton': 'Close',
            'deleteButton': 'Remove',
            'newEvent': 'Add Event',
        },
    }
});

export default {
  data (){
    return {
      height: '550px',
      width: '100%',
      views: ['TimelineDay', 'Day', 'Week', 'Month', 'Agenda'],
      eventSettings: { dataSource: scheduleData },
      selectedDate: new Date(2018, 1, 15),
    }
  },
  provide: {
    schedule: [Day, Week, TimelineViews, Month, Agenda]
  }
}

</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";
</style>

```

{% endtab %}

### How to change the label text of default editor fields

To change the default labels such as Subject, Location and other field names in the editor window, make use of the `title` property available within the field option of `eventSettings`.

{% tab template="schedule/editor-window", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule :height='height' :width='width' :selectedDate='selectedDate' :views='views' :eventSettings='eventSettings'></ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { SchedulePlugin, Day, Week, TimelineViews, Month, Agenda } from '@syncfusion/ej2-vue-schedule';
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);

export default {
  data (){
    return {
      height: '550px',
      width: '100%',
      views: ['TimelineDay', 'Day', 'Week', 'Month', 'Agenda'],
      eventSettings: {
          dataSource: scheduleData,
          fields: {
            id: 'Id',
            subject: { name: 'Subject', title: 'Event Name' },
            location: { name: 'Location', title: 'Event Location'},
            description: { name: 'Description', title: 'Event Description' },
            startTime: { name: 'StartTime', title: 'Start Duration' },
            endTime: { name: 'EndTime', title: 'End Duration'  }
        }
      },
      selectedDate: new Date(2018, 1, 15),
    }
  },
  provide: {
    schedule: [Day, Week, TimelineViews, Month, Agenda]
  }
}

</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";
</style>

```

{% endtab %}

### Field validation

It is possible to validate the required fields of the editor window from client-side before submitting it, by adding appropriate validation rules to each field. The appointment fields have been extended to accept both `string` and `object` type values. To perform validations, it is necessary to specify object values for the event fields.

{% tab template="schedule/editor-window", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule :height='height' :width='width' :selectedDate='selectedDate' :eventSettings='eventSettings'></ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-vue-schedule';
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);

let minValidation: (args) =>  = (args) => {
    return args['value'].length >= 5;
};

export default {
  data (){
    return {
      height: '550px',
      width: '100%',
      eventSettings: {
          dataSource: scheduleData,
          fields: {
            id: 'Id',
            subject: { name: 'Subject', validation: { required: true } },
            location: { name: 'Location', validation: { required: true } },
            description: {
                name: 'Description', validation: {
                    required: true, minLength: [minValidation, 'Need atleast 5 letters to be entered']
                }
            },
            startTime: { name: 'StartTime', validation: { required: true } },
            endTime: { name: 'EndTime', validation: { required: true } }
          }
      },
      selectedDate: new Date(2018, 1, 15),
    }
  },
  provide: {
    schedule: [Day, Week, WorkWeek, Month, Agenda]
  }
}

</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";
</style>

```

{% endtab %}

> Applicable validation rules can be referred from [form validation](http://ej2.syncfusion.com/documentation/form-validator/#validation-rules) documentation.

### Add additional fields to the default editor

The additional fields can be added to the default event editor by making use of the `popupOpen` event which gets triggered before the event editor opens on the Scheduler. The `popupOpen` is a client-side event that triggers before any of the generic popups opens on the Scheduler. The additional field (any of the form elements) should be added with a common class name `e-field`, so as to handle and process those additional data along with the default event object. In the following example, an additional field `Event Type` has been added to the default event editor and its value is processed accordingly.

{% tab template="schedule/editor-window", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule :height='height' :width='width' :views='views' :selectedDate='selectedDate' :eventSettings='eventSettings' :popupOpen='onPopupOpen'></ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { SchedulePlugin, Day, Week, WorkWeek, Month } from '@syncfusion/ej2-vue-schedule';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { createElement } from '@syncfusion/ej2-base';
import { eventData } from './datasource.js';

Vue.use(SchedulePlugin);

export default {
  data (){
    return {
      height: '550px',
      width: '100%',
      views: ['Day', 'Week', 'WorkWeek', 'Month'],
      eventSettings: {
          dataSource: eventData
      },
      selectedDate: new Date(2018, 1, 15),
    }
  },
  methods: {
    onPopupOpen: function(args) {
        if (args.type === 'Editor') {
            // Create required custom elements in initial time
            if (!args.element.querySelector('.custom-field-row')) {
              let row = createElement('div', { className: 'custom-field-row' });
              let formElement = args.element.querySelector('.e-schedule-form');
              formElement.firstChild.insertBefore(row, args.element.querySelector('.e-title-location-row'));
              let container = createElement('div', { className: 'custom-field-container' });
              let inputEle = createElement('input', {
                  className: 'e-field', attrs: { name: 'EventType' }
              });
              container.appendChild(inputEle);
              row.appendChild(container);
              let dropDownList = new DropDownList({
                  dataSource: [
                    { text: 'Public Event', value: 'public-event' },
                    { text: 'Maintenance', value: 'maintenance' },
                    { text: 'Commercial Event', value: 'commercial-event' },
                    { text: 'Family Event', value: 'family-event' }
                  ],
                    fields: { text: 'text', value: 'value' },
                    value: args.data.EventType,
                    floatLabelType: 'Always', placeholder: 'Event Type'
              });
              dropDownList.appendTo(inputEle);
              inputEle.setAttribute('name', 'EventType');
            }
        }
    }
  },
  provide: {
    schedule: [Day, Week, WorkWeek, Month]
  }
}

</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";
  
  .custom-field-row {
    padding-bottom: 14px;
  }
</style>

```

{% endtab %}

### Customizing the default time duration in editor window

In default event editor window, start and end time duration are processed based on the `interval` value set within the `timeScale` property. By default, `interval` value is set to 30, and therefore the start/end time duration within the event editor will be in a 30 minutes time difference. You can change this duration value by changing the `duration` option within the `popupOpen` event as shown in the following code example.

{% tab template="schedule/editor-window", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule :height='height' :width='width' :views='views' :selectedDate='selectedDate' :eventSettings='eventSettings' :popupOpen='onPopupOpen'></ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { SchedulePlugin, Day, Week, WorkWeek, Month } from '@syncfusion/ej2-vue-schedule';
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);

export default {
  data (){
    return {
      height: '550px',
      width: '100%',
      views: ['Day', 'Week', 'WorkWeek', 'Month'],
      eventSettings: {
          dataSource: scheduleData
      },
      selectedDate: new Date(2018, 1, 15),
    }
  },
  methods: {
    onPopupOpen: function(args) {
        if (args.type === 'Editor') {
          args.duration = 60;
        }
    }
  },
  provide: {
    schedule: [Day, Week, WorkWeek, Month]
  }
}

</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";
</style>

```

{% endtab %}

### How to prevent the display of editor and quick popups

It is possible to prevent the display of editor and quick popup windows by passing the value `true` to `cancel` option within the `popupOpen` event.

{% tab template="schedule/editor-window", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule :height='height' :width='width' :views='views' :selectedDate='selectedDate' :eventSettings='eventSettings' :popupOpen='onPopupOpen'></ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { SchedulePlugin, Day, Week, WorkWeek, Month } from '@syncfusion/ej2-vue-schedule';
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);

export default {
  data (){
    return {
      height: '550px',
      width: '100%',
      views: ['Day', 'Week', 'WorkWeek', 'Month'],
      eventSettings: {
          dataSource: scheduleData
      },
      selectedDate: new Date(2018, 1, 15),
    }
  },
  methods: {
    onPopupOpen: function(args) {
        args.cancel = true;
    }
  },
  provide: {
    schedule: [Day, Week, WorkWeek, Month]
  }
}

</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";
</style>

```

{% endtab %}

In case, if you need to prevent only specific popups on Scheduler, then you can check the condition based on the popup type. The types of the popup that can be checked within the `popupOpen` event are as follows.

| Type | Description |
|------|-------------|
| Editor | For Detailed editor window.|
| QuickInfo | For Quick popup which opens on cell click.|
| EditEventInfo |For  Quick popup which opens on event click.|
| ViewEventInfo | For Quick popup which opens on responsive mode.|
| EventContainer | For more event indicator popup.|
| RecurrenceAlert | For edit recurrence event alert popup.|
| DeleteAlert | For delete confirmation popup.|
| ValidationAlert | For validation alert popup.|
| RecurrenceValidationAlert | For recurrence validation alert popup.|

## Customizing event editor using template

The event editor window can be customized by making use of the `editorTemplate` option. Here, the custom window design is built with the required fields using the script template and its type should be of **text/x-template**.

Each field defined within template should contain the **e-field** class, so as to allow the processing of those field values internally. The ID of this customized script template section is assigned to the `editorTemplate` option, so that these customized fields will be replaced onto the default editor window.

As we are using our Syncfusion sub-components within our editor using template in the following example, the custom defined form elements needs to be configured as required Syncfusion components such as **DropDownList** and **DateTimePicker** within the `popupOpen` event. This particular step can be skipped, if the user needs to simply use the usual form elements.

{% tab template="schedule/editor", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
      <ejs-schedule :height='height' :width='width' :views='views' :selectedDate='selectedDate'
        :eventSettings='eventSettings' :editorTemplate='editorTemplate' :popupOpen='onPopupOpen'>
      </ejs-schedule>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import { SchedulePlugin, Day, Week, WorkWeek, Month } from '@syncfusion/ej2-vue-schedule';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { DateTimePicker } from '@syncfusion/ej2-calendars';
import { eventData } from './datasource.js';

Vue.use(SchedulePlugin);

var editorTemplateVue = Vue.component('editorTemplate', {
  template: `<table class="custom-event-editor" width="100%" cellpadding="5"><tbody><tr>
  <td class="e-textlabel">Summary</td><td colspan="4"><input id="Subject" class="e-field e-input" type="text" value="" name="Subject" style="width: 100%" /></td></tr><tr><td class="e-textlabel">Status</td><td colspan="4"><input type="text" id="EventType" name="EventType" class="e-field" style="width: 100%" /></td></tr><tr><td class="e-textlabel">From</td><td colspan="4"><input id="StartTime" class="e-field" type="text" name="StartTime" /></td></tr><tr>
  <td class="e-textlabel">To</td><td colspan="4"><input id="EndTime" class="e-field" type="text" name="EndTime" /></td></tr><tr><td class="e-textlabel">Reason</td><td colspan="4">
  <textarea id="Description" class="e-field e-input" name="Description" rows="3" cols="50"                 style="width: 100%; height: 60px !important; resize: vertical"></textarea></td></tr></tbody></table>`,
  data() {
    return {
      data: {}
    };
  }
});
export default {
  data() {
    return {
      height: '550px',
      width: '100%',
      views: ['Day', 'Week', 'WorkWeek', 'Month'],
      eventSettings: {
        dataSource: eventData
      },
      selectedDate: new Date(2018, 1, 15),
      showQuickInfo: false,
      editorTemplate: function(e) {
        return {
          template: editorTemplateVue
        };
      }
    };
  },
  methods: {
    onPopupOpen: function(args) {
      if (args.type === 'Editor') {
        let statusElement = args.element.querySelector('#EventType');
        if (!statusElement.classList.contains('e-dropdownlist')) {
          let dropDownListObject = new DropDownList({
            placeholder: 'Choose status',
            value: statusElement.value,
            dataSource: ['New', 'Requested', 'Confirmed']
          });
          dropDownListObject.appendTo(statusElement);
          statusElement.setAttribute('name', 'EventType');
        }
        let startElement = args.element.querySelector('#StartTime');
        if (!startElement.classList.contains('e-datetimepicker')) {
          new DateTimePicker(
            { value: new Date(startElement.value) || new Date() },
            startElement
          );
        }
        let endElement = args.element.querySelector('#EndTime');
        if (!endElement.classList.contains('e-datetimepicker')) {
          new DateTimePicker(
            { value: new Date(endElement.value) || new Date() },
            endElement
          );
        }
      }
    }
  },
  provide: {
    schedule: [Day, Week, WorkWeek, Month]
  }
}
</script>

<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";
.custom-event-editor .e-textlabel {
  padding-right: 15px;
  text-align: right;
}
.custom-event-editor td {
  padding: 7px;
  padding-right: 16px;
}
</style>

```

{% endtab %}

### How to add resource options within editor template

The resource field can be added within editor template with multiselect control for allow multiple resources.

{% tab template="schedule/resource-field", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
      <ejs-schedule :height='height' :width='width' :views='views' :selectedDate='selectedDate'
        :eventSettings='eventSettings' :editorTemplate='editorTemplate' :popupOpen='onPopupOpen'
        :group='group'>
        <e-resources>
          <e-resource field='OwnerId' title='Owner' name='Owners' :dataSource='ownerDataSource' textField='text' idField='id' colorField='color'>
          </e-resource>
        </e-resources>
      </ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { SchedulePlugin, Day, Week, WorkWeek, Month } from '@syncfusion/ej2-vue-schedule';
import { MultiSelect } from '@syncfusion/ej2-dropdowns';
import { DateTimePicker } from '@syncfusion/ej2-calendars';
import { eventData } from './datasource.js';

Vue.use(SchedulePlugin);

var editorTemplateVue = Vue.component('editorTemplate', {
  template: `<table class="custom-event-editor" width="100%" cellpadding="5">
        <tbody>
            <tr>
                <td class="e-textlabel">Summary</td>
                <td colspan="4">
                    <input id="Subject" class="e-field e-input" type="text" value="" name="Subject" style="width: 100%" />
                </td>
            </tr>
            <tr>
            <td class="e-textlabel">From</td>
                <td colspan="4">
                    <input id="StartTime" class="e-field" type="text" name="StartTime" />
                </td>
            </tr>
            <tr>
                <td class="e-textlabel">To</td>
                <td colspan="4">
                    <input id="EndTime" class="e-field" type="text" name="EndTime" />
                </td>
            </tr>
            <tr>
                <td class="e-textlabel">Owner</td>
                <td colspan="4">
                    <input type="text" id="OwnerId" name="OwnerId" class="e-field" style="width: 100%" />
                </td>
            </tr>
            <tr>
                <td class="e-textlabel">Reason</td>
                <td colspan="4">
                    <textarea id="Description" class="e-field e-input" name="Description" rows="3" cols="50" style="width: 100%; height: 60px !important; resize: vertical"></textarea>
                </td>
            </tr>
        </tbody>
    </table>`,
  data() {
    return {
      data: {}
    };
  }
});

export default {
  data() {
    return {
      height: '550px',
      width: '100%',
      views: ['Day', 'Week', 'WorkWeek', 'Month'],
      eventSettings: {
        dataSource: eventData
      },
      selectedDate: new Date(2018, 1, 15),
      group: { resources: ['Owners'] },
      ownerDataSource: [
        { text: 'Nancy', id: 1, color: '#1aaa55' },
        { text: 'Smith', id: 2, color: '#7fa900' },
        { text: 'Paul', id: 3, color: '#357cd2' }
      ],
      editorTemplate: function(e) {
        return {
          template: editorTemplateVue
        };
      }
    };
  },
  methods: {
    onPopupOpen: function(args) {
      if (args.type === 'Editor') {
        let startElement = args.element.querySelector('#StartTime');
        if (!startElement.classList.contains('e-datetimepicker')) {
          new DateTimePicker(
            { value: new Date(startElement.value) || new Date() },
            startElement
          );
        }
        let endElement = args.element.querySelector('#EndTime');
        if (!endElement.classList.contains('e-datetimepicker')) {
          new DateTimePicker(
            { value: new Date(endElement.value) || new Date() },
            endElement
          );
        }
        let processElement = args.element.querySelector('#OwnerId');
        if (!processElement.classList.contains('e-multiselect')) {
          let multiSelectObject = new MultiSelect({
            placeholder: 'Choose a owner',
            fields: { text: 'text', value: 'id' },
            dataSource: this.ownerDataSource,
            value: [args.data.OwnerId],
          });
          multiSelectObject.appendTo(processElement);
        }
      }
    }
  },
  provide: {
    schedule: [Day, Week, WorkWeek, Month]
  }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";

  .custom-event-editor .e-textlabel {
    padding-right: 15px;
    text-align: right;
  }
  .custom-event-editor td {
    padding: 7px;
    padding-right: 16px;
  }  
</style>

```

{% endtab %}

### How to add recurrence options within editor template

The following code example shows how to add recurrence options within the editor template by importing `RecurrenceEditor`.

{% tab template="schedule/editor-recurrence", iframeHeight="588px"  %}

```html

<template>
  <div id='app'>
    <div id='container'>
      <ejs-schedule ref='scheduleObj' :height='height' :width='width' :views='views' :selectedDate='selectedDate' :eventSettings='eventSettings' :editorTemplate='editorTemplate' :popupOpen='onPopupOpen'>
      </ejs-schedule>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import {
    SchedulePlugin, Day, Week, WorkWeek, Month, RecurrenceEditor
} from '@syncfusion/ej2-vue-schedule';
import { DateTimePicker } from '@syncfusion/ej2-calendars';
import { eventData } from './datasource.js';

Vue.use(SchedulePlugin);

var editorTemplateVue = Vue.component('editorTemplate', {
  template: `<table class="custom-event-editor" width="100%" cellpadding="5">
        <tbody>
            <tr>
                <td class="e-textlabel">Summary</td>
                <td colspan="4">
                    <input id="Subject" class="e-field e-input" type="text" value="" name="Subject" style="width: 100%" />
                </td>
            </tr>
            <tr>
            <td class="e-textlabel">From</td>
                <td colspan="4">
                    <input id="StartTime" class="e-field" type="text" name="StartTime" />
                </td>
            </tr>
            <tr>
                <td class="e-textlabel">To</td>
                <td colspan="4">
                    <input id="EndTime" class="e-field" type="text" name="EndTime" />
                </td>
            </tr>
            <tr>
                <td colspan="4">
                    <div id='RecurrenceEditor'></div>
                </td>
            </tr>
            <tr>
                <td class="e-textlabel">Reason</td>
                <td colspan="4">
                    <textarea id="Description" class="e-field e-input" name="Description" rows="3" cols="50" style="width: 100%; height: 60px !important; resize: vertical"></textarea>
                </td>
            </tr>
        </tbody>
    </table>`,
  data() {
    return {
      data: {}
    };
  }
});

export default {
  data() {
    return {
      height: '550px',
      width: '100%',
      views: ['Day', 'Week', 'WorkWeek', 'Month'],
      eventSettings: {
        dataSource: eventData
      },
      selectedDate: new Date(2018, 1, 15),
      editorTemplate: function(e) {
        return {
          template: editorTemplateVue
        };
      }
    };
  },
  methods: {
    onPopupOpen: function(args) {
      if (args.type === 'Editor') {
        let scheduleObj = this.$refs.scheduleObj.ej2Instances;
        let startElement = args.element.querySelector('#StartTime');
        if (!startElement.classList.contains('e-datetimepicker')) {
            new DateTimePicker({ value: new Date(startElement.value) || new Date() }, startElement);
        }
        let endElement = args.element.querySelector('#EndTime');
        if (!endElement.classList.contains('e-datetimepicker')) {
            new DateTimePicker({ value: new Date(endElement.value) || new Date() }, endElement);
        }
        let recurElement = args.element.querySelector('#RecurrenceEditor');
        if (!recurElement.classList.contains('e-recurrenceeditor')) {
            let recurrObject = new RecurrenceEditor({});
            recurrObject.appendTo(recurElement);
            scheduleObj.eventWindow.recurrenceEditor = recurrObject;
        }
        document.getElementById('RecurrenceEditor').style.display = (scheduleObj.currentAction == 'EditOccurrence') ? 'none' : 'block';
      }
    }
  },
  provide: {
    schedule: [Day, Week, WorkWeek, Month]
  }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";

  .custom-event-editor .e-textlabel {
    padding-right: 15px;
    text-align: right;
  }
  .custom-event-editor td {
    padding: 7px;
    padding-right: 16px;
  }  
</style>

```

{% endtab %}

### Apply validations on editor template fields

In the following code example, validation has been added to the status field.

{% tab template="schedule/editor", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
      <ejs-schedule :height='height' :width='width' :views='views' :selectedDate='selectedDate'
        :eventSettings='eventSettings' :editorTemplate='editorTemplate' :popupOpen='onPopupOpen'>
      </ejs-schedule>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import { SchedulePlugin, Day, Week, WorkWeek, Month } from '@syncfusion/ej2-vue-schedule';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { DateTimePicker } from '@syncfusion/ej2-calendars';
import { FormValidator } from '@syncfusion/ej2-inputs';
import { isNullOrUndefined } from '@syncfusion/ej2-base';
import { eventData } from './datasource.js';

Vue.use(SchedulePlugin);

var editorTemplateVue = Vue.component('editorTemplate', {
  template: `<table class="custom-event-editor" width="100%" cellpadding="5"><tbody><tr>
  <td class="e-textlabel">Summary</td><td colspan="4"><input id="Subject" class="e-field e-input" type="text" value="" name="Subject" style="width: 100%" /></td></tr><tr><td class="e-textlabel">Status</td><td colspan="4"><input type="text" id="EventType" name="EventType" class="e-field" style="width: 100%" /></td></tr><tr><td class="e-textlabel">From</td><td colspan="4"><input id="StartTime" class="e-field" type="text" name="StartTime" /></td></tr><tr>
  <td class="e-textlabel">To</td><td colspan="4"><input id="EndTime" class="e-field" type="text" name="EndTime" /></td></tr><tr><td class="e-textlabel">Reason</td><td colspan="4">
  <textarea id="Description" class="e-field e-input" name="Description" rows="3" cols="50"                 style="width: 100%; height: 60px !important; resize: vertical"></textarea></td></tr></tbody></table>`,
  data() {
    return {
      data: {}
    };
  }
});
export default {
  data() {
    return {
      height: '550px',
      width: '100%',
      views: ['Day', 'Week', 'WorkWeek', 'Month'],
      eventSettings: {
        dataSource: eventData
      },
      selectedDate: new Date(2018, 1, 15),
      showQuickInfo: false,
      editorTemplate: function(e) {
        return {
          template: editorTemplateVue
        };
      }
    };
  },
  methods: {
    onPopupOpen: function(args) {
      if (args.type === 'Editor') {
          if (!isNullOrUndefined(document.getElementById("EventType_Error"))) {
              document.getElementById("EventType_Error").style.display = "none";
              document.getElementById("EventType_Error").style.left = "351px";
          }
          let formElement = args.element.querySelector('.e-schedule-form');
          let statusElement = args.element.querySelector('#EventType');
          if (!statusElement.classList.contains('e-dropdownlist')) {
              let dropDownListObject = new DropDownList({
                  placeholder: 'Choose status', value: statusElement.value,
                  dataSource: ['New', 'Requested', 'Confirmed'],
                  select: function(args) {
                      if (!isNullOrUndefined(document.getElementById("EventType_Error"))) {
                          document.getElementById("EventType_Error").style.display = "none";
                      }
                  }
              });
              dropDownListObject.appendTo(statusElement);
          }
          let validator = formElement.ej2_instances[0];
          validator.addRules('EventType', { required: true });
          let startElement = args.element.querySelector('#StartTime');
          if (!startElement.classList.contains('e-datetimepicker')) {
              new DateTimePicker({ value: new Date(startElement.value) || new Date() }, startElement);
          }
          let endElement = args.element.querySelector('#EndTime');
          if (!endElement.classList.contains('e-datetimepicker')) {
              new DateTimePicker({ value: new Date(endElement.value) || new Date() }, endElement);
          }
      }
    }
  },
  provide: {
    schedule: [Day, Week, WorkWeek, Month]
  }
}
</script>

<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";
.custom-event-editor .e-textlabel {
  padding-right: 15px;
  text-align: right;
}
.custom-event-editor td {
  padding: 7px;
  padding-right: 16px;
}
</style>

```

{% endtab %}

### How to save the customized event editor using template

The **e-field** class is not added to each field defined within the template, so you should allow to set those field values externally by using the `popupClose` event.

Note: You can allow to retrieve the data only on the `save` and `delete` option. Data cannot be retrieved on the `close` and `cancel` options in the editor window.

The following code example shows how to save the customized event editor using a template by the `popupClose` event.

{% tab template="schedule/editor", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
      <ejs-schedule :height='height' :width='width' :views='views' :selectedDate='selectedDate'
        :eventSettings='eventSettings' :editorTemplate='editorTemplate' :popupOpen='onPopupOpen' :popupClose='onPopupClose' >
      </ejs-schedule>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import { SchedulePlugin, Day, Week, WorkWeek, Month } from '@syncfusion/ej2-vue-schedule';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { DateTimePicker } from '@syncfusion/ej2-calendars';
import { eventData } from './datasource.js';

Vue.use(SchedulePlugin);

var editorTemplateVue = Vue.component('editorTemplate', {
  template: `<table class="custom-event-editor" width="100%" cellpadding="5"><tbody><tr>
  <td class="e-textlabel">Summary</td><td colspan="4"><input id="Subject" class="e-input" type="text" name="Subject" style="width: 100%" /></td></tr><tr><td class="e-textlabel">Status</td><td colspan="4"><input type="text" id="EventType" name="EventType" style="width: 100%" /></td></tr><tr><td class="e-textlabel">From</td><td colspan="4"><input id="StartTime" type="text" name="StartTime" /></td></tr><tr>
  <td class="e-textlabel">To</td><td colspan="4"><input id="EndTime" type="text" name="EndTime" /></td></tr><tr><td class="e-textlabel">Reason</td><td colspan="4">
  <textarea id="Description" class="e-input" name="Description" rows="3" cols="50" style="width: 100%; height: 60px !important; resize: vertical"></textarea></td></tr></tbody></table>`,
  data() {
    return {
      data: {}
    };
  }
});
export default {
  data() {
    return {
      height: '550px',
      width: '100%',
      views: ['Day', 'Week', 'WorkWeek', 'Month'],
      eventSettings: {
        dataSource: eventData
      },
      selectedDate: new Date(2018, 1, 15),
      showQuickInfo: false,
      editorTemplate: function(e) {
        return {
          template: editorTemplateVue
        };
      }
    };
  },
  methods: {
    onPopupOpen: function(args) {
      if (args.type === 'Editor') {
          let subjectElement = args.element.querySelector('#Subject');
            if (subjectElement) {
                subjectElement.value = args.data.Subject || "";
            }
        let statusElement = args.element.querySelector('#EventType');
        if (!statusElement.classList.contains('e-dropdownlist')) {
          let dropDownListObject = new DropDownList({
            placeholder: 'Choose status',
            value: args.data.EventType,
            dataSource: ['New', 'Requested', 'Confirmed']
          });
          dropDownListObject.appendTo(statusElement);
          statusElement.setAttribute('name', 'EventType');
        }
        let startElement = args.element.querySelector('#StartTime');
        if (!startElement.classList.contains('e-datetimepicker')) {
          new DateTimePicker(
            { value: new Date(args.data.StartTime) || new Date() },
            startElement
          );
        }
        let endElement = args.element.querySelector('#EndTime');
        if (!endElement.classList.contains('e-datetimepicker')) {
          new DateTimePicker(
            { value: new Date(args.data.EndTime) || new Date() },
            endElement
          );
        }
        let descriptionElement = args.element.querySelector('#Description');
            if (descriptionElement) {
                descriptionElement.value = args.data.Description || "";
            }
      }
    },
    onPopupClose: function(args) {
      if (args.type === 'Editor'  && !isNullOrUndefined(args.data)) {
          let subjectElement = args.element.querySelector('#Subject');
            if (subjectElement) {
                args.data.Subject = subjectElement.value;
            }
        let statusElement = args.element.querySelector('#EventType');
        if (statusElement) {
          args.data.EventType = statusElement.value;
        }
        let startElement = args.element.querySelector('#StartTime');
        if (startElement) {
            args.data.StartTime = startElement.value;
        }
        let endElement = args.element.querySelector('#EndTime');
        if (endElement) {
            args.data.EndTime  = endElement.value;
        }
        let descriptionElement = args.element.querySelector('#Description');
            if (descriptionElement) {
                args.data.Description = descriptionElement.value;
            }
      }
    }
  },
  provide: {
    schedule: [Day, Week, WorkWeek, Month]
  }
}
</script>

<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";
.custom-event-editor .e-textlabel {
  padding-right: 15px;
  text-align: right;
}
.custom-event-editor td {
  padding: 7px;
  padding-right: 16px;
}
</style>

```

{% endtab %}

In case, if you need to prevent only specific popups on Scheduler, then you can check the condition based on the popup type. The types of the popup that can be checked within the `popupClose` event are as follows.

| Type | Description |
|------|-------------|
| Editor | For Detailed editor window.|
| QuickInfo | For Quick popup which opens on cell click.|
| EditEventInfo |For  Quick popup which opens on event click.|
| ViewEventInfo | For Quick popup which opens on responsive mode.|
| EventContainer | For more event indicator popup.|
| RecurrenceAlert | For edit recurrence event alert popup.|
| DeleteAlert | For delete confirmation popup.|
| ValidationAlert | For validation alert popup.|
| RecurrenceValidationAlert | For recurrence validation alert popup.|

## Quick popups

The quick info popups are the ones that gets opened, when a cell or appointment is single clicked on the desktop mode. On single clicking a cell, you can simply provide a subject and save it. Also, while single clicking on an event, a popup will be displayed where you can get the overview of the event information. You can also edit or delete those events through the options available in it.

By default, these popups are displayed over cells and appointments of Scheduler and to disable this action, set `false` to `showQuickInfo` property.

> The quick popup that opens while single clicking on the cells are not applicable on mobile devices.

{% tab template="schedule/editor-window", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule :height='height' :width='width' :views='views' :selectedDate='selectedDate' :eventSettings='eventSettings' :showQuickInfo='showQuickInfo'></ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { SchedulePlugin, Day, Week, Month, TimelineViews, Agenda } from '@syncfusion/ej2-vue-schedule';
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);

export default {
  data (){
    return {
      height: '550px',
      width: '100%',
      views: ['TimelineDay', 'Day', 'Week', 'Month', 'Agenda'],
      eventSettings: {
          dataSource: scheduleData
      },
      selectedDate: new Date(2018, 1, 15),
      showQuickInfo: false,
    }
  },
  provide: {
    schedule: [TimelineViews, Day, Week, Month, Agenda]
  }
}

</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";
</style>

```

{% endtab %}

### How to change the watermark text of quick popup subject

By default, `Add Title` text is displayed on the subject field of quick popup. To change the default watermark text, change the value of the appropriate localized word collection used in the Scheduler.

```typescript
L10n.load({
    'en-US': {
        'schedule': {
          'addTitle' : 'New Title'
        }
    }
});
```

### Customizing quick popups

The look and feel of the built-in quick popup window, which opens when single clicked on the cells or appointments can be customized by making use of the `quickInfoTemplates` property of the Scheduler. There are 3 sub-options available to customize them easily,

* header - Accepts the template design that customizes the header part of the quick popup.
* content - Accepts the template design that customizes the content part of the quick popup.
* footer - Accepts the template design that customizes the footer part of the quick popup.

{% tab template="schedule/quick-info", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
      <ejs-schedule :height='height' :width='width' :views='views'
        :selectedDate='selectedDate' :eventSettings='eventSettings'
        :quickInfoTemplates='quickInfoTemplates'>
      </ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import {SchedulePlugin, Day, Week, WorkWeek } from '@syncfusion/ej2-vue-schedule';
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);

var headerTemplateVue = Vue.component('headerTemplate', {
  template: `<div><div v-if= "data.elementType === 'cell' "><div class="e-cell-header">
        <div class="e-header-icon-wrapper"><button class="e-close" title="Close"></button></div></div></div>
        <div v-else><div class="e-event-header"><div class="e-header-icon-wrapper"><button class="e-close" title="CLOSE"></button></div></div></div></div>`,
  data() {
    return {
      data: {}
    };
  }
});

var contentTemplateVue = Vue.component('contentTemplate', {
  template: `<div><div v-if= "data.elementType === 'cell' "><div class="e-cell-content e-template">
        <form class="e-schedule-form"><div><input class="subject e-field" type="text" name="Subject" placeholder="Title"></div><div><input class="location e-field" type="text" name="Location" placeholder="Location"></div></form></div></div><div v-else><div class="e-event-content e-template">
        <div class="e-subject-wrap"><div><div v-if="data.Subject !== undefined"><div class="subject">{{data.Subject}}</div></div></div><div><div v-if="data.Location !== undefined"><div class="location">{{data.Location}}</div></div></div><div><div v-if="data.Description !== undefined"><div class="description">{{data.Description}}</div></div></div></div></div></div></div>`,
  data() {
    return {
      data: {}
    };
  }
});

var footerTemplateVue = Vue.component('footerTemplate', {
  template: `<div><div v-if= "data.elementType === 'cell' "><div class="e-cell-footer">
        <button class="e-event-details" title="Extra Details">Extra Details</button>
        <button class="e-event-create" title="Add">Add</button></div></div>
        <div v-else><div class="e-event-footer"><button class="e-event-edit" title="Edit">Edit</button>
        <button class="e-event-delete" title="Delete">Delete</button></div></div></div>`,
  data() {
    return {
      data: {}
    };
  }
});

export default {
  data() {
    return {
      height: '550px',
      width: '100%',
      eventSettings: {
        dataSource: scheduleData
      },
      selectedDate: new Date(2018, 1, 15),
      views: ['Day', 'Week', 'WorkWeek'],
      quickInfoTemplates: {
        header: function(e) {
          return {
            template: headerTemplateVue
          };
        },
        content: function(e) {
          return {
            template: contentTemplateVue
          };
        },
        footer: function(e) {
          return {
            template: footerTemplateVue
          };
        }
      }
    };
  },
  provide: {
    schedule: [Day, Week, WorkWeek]
  }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";

  .e-textlabel {
    font-weight: bold;
    padding-right: 5px;
  }
  .custom-event-editor td {
    padding: 5px;
  }
  .e-quick-popup-wrapper .e-cell-content {
    padding: 0 10px 10px 10px;
  }
  .e-quick-popup-wrapper .e-cell-content div {
    padding-bottom: 10px;
  }
  .e-quick-popup-wrapper .e-cell-content .e-field {
    border-left-width: 0;
    border-top-width: 0;
    border-right-width: 0;
    height: 25px;
    width: 100%;
  }
  .e-quick-popup-wrapper .e-event-content {
    display: flex;
  }
  .e-quick-popup-wrapper .e-event-header {
    position: absolute;
    right: 0;
  }
  .e-quick-popup-wrapper .e-cell-footer .e-event-create,
  .e-quick-popup-wrapper .e-event-footer .e-event-edit {
    position: absolute;
    right: 0;
  }
  .e-quick-popup-wrapper .e-event-content .subject {
    padding-top: 10px;
    padding-left: 10px;
    font-weight: 500;
    font-size: 14px;
  }
</style>

```

{% endtab %}

> The quick popup in adaptive mode can also be customized using `quickInfoTemplates` using `e-device` class.

## More events indicator and popup

When the number of appointments count that lies on a particular time range * default appointment height exceeds the default height of a cell in month view and all other timeline views, a `+ more` text indicator will be displayed at the bottom of those cells. This indicator denotes that the cell contains few more appointments in it and clicking on that will display a popup displaying all the appointments present on that day.

> To disable this option of showing popup with all hidden appointments, while clicking on the text indicator, you can do code customization within the `popupOpen` event.

The same indicator is displayed on all-day row in calendar views such as day, week and work week views alone, when the number of appointment count present in a cell exceeds three. Clicking on the text indicator here will not open a popup, but will allow the expand/collapse option for viewing the remaining appointments present in the all-day row.

The following code example shows how to disable the display of such popups while clicking on the more text indicator.

{% tab template="schedule/editor-window", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule :height='height' :width='width' :views='views' :selectedDate='selectedDate' :currentView='currentView' :eventSettings='eventSettings' :popupOpen='onPopupOpen'>
        </ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { SchedulePlugin, Day, Week, WorkWeek, Month } from '@syncfusion/ej2-vue-schedule';
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);

export default {
  data (){
    return {
      height: '550px',
      width: '100%',
      currentView: 'Month',
      views: ['Day', 'Week', 'WorkWeek', 'Month'],
      eventSettings: {
          dataSource: scheduleData
      },
      selectedDate: new Date(2018, 1, 15),
    }
  },
  methods: {
    onPopupOpen: function(args) {
        if (args.type === 'EventContainer') {
            args.cancel = true;
        }
    }
  },
  provide: {
    schedule: [Day, Week, WorkWeek, Month]
  }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";
</style>

```

{% endtab %}

### How to customize the popup that opens on more indicator

The following code example shows you how to customize the default more indicator popup in which number of events rendered count on the day has been shown in the header.

{% tab template="schedule/editor-window", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule :height='height' :width='width' :views='views' :selectedDate='selectedDate' :eventSettings='eventSettings' :popupOpen='onPopupOpen'></ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { Internationalization } from '@syncfusion/ej2-base';
import { SchedulePlugin, Month } from '@syncfusion/ej2-vue-schedule';
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);

export default {
  data (){
    return {
      height: '550px',
      width: '100%',
      views: ['Month'],
      eventSettings: {
          dataSource: scheduleData
      },
      selectedDate: new Date(2018, 1, 15),
    }
  },
  methods: {
    onPopupOpen: function(args) {
        if (args.type === 'EventContainer') {
            let instance = new Internationalization();
            let date  = instance.formatDate(args.data.date, { skeleton: 'MMMEd' });
            args.element.querySelector('.e-header-date').innerText = date;
            args.element.querySelector('.e-header-day').innerText = 'Event count: ' + args.data.event.length;
        }
    }
  },
  provide: {
    schedule: [Month]
  }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";

  /* csslint ignore:start */
  .e-schedule .e-more-popup-wrapper .e-header-date {
    font-size: 15px !important;
    max-width: 44% !important;
  }
  /* csslint ignore:end */
</style>

```

{% endtab %}

### How to prevent the display of popup when clicking on the more text indicator

It is possible to prevent the display of popup window by passing the value `true` to `cancel` option within the `MoreEventsClick` event.

{% tab template="schedule/editor-window", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule :height='height' :width='width' :views='views' :selectedDate='selectedDate' :currentView='currentView' :eventSettings='eventSettings' :moreEventsClick='onMoreEventsClick'>
        </ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { SchedulePlugin, Day, Week, WorkWeek, Month } from '@syncfusion/ej2-vue-schedule';
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);

export default {
  data (){
    return {
      height: '550px',
      width: '100%',
      currentView: 'Month',
      views: ['Day', 'Week', 'WorkWeek', 'Month'],
      eventSettings: {
          dataSource: scheduleData
      },
      selectedDate: new Date(2018, 1, 15),
    }
  },
  methods: {
    onMoreEventsClick: function(args) {
      args.cancel = true;
    }
  },
  provide: {
    schedule: [Day, Week, WorkWeek, Month]
  }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";
</style>

```

{% endtab %}

### How to navigate Day view when clicking on more text indicator

The following code example shows you how to customize the `moreEventsClick` property to navigate to the Day view when clicking on the more text indicator.

{% tab template="schedule/editor-window", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule :height='height' :width='width' :views='views' :selectedDate='selectedDate' :currentView='currentView' :eventSettings='eventSettings' :moreEventsClick='onMoreEventsClick'>
        </ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { SchedulePlugin, Day, Week, WorkWeek, Month } from '@syncfusion/ej2-vue-schedule';
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);

export default {
  data (){
    return {
      height: '550px',
      width: '100%',
      currentView: 'Month',
      views: ['Day', 'Week', 'WorkWeek', 'Month'],
      eventSettings: {
          dataSource: scheduleData
      },
      selectedDate: new Date(2018, 1, 15),
    }
  },
  methods: {
    onMoreEventsClick: function(args) {
      args.isPopupOpen = false;
    }
  },
  provide: {
    schedule: [Day, Week, WorkWeek, Month]
  }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";
</style>

```

{% endtab %}