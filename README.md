# BellyButton
Roza, from Microbology laboratory wanted a dashboard with the information of voulunteer's belly button specifically their bacterias.

## Overview of Project 
### Purpose 
The purpose of this project is to analyze the bacterias located onto the volunter's bely button. This information will help Roza and the company to know if there are bactererial species that have the ability to synthesize proteins that taste like beef in human body.

### Description of data

For this project, there were used a json file than contained the following information for each volunteer:

* **ID:** A distinct number of the volunteer.
* **Ethnicity:** The Ecthnicity of the volunteer.
* **Gender:** The gender of the volunteer.
* **Age:** The age of the volunteer.
* **Location:** Where the volunteer come from.
* **bbtype:** The bacteria type of the volunteer.
* **Wfreq:** Belly button whashing frecuency. 
* **Otu_ids:** The id of the bacteria species.
* **Sample_values:** the quantity found of the bateria species.
* **Otu_labels:** The name of the bacteria species.


## Results 

The results of the dashboard created are:

**1)** First, there were created the Test Subject ID number, to filter the information of the volunteer showed in the filter.
At the moment the user choose an ID all the uformation (the table and the charts) match with the belly button description of the volunteer.
The table indicated the demographic infomation, ID, Ethnicity, gender, age, location bbtype and Wfreq. Then, there were created a horizontal bar chart to display the top 10 bacterial species (OTUs), as we can observe the it displays the Sample_values asthe values, and the Otu_ids, as the labels.

To create the bar chart, there were created the yticks, slice to 0 to 10 and use teh reverse function to have it in descending order.

    var yticks = otu_ids.slice(0,10).map(id => "OTU" + id).reverse();
       console.log(yticks)

Also to create  the tarce of the bar chart we use slice() and reverse() functions.

      var barData = [{
        x:sample_values.slice(0,10).reverse(),
        y:yticks.slice(0,10).reverse(),
        type: "bar",
        text:otu_labels,
        orientation: 'h'
          }];

The orientation is horizontal, and we define the x, y, type and text and the we create the layouts ad the function to plotly the bar chart.
Also, for the gauge chart there were created a variable named gaugeData, gaugelayout and finally there use plotly to plot the gauge data and gauge layout.

      Plotly.newPlot("gauge", gaugeData,gaugeLayout);
    })

For these two charts there were resulted this:


<img width="913" alt="imagen1" src="https://user-images.githubusercontent.com/96165500/185718485-c173a9b1-2a8f-445f-878c-e12b64b0d11e.png">

Continue with the dashboard, there created a bubble chart below the gauge and bar chart. For the bubble chart, there were created a varivle named bubbleData, bubbleLayout and there were used plotly to plot bubbleData and bubbleLayout. In ths chart, there were defined the otu_ids, the sample values and the otu_labelsto the x, y and text properties, respectively.

       var bubbleData = [{
      x:otu_ids,
      y:sample_values,
      text: otu_labels,
      mode: 'markers',
      marker: {
        size: sample_values,
        color:otu_ids,
        colorscale:'Picnic'
      }
    }];
    
The result of bubble chart was the following:

<img width="830" alt="imagen12png" src="https://user-images.githubusercontent.com/96165500/185718486-2e4b0220-28e5-4174-8002-f541ffc340cd.png">

## Summary

After this working visualization, it will be easily for the company identifies if there a candidate to fabricate synthetic beef and the Roza's volunteers will be able to identify whether that species is found in their navel. These viusally information facilite teh users to find the information needed, and they just must select the volunteer id, and all the information in table and charts will be deploy. Actually, there is only the information they needed to viusalizaed to find the volunteer properties and their navels. In three charts they found the answers and if some volunteer have the bacteria species needed, they can fnd the volunteer easily. To performance a better but simple dashbordthere addded a title and a few information about the project.

##Link

To visualiza the complete dashboard, visit: https://alecano1.github.io/BellyButton/
 

