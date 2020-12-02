# Create Dual List from ListView

The dual list contains two ListView. This allows you to move list items from one list to another using the client-side
events. This section explains how to integrate the ListView component to achieve dual list.

## Use cases

* Stock exchanges of two different countries
* Job applications (skill sets)

### Integration of Dual List

Here, two ListView components have been used to display the list items. An ej2-button is used to transfer data between
the ListView, and a textbox is used to achieve the UI of filtering support.

The dual list supports:

* Moving whole data from one list to another.
* Moving selected data from one list to another.
* Filtering the list by using a client-side typed character.

In the ListView component, sorting is enabled using the
[`sortOrder`](https://ej2.syncfusion.com/vue/documentation/api/list-view/#sortorder) property, and
the [select](https://ej2.syncfusion.com/vue/documentation/api/list-view/#select) event is triggered
while selecting an item. Here, the select event is triggered to enable and disable button states.

### Manipulating data

### Moving whole data from the first list to the second list(>>)

* Here, the whole data can be moved from the first ListView to the second by clicking the first button. When clicking the button,
the whole list items are sliced, and `concat` with the second ListView. This button is enabled only when the data source
of the first ListView is not empty.

### Moving whole data from the second list to the first list(<<)

* The functionality of the second button is the same as above, and data is transferred from the second list to the first
list. This button is enabled only when the data source of the second ListView is not empty.

### Moving selected item from one list to another list (>) and (<)

* The [Select](https://ej2.syncfusion.com/vue/documentation/api/list-view/#select) event is triggered
when selecting a list item in the ListView. The selected items can be transferred between two lists. These buttons will be
enabled when selecting an item in lists.

### Filtering method

* The filtering method is used to filter list items when typing a character in the text box. In this
method, the [`dataManager`](https://ej2.syncfusion.com/vue/documentation/data/getting-started/) has been
used to fetch data from the data source and display in ListView.

### Sorting

* By using the dual list, list items can be sorted in the ListView component using the
[`sortOrder`](https://ej2.syncfusion.com/vue/documentation/api/list-view/#sortorder) property.
You can enable sorting in one ListView; in the same order, data can be transferred to another ListView.

{% tab template="listview/checklist", isDefaultActive=true %}

```html
<template>
 <div>
            <div id="text1">
            <input ref='textboxEle' class="e-input" type="text" id="firstInput" placeholder="Filter" title="Type in a name" @keyup="onFirstKeyUp" />
              </div>
            <ejs-listview ref='firstListObj' id='list-1' :dataSource='firstListData' :fields='fields' sortOrder='Ascending' :select="onFirstListSelect"></ejs-listview>
             <div id="btn">
             <ejs-button ref='firstBtnObj' id="firstBtn" @click.native="firstbtnclick"> >> </ejs-button>
             <ejs-button ref='secondBtnObj' id="secondBtn" :disabled='disabled' @click.native="secondbtnclick"> > </ejs-button>
             <ejs-button ref='thirdBtnObj' id="thirdBtn" :disabled='disabled' @click.native="thirdbtnclick"> < </ejs-button>
             <ejs-button ref='fourthBtnObj' id="fourthBtn" @click.native="fourthbtnclick"> << </ejs-button>
             </div>

            <div id="text2">
            <input ref='textEle' class="e-input" type="text" id="secondInput" placeholder="Filter" title="Type in a name" @keyup="onSecondKeyUp" />
            </div>
            <ejs-listview ref='secondListObj' id='list-2' :dataSource='secondListData' :fields='fields' sortOrder='Ascending' :select="onSecondListSelect"></ejs-listview>
</div>
</template>
<style>
#list-1,
    #list-2 {
        width: 40%;
        height: 430px;
        box-shadow: 0 1px 4px #ddd;
        border-bottom: 1px solid #ddd;
    }
    #firstList, #secondList {
        margin-top: 13px;
    }

    .e-btn {
        width: 60px;
        height: 60px;
        margin-bottom: 15px;
    }

    #btn {
        float: left;
        width: 5%;
        padding-left: 30px;
        margin-top: 67px;
    }

    #list-1 {
        float: left;
    }

    #list-2 {
        float: right;
    }
    #firstInput {
        width: 40%;
    }
    #secondInput {
      margin-left: 102px;
      width: 51.4%;
    }
    #text2 {
        margin-top: -23px;
        margin-left: 194px;
    }
</style>
<script>
import Vue from "vue";
import { ListViewPlugin } from "@syncfusion/ej2-vue-lists";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { enableRipple } from '@syncfusion/ej2-base';
import { DataManager, Query, ODataV4Adaptor } from "@syncfusion/ej2-data";
enableRipple(true);
Vue.use(ListViewPlugin);
Vue.use(ButtonPlugin);

Vue.use(ListViewPlugin);
export default {
  data: function() {
      return {
      firstListData: [
  { text: "Hennessey Venom", id: "list-01" },
  { text: "Bugatti Chiron", id: "list-02" },
  { text: "Bugatti Veyron Super Sport", id: "list-03" },
  { text: "SSC Ultimate Aero", id: "list-04" },
  { text: "Koenigsegg CCR", id: "list-05" },
  { text: "McLaren F1", id: "list-06" }
],
secondListData : [
    { text: 'Aston Martin One- 77', id: 'list-07' },
    { text: 'Jaguar XJ220', id: 'list-08' },
    { text: 'McLaren P1', id: 'list-09' },
    { text: 'Ferrari LaFerrari', id: 'list-10' },
  ],
      fields:  {text: "text", id: "id" },
      disabled: true
    };
  },
  mounted: function(){
      this.firstListData = this.$refs.firstListObj.dataSource.slice();
      this.secondListData = this.$refs.secondListObj.dataSource.slice();
  },
  methods: {
    firstbtnclick: function() {
        this.$refs.secondListObj.dataSource = Array.prototype.concat.call(this.$refs.firstListObj.dataSource, this.$refs.secondListObj.dataSource);
        this.$refs.secondListObj.dataBind();
        this.updateFirstListData();
        this.$refs.firstListObj.removeMultipleItems(this.$refs.firstListObj.$el.ej2_instances[0].liCollection);
        this.firstListData = this.firstListData.concat(this.$refs.firstListObj.dataSource);
        this.secondListData = this.$refs.secondListObj.dataSource.slice();
        this.$refs.firstBtnObj.$el.disabled = true;
        this.onFirstKeyUp();
        this.setButtonState();
    },

  secondbtnclick:function() {   //Here, the selected list items are moved to the second list on clicking move button
        let e = this.$refs.firstListObj.getSelectedItems();
        this.$refs.secondListObj.dataSource = Array.prototype.concat.call(this.$refs.secondListObj.dataSource, e.data);
        this.$refs.firstListObj.removeItem(e.item);
        this.firstListData = this.$refs.firstListObj.dataSource;
        this.secondListData = this.$refs.secondListObj.dataSource.slice();
        this.onFirstKeyUp();
        this.$refs.secondBtnObj.$el.disabled = true;
        this.setButtonState();
    },

   thirdbtnclick: function() {  //Here, the selected list items are moved to the first list on clicking move button
        let e = this.$refs.secondListObj.getSelectedItems();
        this.$refs.firstListObj.dataSource = Array.prototype.concat.call(this.$refs.firstListObj.dataSource, e.data);
        this.$refs.secondListObj.removeItem(e.item);
        this.secondListData = this.$refs.secondListObj.dataSource;
        this.firstListData = this.$refs.firstListObj.dataSource.slice();
        this.onSecondKeyUp();
        this.$refs.thirdBtnObj.$el.disabled = true;
        this.setButtonState();

    },

   fourthbtnclick: function() {   //Here, all list items are moved to the first list on clicking move all button
        this.$refs.firstListObj.dataSource = Array.prototype.concat.call(this.$refs.firstListObj.dataSource, this.$refs.secondListObj.dataSource);
        this.updateSecondListData();
        this.$refs.secondListObj.removeMultipleItems(this.$refs.secondListObj.$el.ej2_instances[0].liCollection);
        this.secondListData = this.secondListData.concat(this.$refs.secondListObj.dataSource);
        this.firstListData = this.$refs.firstListObj.dataSource.slice();
        this.onSecondKeyUp();
        this.setButtonState();

    },

    updateFirstListData: function() {  //Here, the ListView data source is updated to the first list
        Array.prototype.forEach.call(this.$refs.firstListObj.$el.ej2_instances[0].liCollection, (list) => {
            this.firstListData.forEach((data, index) => {
                if (list.innerText.trim() === data.text) {
                  this.firstListData.splice(index, 1)
                }
            });
        });
        this.$refs.textboxEle.value= '';
        let ds = [];
        this.firstListData.forEach((data) => {
            ds.push(data);
        });
        this.firstListData = ds;

    },

    //Here, the ListView dataSource is updated for the second list
    updateSecondListData: function() {
        Array.prototype.forEach.call(this.$refs.secondListObj.$el.ej2_instances[0].liCollection, (list) => {
            this.secondListData.forEach((data, index) => {
                if (list.innerText.trim() === data.text){
                    this.secondListData.splice(index, 1);
                }
            });
        });
        this.$refs.textEle.value = '';
        let ds = [];
        this.secondListData.forEach((data) => {
            ds.push(data);
        });
        this.secondListData = ds;

    },
    onFirstListSelect: function() {
        this.$refs.secondBtnObj.disabled = false;
    },
    onSecondListSelect: function() {
        this.$refs.thirdBtnObj.disabled = false;
    },
    //Here, filtering is handled using the dataManager for the first list
    onFirstKeyUp: function(e) {
        let value = this.$refs.textboxEle.value;
        let data = new DataManager(this.firstListData).executeLocal(new Query().where('text', 'startswith', value, true));
        if (!value) {
            this.$refs.firstListObj.dataSource = this.firstListData.slice();
        } else {
            this.$refs.firstListObj.dataSource = data;
        }
    },
    //Here, filtering is handled using the dataManager for the second list
     onSecondKeyUp:function(e) {
        let value =this.$refs.textEle.value;
        let data = new DataManager(this.secondListData).executeLocal(new Query().where('text', 'startswith', value, true));
        if (!value) {
            this.$refs.secondListObj.dataSource = this.secondListData.slice();
        } else {
            this.$refs.secondListObj.dataSource = data;
        }
    },
    //Here, the state of the button is changed
    setButtonState: function() {
        if (this.$refs.firstListObj.dataSource.length) {
            this.$refs.firstBtnObj.$el.disabled = false;
        } else {
            this.$refs.firstBtnObj.$el.disabled = true;
            this.$refs.secondBtnObj.$el.disabled = true;
        }

        if (this.$refs.secondListObj.dataSource.length) {
            this.$refs.fourthBtnObj.$el.disabled = false;
        } else {
            this.$refs.fourthBtnObj.$el.disabled = true;
            this.$refs.thirdBtnObj.$el.disabled = true;
        }

    }
  }
}
</script>
```

{% endtab %}