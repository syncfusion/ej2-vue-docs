---
title: "Add nested Tabs"
component: "Tab"
description: "This example demonstrates how to create the Essential JS 2 Tab control inside another Essential JS 2 Tab control."
---

# Add nested Tabs

Tab supports to render the nested level of Tabs by using `content` property. You can add the nested Tab element inside the parent Tab `content`
 property. To render the nested Tab, initialize the component using the id of Tab from a selected event handler.

{% tab template="tab/how-to/nested-tab", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <ejs-tab ref='element'  :selected= "handleSelectEvent">
    <e-tabitems>
              <e-tabitem :header='headerText0' :content="content0"></e-tabitem>
              <e-tabitem :header='headerText1' :content="content1"></e-tabitem>
              <e-tabitem :header='headerText2' :content="content2"></e-tabitem>
    <e-tabitems>
    </ejs-tab>
  </div>
</template>
<script>
import Vue from 'vue';
import { TabPlugin } from '@syncfusion/ej2-vue-navigations';
import { Tab, TabComponent, SelectEventArgs } from '@syncfusion/ej2-navigations';
import { enableRipple, isNullOrUndefined as isNOU } from '@syncfusion/ej2-base';
Vue.use(TabPlugin);
export default {
  name: 'app',
   data: function(){
        return {
          headerText0: { text: 'USA' },
          headerText1: { text: 'France' },
          headerText2: { text: 'Australia' },

         content0: '<div id="usa_tab"></div>',
         content1: '<div id="france_tab"></div>',
         content2: '<div id="australia_tab"></div>',
}

  },methods:{


handleSelectEvent: function(e) {
  if (e.selectedIndex === 0 && isNOU(document.querySelector('#usa_tab.e-tab'))) {
    var usa_obj = new Tab({
       items:[
  {
    header: { 'text': 'New York' },
    content: 'New York City comprises 5 boroughs sitting where the Hudson River meets the Atlantic Ocean. At its core is Manhattan, a densely populated borough that’s among the world’s major commercial, financial and cultural centers. Its iconic sites include skyscrapers such as the Empire State Building and sprawling Central Park. Broadway theater is staged in neon-lit Times Square.'
  },
  {
    header: { 'text': 'Los Angeles' },
    content: 'Los Angeles is a sprawling Southern California city and the center of the nation’s film and television industry. Near its iconic Hollywood sign, studios such as Paramount Pictures, Universal and Warner Brothers offer behind-the-scenes tours. On Hollywood Boulevard, TCL Chinese Theatre displays celebrities’ hand- and footprints, the Walk of Fame honors thousands of luminaries and vendors sell maps to stars’ homes.'
  },
  {
    header: { 'text': 'Chicago' },
    content: 'Chicago, on Lake Michigan in Illinois, is among the largest cities in the U.S. Famed for its bold architecture, it has a skyline punctuated by skyscrapers such as the iconic John Hancock Center, 1,451-ft. Willis Tower (formerly the Sears Tower) and the neo-Gothic Tribune Tower. The city is also renowned for its museums, including the Art Institute of Chicago with its noted Impressionist and Post-Impressionist works.'
  }
]
    }, '#usa_tab');

  } else if (e.selectedIndex === 1 && isNOU(document.querySelector('#france_tab.e-tab'))) {
    var france_obj= new Tab({
       items:[
  {
    header: { 'text': 'Paris' },
    content: 'Paris, France capital, is a major European city and a global center for art, fashion, gastronomy and culture. Its 19th-century cityscape is crisscrossed by wide boulevards and the River Seine. Beyond such landmarks as the Eiffel Tower and the 12th-century, Gothic Notre-Dame cathedral, the city is known for its cafe culture and designer boutiques along the Rue du Faubourg Saint-Honoré.'
  },
  {
    header: { 'text': 'Marseille' },
    content: 'Marseille, a port city in southern France, has been a crossroads of immigration and trade since its founding by the Greeks circa 600 B.C. At its heart is the Vieux-Port (Old Port), where fishmongers sell their catch along the boat-lined quay. Basilique Notre-Dame-de-la-Garde is a Romanesque-Byzantine church. Modern landmarks include Le Corbusier’s influential Cité Radieuse complex and Zaha Hadid’s CMA CGM Tower.'
  },
  {
    header: { 'text': 'Lyon' },
    content: 'Lyon, the capital city in France’s Auvergne-Rhône-Alpes region, sits at the junction of the Rhône and Saône rivers. Its center reflects 2,000 years of history from the Roman Amphithéâtre des Trois Gaules, medieval and Renaissance architecture in Vieux (Old) Lyon, to the modern Confluence district on Presquîle peninsula. Traboules, covered passageways between buildings, connect Vieux Lyon and La Croix-Rousse hill.'
  }
]
    }, '#france_tab');

  } else if (e.selectedIndex === 2 && isNOU(document.querySelector('#australia_tab.e-tab'))) {
    var australia_obj= new Tab({
       items:[
  {
    header: { 'text': 'Sydney' },
    content: 'Sydney, capital of New South Wales and one of Australia largest cities, is best known for its harbourfront Sydney Opera House, with a distinctive sail-like design. Massive Darling Harbour and the smaller Circular Quay port are hubs of waterside life, with the arched Harbour Bridge and esteemed Royal Botanic Garden nearby. Sydney Tower’s outdoor platform, the Skywalk, offers 360-degree views of the city and suburbs.'
  },
  {
    header: { 'text': 'Melbourne' },
    content: 'Melbourne is the coastal capital of the southeastern Australian state of Victoria. At the city centre is the modern Federation Square development, with plazas, bars, and restaurants by the Yarra River. In the Southbank area, the Melbourne Arts Precinct is the site of Arts Centre Melbourne – a performing arts complex – and the National Gallery of Victoria, with Australian and indigenous art.'
  },
  {
    header: { 'text': 'Brisbane' },
    content: 'Brisbane, capital of Queensland, is a large city on the Brisbane River. Clustered in its South Bank cultural precinct are the Queensland Museum and Sciencentre, with noted interactive exhibitions. Another South Bank cultural institution is Queensland Gallery of Modern Art, among Australia major contemporary art museums. Looming over the city is Mt. Coot-tha, site of Brisbane Botanic Gardens.'
  }
]
    }, '#australia_tab');
}
 }
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
</style>
```

{% endtab %}
