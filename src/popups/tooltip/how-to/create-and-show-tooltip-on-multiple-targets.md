# Create and show tooltip on multiple targets

Tooltip can be created and shown on multiple targets within a container by defining the specific target elements to the target property. So, the tooltip is initialized only on matched targets within a container.

In this case, the tooltip content is assigned from the title attribute of the target element.

```typescript

<ejs-tooltip target='.e-info' position='RightCenter'>
</ejs-tooltip>

```

{% tab template="tooltip/target", isDefaultActive=true %}

```html
<template>
   <div id='app'>
        <ejs-tooltip target='.e-info' position='RightCenter'>
            <div id="container">
                <form id="details" role="form">
                    <div id="user">
                    <div class="info">User Name:</div>
                    <div class="inputs">
                        <input type="text" ref="uname" id="uname" class="e-info e-input" name="firstname" title="Please enter your name">
                    </div>
                    </div>
                    <br/>
                    <div>
                    <div class="info">Email Address:</div>
                    <div class="inputs">
                        <input type="text" id="mail" class="e-info e-input" name="email" title="Enter a valid email address">
                    </div>
                    </div>
                    <br/>
                    <div>
                    <div class="info">Password:</div>
                        <div class="inputs">
                            <input id="pwd" ref="pwd" type="password" class="e-info e-input" name="password" title="Be at least 8 characters length">
                        </div>
                    </div>
                    <br/>
                    <div>
                    <div class="info">Confirm Password:</div>
                    <div class="inputs">
                        <input id="cpwd" ref="cpwd" type="password" class="e-info e-input" name="Cpwd" title="Re-enter your password">
                    </div>
                    </div>
                    <br/>
                    <div class="btn">
                        <ejs-button id="sample" v-on:click.native='onSubmit'>Submit</ejs-button>
                        <ejs-button id='clear' v-on:click.native='onClear'type='reset'>Reset</ejs-button>
                    </div>
                </form>
            </div>
        </ejs-tooltip>
    </div>
</template>
<style>
@import "node_modules/@syncfusion/ej2-base/styles/material.css";
@import "node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
#container {
    border: 1px solid #ddd;
}

#details .info {
    font-weight: bold;
    width: 165px;
    display: inline-block;
    margin-left: 10px;
}
#details .inputs {
    display: inline-block;
}
#details .btn{
  margin-top: 10px;
  position: relative;
  left: 50%;
  transform: translateX(-50%);
  display: inline-block;
}
#details #sample{
  margin-left:10px;
}
#details #clear{
  margin-left:10px;
}
#details {
  padding-top: 30px;
  padding-bottom: 30px;
  position: relative;
  left: 50%;
  transform: translateX(-50%);
  display: inline-block;
}
</style>
<script>
import Vue from 'vue';
import { TooltipPlugin } from '@syncfusion/ej2-vue-popups';
Vue.use(TooltipPlugin);
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
Vue.use(ButtonPlugin);

export default {
  data: function() {
    return {
    };
  },
  methods: {
    onSubmit:function(args){
    let name = this.$refs.uname.value;
    let pwd = this.$refs.pwd.value;
    let cpwd = this.$refs.cpwd.value;
    if(name.length > 0 & name.length < 4){
        this.$refs.uname.title = 'Required Minimum 4 Characters';
        this.$refs.uname.style.backgroundColor = 'red';
        let target = this.$refs.uname;
        tooltip1.open(target);
    } else {

        this.$refs.uname.style.backgroundColor = 'white';
    }
    if(pwd !== '' && pwd.length < 8){
        this.$refs.pwd.title = 'Required Minimum 8 Characters';
        this.$refs.pwd.style.backgroundColor = 'red';
        let pwdtarget = this.$refs.pwd;
        tooltip3.open(pwdtarget);
    } else {
        this.$refs.pwd.style.backgroundColor = 'white';
    }
    if(name.length >= 4 && pwd !== '' && pwd.length >= 8  &&  pwd == cpwd ){
        alert('Form Submitted');
    } else {
        alert('Details are not Valid');
    }
    },
    onClear:function(args){
        this.$refs.uname.style.backgroundColor = 'white';
        this.$refs.pwd.style.backgroundColor = 'white';
        let target = this.$refs.uname;
        tooltip1.close(target);
        this.$refs.uname.title = 'Please enter your name';
        let pwdtarget = this.$refs.pwd;
        tooltip3.close(pwdtarget);
    }
  }
}
</script>

```

{% endtab %}