---
title: Initial data exploration in SAP BusinessObjects Lumira
description: Overview of the data exploration basics using the Prepare room
primary_tag: products>sap-lumira
tags: [  tutorial>beginner, products>sap-lumira ]
---
## Prerequisites  
- **Proficiency:** Beginner
- **Tutorials:** [Initial data acquisition in SAP BusinessObjects Lumira](https://www.sap.com/developer/tutorials/lumira-initial-data-acquisition.html)

## Next Steps
- [Basics of data visualization](https://www.sap.com/developer/tutorials/lumira-initial-data-visualization.html)

## Details
### You will learn  
How to understand the dataset that has been added to SAP BusinessObjects Lumira.

### Time to Complete
**10 Min**.

---


[ACCORDION-BEGIN [Step 1: ](Check row and column count)] ￼

Make sure you opened the Prepare room of SAP BusinessObjects Lumira to explore the data acquired in the previous tutorial.

In Status bar check how many rows and columns are in the dataset. In this example the dataset has 16317 rows with 13 columns and all are displayed.

![Dataset view in Grid view of the Prepare room](Lum02-01.png)

All of columns became **Dimensions** to analyze data. Dimensions with numeric data have been additionally recognized by SAP BusinessObjects Lumira as **Measures**, which can be used for numerical analysis using different types of aggregation. Aggregation of the type `Sum` is the default for all measures.

> You can check UI components terminology of SAP BusinessObjects Lumira by downloading the ***Terminology Quick Reference*** from User Guides available at [SAP BusinessObjects Lumira help portal](https://help.sap.com/lumira#section2).


[ACCORDION-END]

[ACCORDION-BEGIN [Step 2: ](View facets)] ￼

To better understand values of dimensions in your dataset switch display of the Data pane to **Facets**.

![The Facets view of Data pane in Prepare room](Lum02-02.png)

Now each facet displays a list of unique values of corresponding dimension. And you can see the number of unique values in the given dimension right next the to facet's name. In this case there are 32 distinct values of `Country` in example above.

If a dimension has more than 100 values, like in case of the **Date** dimension, then `100+` is displayed by default. Click on it to force the facet view to calculate the exact number of distinct values of corresponding dimension.


[ACCORDION-END]

[ACCORDION-BEGIN [Step 3: ](View facet values)] ￼

Right click on the Facet's value highlights all related values from other dimensions, i.e. all values which appear in same rows with the selected one. Right click on `Australia`, and you see `Melbourne` and `Sydney` highlighted in the **City** facet.

![Values relationships highlighted in the Facets view](Lum02-03.png)


[ACCORDION-END]

[ACCORDION-BEGIN [Step 4: ](Change facet measure)] ￼

Facet's values are ordered alphabetically by default and display the number of occurrences next to each value.

Click on **Options** button next to the `Lines` Facet's name, and change the measure from **Occurrences** to **Sales Revenue**.

![Aggregation changed from Occurences to Sales Revenue](Lum02-04.png)


[ACCORDION-END]

[ACCORDION-BEGIN [Step 5: ](Change sort order)] ￼

To find top selling lines of products change the sort order by clicking on **Options** button next to **Lines** facet's name and selecting **Sort** -> **Sort Measure Descending**.

You can see that top selling line of products is `Sweat-T-Shirts`.

![Sorting values by Sales Revenue](Lum02-05.png)


[ACCORDION-END]

[ACCORDION-BEGIN [Step 6: ](Add a filter)] ￼

And to find what lines of products are best selling in `Australia`, add the filter by clicking on **Options** button and then selecting **Filter...** to open a dialog box. Select `Australia` and then click **Apply**.

![Filter dialog window](Lum02-06.png)

You should notice that Austria has been added as a filter in **Filters bar**. Remove it from there by clicking `x` after you analyzed filtered data.

![Remove filter from the Filters bar](Lum02-07.png)


[ACCORDION-END]



### Optional
- You can learn more about data exploration from the product's official [user guide](https://help.sap.com/lumira#section2) for SAP BusinessObjects Lumira

## Next Steps
- [Basics of data visualization](https://www.sap.com/developer/tutorials/lumira-initial-data-visualization.html)
