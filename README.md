# BellyButton
Roza, from the Microbiology laboratory, wanted a dashboard with the information that was analyzed from samples of hundreds of volunteers to know the species of bacteria that live in their belly buttons.

## Overview of Project 
### Purpose 

The purpose of this project is to analyze the bacteria located on the volunteer's belly button. This information will help Roza and the company to know if there are bacterial species that have the ability to synthesize proteins that taste like beef in the human body.

### Description of data

For this project, there were used a json file than contained the following information for each volunteer:

* **ID:** A distinct number that identifies each volunteer.
* **Ethnicity:** The Ethnicity of the volunteer.
* **Gender:** The gender of the volunteer.
* **Age:** The age of the volunteer.
* **Location:** Where the volunteer comes from.
* **bbtype:** The bacteria type of the volunteer.
* **Wfreq:** Belly button washing frequency. 
* **Otu_ids:** The id of the bacteria species.
* **Sample_values:** The quantity found of the bacteria species.
* **Otu_labels:** The name of the bacteria species.


## Results 

The results of the dashboard created are:

The results of the dashboard created are:

First, there was created a filter in "Test Subject ID no", to filter the information of the volunteer indicated.
At the moment the user chooses an ID, all the information (the table and the charts) matches with the volunteer and their belly button description.

The table indicates the demographic information, ID, Ethnicity, gender, age, location bbtype, and Wfreq. Then, there was created a horizontal bar chart to display the top 10 bacterial species (OTUs), as we can observe in the image below, there was defined the Sample_values as the values, and the Otu_ids, as the labels.

To create the bar chart, there were created the yticks, slice from 0 to 10, and used the reverse function to have it in descending order.
The results of the dashboard created are:

    var yticks = otu_ids.slice(0,10).map(id => "OTU" + id).reverse();
       console.log(yticks)

As well, to create the trace of the bar chart, there were used the slice() and reverse() functions.

      var barData = [{
        x:sample_values.slice(0,10).reverse(),
        y:yticks.slice(0,10).reverse(),
        type: "bar",
        text:otu_labels,
        orientation: 'h'
          }];

The orientation is horizontal, and we define the x, y, type, and text and we create the layouts ad the function to plot the bar chart.
Also, for the gauge chart, there was created a variable named gaugeData, gaugeLayout and finally, there use Plotly to plot the gaugeData and gaugeLayout.

      Plotly.newPlot("gauge", gaugeData,gaugeLayout);
    })

For these two charts there were resulted this:


<img width="913" alt="imagen1" src="https://user-images.githubusercontent.com/96165500/185718485-c173a9b1-2a8f-445f-878c-e12b64b0d11e.png">

to continue with the dashboard, there created a bubble chart below the gauge and bar chart. For the bubble chart, there was created a variable named bubbleData, and bubbleLayout and there were used Plotly to plot bubbleData and bubbleLayout. In this chart, there were defined the otu_ids, the sample_values, and the otu_labelsto the x, y, and text properties, respectively.

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

After this working visualization, it will be easy for the company identifies if there is a candidate to fabricate synthetic beef, and Roza's volunteers will be able to identify whether that species is found in their navel. This visual information facilitates the users to find the information needed, they just must select the volunteer id, and all the information in the table and charts will be deployed.  There is only the information they needed to visualize to find the volunteer's properties and their navels. In three charts they found the answers and if some volunteers have the bacteria species needed, they can find the volunteer easily. To perform a better but simple dashboard is a must to add a title and a little information about the project.

## Link

To visualiza the complete dashboard, visit: https://alecano1.github.io/BellyButton/
 

