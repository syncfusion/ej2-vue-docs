---
title: "Recurrence Editor | VueJS Scheduler"
component: "Scheduler"
description: "This section demonstrates the options available in recurrence editor and how to use its available methods separately in an application."
---

# Recurrence editor

The Recurrence editor is integrated into Scheduler editor window by default, to process the recurrence rule generation for events. Apart from this, it can also be used as an individual component referring from the Scheduler repository to work with the recurrence related processes.

> All the valid recurrence rule string mentioned in the [iCalendar](https://tools.ietf.org/html/rfc5545#section-3.3.10) specifications are applicable to use with the recurrence editor.

## Customizing the repeat type option in editor

By default, there are 5 types of repeat options available in recurrence editor such as,

* Never
* Daily
* Weekly
* Monthly
* Yearly

It is possible to customize the recurrence editor to display only the specific repeat options such as `Daily` and `Weekly` options alone by setting the appropriate `frequencies` option.

{% tab template="schedule/recurrence", iframeHeight="588px" %}

```html
<template>
  <div id='app'>
    <div id='container'>
      <ejs-schedule height='550px' width='100%' :selectedDate='selectedDate'
      :eventSettings='eventSettings' :popupOpen='onPopupOpen'>
      </ejs-schedule>
    </div>
  </div>
</template>
<script>
  import Vue from 'vue';
  import { scheduleData } from './datasource.js';
  import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-vue-schedule';

  Vue.use(SchedulePlugin);

  export default {
    data () {
      return {
        selectedDate: new Date(2018, 1, 15),
        eventSettings: { dataSource: scheduleData }
      }
    },
    methods: {
        onPopupOpen: function(args) {
            if (args.type == 'Editor') {
                let recurrenceEditorObj =
                    args.element.querySelector('.e-recurrenceeditor').ej2_instances[0];
                recurrenceEditorObj.frequencies = ['none', 'daily', 'weekly'];
            }
        }
    },
    provide: {
      schedule: [ Day, Week, WorkWeek, Month, Agenda]
    }
  }
</script>
<style>
@import '../../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-calendars/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css';
</style>
```

{% endtab %}

The other properties available in recurrence editor are tabulated below,

| Properties | Type | Description |
|------------|------|-------------|
| firstDayOfWeek | number | Sets the first day of the week on recurrence editor.|
| startDate | Date | Sets the start date from which date the recurrence event starts. |
| dateFormat | string | Sets the specific date format on recurrence editor.|
| locale | string | Sets the locale to be applied on recurrence editor.|
| cssClass | string | Allows styling to be applied on recurrence editor with custom class names.|
| enableRtl | boolean | Allows recurrence editor to render in RTL mode.|
| minDate | Date | Sets the minimum date on recurrence editor.|
| maxDate | Date | Sets the maximum date on recurrence editor.|
| value | string | Sets the recurrence rule value on recurrence editor. |
| selectedType | number | Sets the specific repeat type on the recurrence editor.|

## Accessing the recurrence rule string

The recurrence rule is usually generated based on the options selected from the recurrence editor and also it follows the [`iCalendar`](https://tools.ietf.org/html/rfc5545#section-3.3.10) specifications. The generated recurrence rule string is a valid one to be used with the Scheduler event’s recurrence rule field.

There is a `change` event available in recurrence editor, that triggers on every time the fields of recurrence editor tends to change. Within this event argument, you can access the generated recurrence value through the `value` option as shown in the following code example.

{% tab template="schedule/recur-editor", iframeHeight="588px" %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <div style='padding-bottom:15px;'>
            <label>Rule Output</label>
                <div class='rule-output-container'>
                    <div id='rule-output'></div>
                </div>
            </div>
        <ejs-recurrenceeditor :selectedType='selectedType' :change='onChange'></ejs-recurrenceeditor>
    </div>
  </div>
</template>
<script>
  import Vue from 'vue';
  import { RecurrenceEditorPlugin } from '@syncfusion/ej2-vue-schedule';

  Vue.use(RecurrenceEditorPlugin);

  export default {
    data () {
      return {
        selectedType: 1  
      }
    },
    mounted: function () {
        let outputElement = document.querySelector('#rule-output');
        outputElement.innerText = 'Select Rule';
    },
    methods: {
        onChange: function(args) {
            let outputElement = document.querySelector('#rule-output');
            if(args.value == "") {
                outputElement.innerText = 'Select Rule';
            } else {
                outputElement.innerText = args.value;
            }
        }
    }
  }
</script>
<style>
@import '../../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-calendars/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css';

.recurrence-editor-wrap {
        margin: 0 25%;
    }

    .rule-output-container {
        height: auto;
        border: 1px solid #969696;
    }

    #rule-output {
        padding: 8px 4px;
        text-align: center;
        min-height: 20px;
        overflow: hidden;
        overflow-wrap: break-word;
    }

    @media (max-width: 580px) {
        .recurrence-editor-wrap {
            margin: 0 5%;
        }
    }
</style>
```

{% endtab %}

## Set specific value on recurrence editor

It is possible to display the recurrence editor with specific options loaded initially, based on the rule string that we provide. The fields of recurrence editor will change its values accordingly, when we provide a particular rule through the `setRecurrenceRule` method.

{% tab template="schedule/recur-editor", iframeHeight="588px" %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <div style='padding-bottom:15px;'>
            <label>Rule Output</label>
                <div class='rule-output-container'>
                    <div id='rule-output'></div>
                </div>
            </div>
        <ejs-recurrenceeditor id='editor' ref='EditorObj' :selectedType='selectedType' :change='onChange'></ejs-recurrenceeditor>
    </div>
  </div>
</template>
<script>
  import Vue from 'vue';
  import { RecurrenceEditorPlugin } from '@syncfusion/ej2-vue-schedule';

  Vue.use(RecurrenceEditorPlugin);

  export default {
    data () {
      return {
        selectedType: 1  
      }
    },
    mounted: function () {
        let recObject = this.$refs.EditorObj;
        recObject.setRecurrenceRule('FREQ=DAILY;INTERVAL=2;COUNT=8');
    },
    methods: {
        onChange: function(args) {
            let outputElement = document.querySelector('#rule-output');
            outputElement.innerText = args.value;
        }
    }
  }
</script>
<style>
@import '../../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-calendars/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css';

.recurrence-editor-wrap {
        margin: 0 25%;
    }

    .rule-output-container {
        height: auto;
        border: 1px solid #969696;
    }

    #rule-output {
        padding: 8px 4px;
        text-align: center;
        min-height: 20px;
        overflow: hidden;
        overflow-wrap: break-word;
    }

    @media (max-width: 580px) {
        .recurrence-editor-wrap {
            margin: 0 5%;
        }
    }
</style>
```

{% endtab %}

## Recurrence date generation

You can parse the `recurrenceRule` of an event to generate the date instances on which that particular event is going to occur, using the `getRecurrenceDates` method. It generates the dates based on the `recurrenceRule` that we provide. The parameters to be provided for `getRecurrenceDates` method are as follows.

| Field name | Type | Description |
|------------|------|-------------|
| `startDate` | Date| Appointment start date. |
| `rule` | String| Recurrence rule present in an event object. |
| `excludeDate` | String | Date collection (in ISO format) to be excluded. It is **optional**. |
| `maximumCount` | Number | Number of date count to be generated. It is **optional**. |
| `viewDate` | Date | Current view range's first date. It is **optional**. |

{% tab template="schedule/recur-editor", iframeHeight="588px" %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <div style='padding-bottom:15px;'>
            <label id='rule-label'>Rule Output</label>
                <div class='rule-output-container'>
                    <div id='rule-output'></div>
                </div>
            </div>
        <ejs-recurrenceeditor id='editor' style="display: none;" ref='EditorObj' :selectedType='selectedType'>
        </ejs-recurrenceeditor>
    </div>
  </div>
</template>
<script>
  import Vue from 'vue';
  import { RecurrenceEditorPlugin } from '@syncfusion/ej2-vue-schedule';
  import { createElement } from '@syncfusion/ej2-base';

  Vue.use(RecurrenceEditorPlugin);

  export default {
    data () {
      return {
        selectedType: 1  
      }
    },
    mounted: function () {
        let recObject = this.$refs.EditorObj;
        let outputElement = document.querySelector('#rule-output');
        let labelElement = document.querySelector('#rule-label');
        let dates = recObject.getRecurrenceDates(new Date(2018, 0, 7, 10, 0), 'FREQ=DAILY;INTERVAL=1', '20180108T114224Z,20180110T114224Z', 4, new Date(2018, 0, 7));
        labelElement.innerText = 'Date Collections';
        outputElement.innerHTML = '';
        for (let index = 0; index < dates.length; index++) {
              outputElement.appendChild(createElement('div', { innerHTML: new Date(dates[index]).toString() }));
        }
    }
  }
</script>
<style>
@import '../../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-calendars/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css';

.recurrence-editor-wrap {
    margin: 0 25%;
}

.rule-output-container {
    height: auto;
    border: 1px solid #969696;
}

#rule-output {
    padding: 8px 4px;
    text-align: center;
    min-height: 20px;
    overflow: hidden;
    overflow-wrap: break-word;
}

@media (max-width: 580px) {
    .recurrence-editor-wrap {
        margin: 0 5%;
    }
}
</style>
```

{% endtab %}

> Above example will generate two dates January 7, 2018 & January 9 2018 by excluding the in between dates January 8 2018 & January 10 2018, since those dates were given in the exclusion list. Generated dates can then be utilised to create appointments.

## Recurrence date generation in server-side

It is also possible to generate recurrence date instances from server-side by manually referring the `RecurrenceHelper` class, which is specifically written and referred from application end to handle this date generation process.

> Refer [here](https://www.syncfusion.com/kb/10009/how-to-parse-the-recurrencerule-at-server-side) for the step by step procedure to achieve date generation in server-side.

## Restrict date generation with specific count

In case, if the rule is given in "NEVER ENDS" category, then you can mention the maximum count when you actually want to stop the date generation starting from the provided start date. To do so, provide the appropriate `maximumCount` value within the `getRecurrenceDates` method as shown in the following code example.

{% tab template="schedule/recur-editor", iframeHeight="588px" %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <div style='padding-bottom:15px;'>
            <label id='rule-label'>Rule Output</label>
                <div class='rule-output-container'>
                    <div id='rule-output'></div>
                </div>
            </div>
        <ejs-recurrenceeditor id='editor' style="display: none;" ref='EditorObj' :selectedType='selectedType'>
        </ejs-recurrenceeditor>
    </div>
  </div>
</template>
<script>
  import Vue from 'vue';
  import { RecurrenceEditorPlugin } from '@syncfusion/ej2-vue-schedule';
  import { createElement } from '@syncfusion/ej2-base';

  Vue.use(RecurrenceEditorPlugin);

  export default {
    data () {
      return {
        selectedType: 1  
      }
    },
    mounted: function () {
        let recObject = this.$refs.EditorObj;
        let outputElement = document.querySelector('#rule-output');
        let labelElement = document.querySelector('#rule-label');
        let dates = recObject.getRecurrenceDates(new Date(2018, 0, 7, 10, 0), 'FREQ=DAILY;INTERVAL=1; COUNT=30', '20180108T114224Z,20180110T114224Z', 10, new Date(2018, 0, 7));
        labelElement.innerText = 'Date Collections';
        outputElement.innerHTML = '';
        for (let index = 0; index < dates.length; index++) {
              outputElement.appendChild(createElement('div', { innerHTML: new Date(dates[index]).toString() }));
        }
    }
  }
</script>
<style>
@import '../../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-calendars/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css';

.recurrence-editor-wrap {
    margin: 0 25%;
}

.rule-output-container {
    height: auto;
    border: 1px solid #969696;
}

#rule-output {
    padding: 8px 4px;
    text-align: center;
    min-height: 20px;
    overflow: hidden;
    overflow-wrap: break-word;
}

@media (max-width: 580px) {
    .recurrence-editor-wrap {
        margin: 0 5%;
    }
}
</style>
```

{% endtab %}