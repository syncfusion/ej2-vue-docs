---
title: "Create wizard using Accordion"
component: "Accordion"
description: "This online shopping example demonstrates how to create multiple components inside the Essential JS 2 Accordion control."
---

# Create wizard using Accordion

Accordion items can be disabled dynamically by passing the index and boolean value with the [`enableItem`](../../api/accordion#enableitem) method.

The below Wizard sample is designed for Online Shopping model. In this, each Accordion item is integrated with required components to fill
the details and designed for getting user details and making payment at the end. Each field is provided with validation for all mandatory
option to enable/disable to next Accordion.

{% tab template="accordion/how-to/accordion-wizard", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <div id="Sign_In_Form" style="display:none; padding: 3px 0">
       <form id="formId">
           <div class="form-group">
               <div class="e-float-input">
                   <input type="text" id="email" name="Email" required="" />
                   <span class="e-float-line"></span>
                   <label class="e-float-text" for="email">Email</label>
               </div>
               <div class="e-float-input">
                   <input id="password" type="password" name="Password" required="" />
                   <span class="e-float-line"></span>
                   <label class="e-float-text" for="password">Password</label>
               </div>
           </div>
       </form>
       <div style="text-align: center">
           <button class='e-btn' id="Continue_Btn" >Continue</button>
           <div id="err1">* Please fill all fields</div>
       </div>
   </div>
   <div id="Address_Fill" style="display:none; padding: 3px 0">
       <form id="formId_Address">
           <div class="form-group">
               <div class="e-float-input">
                   <input type="text" id="name" name="Name" required="" />
                   <span class="e-float-line"></span>
                   <label class="e-float-text" for="name">Name</label>
               </div>
           </div>
           <div class="form-group">
               <div class="e-float-input">
                   <input type="text" id="address" name="Address" required="" />
                   <span class="e-float-line"></span>
                   <label class="e-float-text" for="address">Address</label>
               </div>
           </div>
           <div class="form-group">
               <ejs-numerictextbox id="mobile" format='0' placeholder='Mobile' floatLabelType='Auto' showSpinButton=false></ejs-numerictextbox>
           </div>
       </form>
       <div style="text-align: center">
           <button class='e-btn' id="Continue_BtnAdr" >Continue</button>
           <div id="err2">* Please fill all fields</div>
       </div>
   </div>
   <div id="Card_Fill" style="display:none; padding: 3px 0;">
       <div class="col-xs-6 col-sm-6 col-lg-6 col-md-6">
           <div class="form-group">
               <ejs-numerictextbox id="cardNo" format='0' placeholder='Card No' floatLabelType='Auto' showSpinButton=false></ejs-numerictextbox>
           </div>
       </div>
       <div class="col-xs-6 col-sm-6 col-lg-6 col-md-6">
           <div class="form-group">
               <div class="e-float-input">
                   <input type="text" id="cardHolder" name="cardHolder" required="" />
                   <span class="e-float-line"></span>
                   <label class="e-float-text" for="cardHolder">CardHolder Name</label>
               </div>
           </div>
       </div>
       <div class="col-xs-6 col-sm-6 col-lg-6 col-md-6">
           <ejs-datepicker id="expiry" width='100%' format='MM/yyyy' placeholder='Expiry Date' floatLabelType='Auto' ></ejs-datepicker>
       </div>
       <div class="col-xs-6 col-sm-6 col-lg-6 col-md-6">
           <div class="form-group">
               <ejs-numerictextbox id="CVV" format='0' placeholder='CVV' floatLabelType='Auto' showSpinButton=false></ejs-numerictextbox>
           </div>
       </div>
       <div style="text-align: center">
           <button class='e-btn' id="Back_Btn" >Back</button>
           <button class='e-btn' id="Save_Btn" >Save</button>
           <div id="err3">* Please fill all fields</div>
       </div>
   </div>
   <ejs-dialog ref="alertDlg" header='Alert' width=200 isModal=true content='' visible=false :target='dlgTarget' :buttons='dlgButtons' ></ejs-dialog>
   <ejs-accordion ref="accordionInc" :expanding='expanding'>
       <e-accordionitems>
           <e-accordionitem expanded='true' header='Sign In' content='#Sign_In_Form'></e-accordionitem>
           <e-accordionitem header='Delivery Address' content='#Address_Fill'></e-accordionitem>
           <e-accordionitem header='Card Details' content='#Card_Fill'></e-accordionitem>
       </e-accordionitems>
   </ejs-accordion>
     </div>
</template>
<script>
import Vue from 'vue';
import { AccordionPlugin } from '@syncfusion/ej2-vue-navigations';
import {Accordion, ExpandEventArgs, AccordionClickArgs} from '@syncfusion/ej2-navigations';
import { DialogPlugin} from '@syncfusion/ej2-vue-popups';
import { DatePickerPlugin } from '@syncfusion/ej2-vue-calendars';
import { NumericTextBoxPlugin } from '@syncfusion/ej2-vue-inputs';
Vue.use(AccordionPlugin);
Vue.use(DialogPlugin);
Vue.use(DatePickerPlugin);
Vue.use(NumericTextBoxPlugin);
export default {
  name: 'app',
    data(){
        return {
     dlgButtons: [{
       buttonModel: { content: 'Ok', isPrimary: true },
       click: (() => {
         this.$refs.alertDlg.ej2Instances.hide();
          var obj1 = this.$refs.accordionInc.ej2Instances;
         if (obj1.expandedItems[0] === 2 && obj.content === success) {
           obj1.enableItem(0, true);
           obj1.enableItem(1, false);
           obj1.enableItem(2, false);
           obj1.expandItem(true, 0);
         }
       })
     }];
     dlgTarget : document.body;
       };
     },
  methods:{
     checkMail:function(mail) {
     if (/^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(mail)) {
       return (true);
     } else {

       this.$refs.alertDlg.ej2Instances.content = 'Enter valid email address'
       this.$refs.alertDlg.ej2Instances.show();
       return (false);
     }
   }

    checkMobile: function(mobile) {
     if (mobile.match(/^\d{10}$/)) {
       return (true);
     } else {
       this.$refs.alertDlg.ej2Instances.content = 'Mobile number length should be 10'
       this.$refs.alertDlg.ej2Instances.show();
       return (false);
     }
   }

    checkCardNo:function(cardNo) {
     if (cardNo.match(/^\d{16}$/)) {
       return (true);
     } else {
       this.$refs.alertDlg.ej2Instances.content = 'Card number length should be 16'
       this.$refs.alertDlg.ej2Instances.show();
       return (false);
     }
   }

    checkCVV:function(cvv) {
     if (cvv.match(/^\d{3}$/)) {
       return (true);
     } else {
       this.$refs.alertDlg.ej2Instances.content = 'CVV number length should be 3'
       this.$refs.alertDlg.ej2Instances.show();
       return (false);
     }
   }

    expanding:function(e) {

     if (e.name === 'expanding' && [].indexOf.call(this.$refs.accordionInc.ej2Instances.items, e.item) === 0) {
       document.getElementById('Continue_Btn').onclick = (e) => {
         var email = document.getElementById('email');
         var password = document.getElementById('password');
         if (email.value !== '' && password.value !== '') {
           if (this.checkMail(email.value)) {
             email.value = password.value = '';
             var acrdnObj = this.$refs.accordionInc.ej2Instances;
             acrdnObj.enableItem(1, true);
             acrdnObj.enableItem(0, false);
             acrdnObj.expandItem(true, 1);
           }
           document.getElementById('err1').classList.remove('show');
         } else {
           document.getElementById('err1').classList.add('show');
         }
       }
     } else if (e.name === 'expanding' && [].indexOf.call(this.$refs.accordionInc.ej2Instances.items, e.item) === 1) {
       document.getElementById('Continue_BtnAdr').onclick = (e) => {
         var name = document.getElementById('name');
         var address = document.getElementById('address');
         var mobile = document.getElementById('mobile');
         if ((name.value !== '') && (address.value !== '') && (mobile.value !== '')) {
           if (this.checkMobile(mobile.value)) {
             var acrdnObj = this.$refs.accordionInc.ej2Instances;
             acrdnObj.enableItem(2, true);
             acrdnObj.enableItem(1, false);
             acrdnObj.expandItem(true, 2);
           }
           document.getElementById('err2').classList.remove('show');
         } else {
           document.getElementById('err2').classList.add('show');
         }
       }
     } else if (e.name === 'expanding' && [].indexOf.call(this.$refs.accordionInc.ej2Instances.items, e.item) === 2) {
       document.getElementById('Back_Btn').onclick = (e) => {
         acrdnObj = this.$refs.accordionInc.ej2Instances;
         acrdnObj.enableItem(1, true);
         acrdnObj.enableItem(2, false);
         acrdnObj.expandItem(true, 1);
       }
       document.getElementById('Save_Btn').onclick = (e) => {
         var cardHolder = document.getElementById('cardHolder');
         var expiry = document.getElementById('expiry');
         var cardNo = document.getElementById('cardNo');
         var cvv = document.getElementById('CVV');
         if ((cardNo.value !== '') && (cardHolder.value !== '') && (expiry.value !== '') && (cvv.value !== '')) {
           if (this.checkCardNo(cardNo.value)) {
             if (this.checkCVV(cvv.value)) {
               this.$refs.alertDlg.ej2Instances.content = 'Your payment successfully processed'
               this.$refs.alertDlg.ej2Instances.show();
             }
           }
           document.getElementById('err3').classList.remove('show');
         } else {
           document.getElementById('err3').classList.add('show');
         }
       }
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
</style>
```

{% endtab %}