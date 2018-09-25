## Colombian migration : where do people go more ? And who are they ?

### Author
Pierre Raimbaud : https://github.com/pierreraimbaud
Projet page : https://pierreraimbaud.github.io/ColombiansAbroadViz/

### Prerequisites, technologies
This visualization uses open data from data.gov.com. The aim is to show some interesting insights about this data : this is the principal objective. The other ones are more academic, like use d3 and publish the web page on githubPages. The technologies used are d3 (javascript), HTML, CSS and git (nodejs for developing with a local server). There is no specific prerequisites for enjoying the visualization neither for using the code available in github.

### What, why and how ? Understanding this visualization thanks to abstraction

To be more precise about these insights, in the following paragraphs we will explain what were our data (through data abstraction), why this visualization (through task abstraction) and the reason of how we choice to present the data (idioms : visual encoding and interaction) ; thanks to that, we have been able to answer to the title question : Colombian migration : where do people go more ? And who are they ?

### What ?

The dataset type is a table. The dataset availability is static because the dataset available on the website  is not modified in real-time, so we just download the file from the website and create a new file of processed data (correcting absent values and modifying the columns spaces – English names and without spaces), then we load it. Then for separating the dataset in smaller ones, and also to get derive data, we process this file in the visualization with d3.

Before processing the data in d3, the items represent one or one group of people, which have the same characteristics (living country, country iso code, age, age group, level of education, gender, quantity of people). These characteristics are the attributes (named just above).

The attributes Country, ISOCode, AgeGroup, AcademicLevel and Gender are categorical (list of different country and iso code, categories of ages – baby, child, adolescent, young adult, adult, elderly adult), list of academic level (PhD, Master etc.), male, female or not given information categories.

The attributes Age and Quantity are ordered and quantitative (because they are numbers) and sequential (the age is also positive and there is no separation in groups so no diverging– the attribute AgeGroup has been created for this!), the quantity is also positive without diverging).

After processing the data, we obtain new attributes. Each time we consider the people living in one country. 
The average age, from the attribute age, which is also ordered, quantitative and sequential for the same reasons than the attribute age.
The male rate, the female rate, the “no gender” rate, all from the attribute Gender, the PhD rate and Primary rate, from the attribute AcademicLevel, the children rate, the adult rate and the elderly adult rate, from AgeGroup attribute, which are ordered, quantitative and sequential because of being rates of an amount of people.

### Why ?

Which tasks do we want to perform here ? 

As said in the title, first, the primary task we want to do is to show where the Colombian mostly have been migrating up-to-day.
In terms of Tamara, at a high-level, the action is Discover and the target is Features. To be more precise, at a mid-level the action is Browse and the target is Extremes (only the major ones for this case). We could also say at a low-level that the action is Identify and the target is Outliers (we can’t say summarize because we deliberately do not show all the data, eliminating the countries were less than 1000 have been going. The insight is that people mostly have been to Venezuela, United States of America and Spain.

The global secondary task here, also as described in the title, is to know better about these Colombian people. In terms of Tamara, this global task could be divided in smaller task, for each visualization (depending on the dataset). For these secondary tasks we could eventually consider sometimes an action of summarize, considering that the characteristics of people in countries where less than 1000 Colombian people have been are not significant (comparing to the amount of people in the others countries in the world).

In dataset 2 (Average age), one task is Summarize Distribution and another one is Browse Extremes (this time, both of them) ; for example, we see that people are younger (left extreme) in the countries near Colombia (Argentina, Brasil, Panama) + Spain ; but we can’t make a conclusion about that (saying people are younger for Latin and Central America) because for example the other extreme is Dominican Republic which is near Colombia also.

In dataset 3 and 4 (Male and femal age), one task is Browse Extremes – one insight is the confirmation of the common thought that few women go to United Arab Emirates and another one is a surprise : less men than women go to Italia (we could expect the contrary which the “cliches”).

In dataset 7 (Primary rate), combining it with dataset 8 (Child rate), one insight, by doing the task Browse Extremes in dataset 7 and then Locate “the outlier” (outlier in dataset 7, not in 8) Venezuela in dataset 8,  - the two tasks together can be considered as a Compare Feature, is the fact that we can be surprised that despite being in first position for primary level education rate, Venezuela is not in the first rate, far for this, in dataset 8 about children rate. So maybe one explication is that more than in other countries, the Colombian people which have been to Venezuela do not make other studies than primary school. We could compare feature also with dataset 10, where,  Browsing the Extremes, we see that the major elderly rate is also in Venezuela so maybe there is a correlation between these data – maybe in one period of the Colombia history not so recent many people go to Venezuela and at this time the education was not so developed or that no founds for that for the migrants.

### How ?

We choose bar charts for this visualization.
First, we have to say that for all the dataset, in the x axis, we have the country iso code attribute, which is categorical and in the y axis we have an amount or a rate, so ordered attributes.
As a result, about the visual encoding, the mark we choose is line and the channel is vertical position (which give a bar chart) ; it can be easily explain because this channel is the most effective for the ordered attributes (which should always use magnitude channels, in theory, so from this point of view, we use a good and expressive type).
We choose to order and align the marks in our representation because it combines well with ordered attributes.
Then about the interaction, we decide to not provide to the user reduction, because we already have done that, by processing the data, in order to make directly the correct focus for our task. The provided interaction is a button for switching between the dataset, so it’s a Change manipulation. We provide also a “Select” manipulation, with a mouseover which give more detailed information about the current item.