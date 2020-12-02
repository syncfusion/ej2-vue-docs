---
title: "Enable/Disable Tree Grid and its actions"
component: "TreeGrid"
description: "Learn how to Enable/Disable Tree Grid and its actions."
---

# Enable/Disable Tree Grid and its actions

You can enable/disable the Tree Grid and its actions by applying/removing corresponding CSS styles.

To enable/disable the Tree Grid and its actions, follow the given steps:

**Step 1**:

Create CSS class with custom style to override the default style of Tree Grid.

```css
    .disabletreegrid {
        pointer-events: none;
        opacity: 0.4;
    }
    .wrapper {
        cursor: not-allowed;
    }

```

**Step 2**:

Add/Remove the CSS class to the Tree Grid in the click event handler of Button.

```typescript
    btnClick(args) {
      if (this.$refs.treegrid.$el.classList.contains('disablegrid')) {
          this.$refs.treegrid.$el.classList.remove('disablegrid');
          document.getElementById("TreeGridParent").classList.remove('wrapper');
      }
      else {
          this.$refs.treegrid.$el.classList.add('disablegrid');
          document.getElementById("TreeGridParent").classList.add('wrapper');
      }
    }

```

In the below demo, the button click will enable/disable the Tree Grid and its actions.

{% tab template="treegrid/how-to/default" %}

```html

<template>
    <div id="app">
        <div>
            <ejs-button  iconCss="e-icons e-play-icon" cssClass="e-flat" :isPrimary="true" :isToggle="true" v-on:click.native="btnClick">Enable/Disable Grid</ejs-button>
            <div id="TreeGridParent">
              <ejs-treegrid :dataSource="data" :treeColumnIndex="1" height='210px' childMapping="subtasks" ref="treegrid" :editSettings="editSettings" :toolbar="toolbar">
               <e-columns>
                <e-column field="taskID" :isPrimaryKey="true" headerText="Task ID" width="70" textAlign="Right"></e-column>
                <e-column field="taskName" headerText="Task Name" width="100"></e-column>
                <e-column field="startDate" headerText="Start Date" format="yMd" width="90" textAlign="Right"></e-column>
                <e-column field="endDate" headerText="End Date" width="100" format="yMd" textAlign="Right"></e-column>
                <e-column field="duration" headerText="Duration" width="90" textAlign="Right"></e-column>
               </e-columns>
              </ejs-treegrid>
            </div>
        </div>
    </div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page, Toolbar, Edit } from "@syncfusion/ej2-vue-treegrid";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { sampleData } from './datasource.js';

Vue.use(TreeGridPlugin);
Vue.use(ButtonPlugin);

export default {
  data() {
    return {
      data: sampleData,
      editSettings: { allowAdding:true, allowDeleting:true, allowEditing: true },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel']
    };
  },
  methods: {
    btnClick(args) {
      if (this.$refs.treegrid.$el.classList.contains('disabletreegrid')) {
          this.$refs.treegrid.$el.classList.remove('disabletreegrid');
          document.getElementById("TreeGridParent").classList.remove('wrapper');
      }
      else {
          this.$refs.treegrid.$el.classList.add('disabletreegrid');
          document.getElementById("TreeGridParent").classList.add('wrapper');
      }
    }
  },
  provide: {
    treegrid: [Page, Edit, Toolbar]
  }
}
</script>
<style>
  .disabletreegrid {
    pointer-events: none;
    opacity: 0.4;
  }
  .wrapper {
    cursor: not-allowed;
  }
</style>

```

{% endtab %}
