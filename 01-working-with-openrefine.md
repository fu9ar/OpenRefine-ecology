---
layout: lesson
root: .
title: Working with Open Refine
minutes: 
---

# Learning Objectives

* Introduce concept of facets
* Show split columns by defined separator
* Show power of include / exclude, sort by name / count
* Show the power of clustering algorithms to reveal data patterns, data snafus
* Show the power of undo / redo.

----------------------------------------------------

# Lesson

## Creating a Project

Start the program. (Double-click on the google-refine.exe file. Java services will start on your machine, and Refine will open in your Firefox browser).

Note the file types Open Refine handles: TSV, CSF, *SV, Excel (.xls .xlsx), JSON, XML, RDF as XML, Google Data documents. Support for other formats can be added with Google Refine extensions.

In this first step, we'll browse our computer to the sample data file for this lesson. In this case, we are using the Demographics csv file. 

If you haven't already, download the data from:  


**Once Refine is open, you'll be asked if you want to Create, Open, or Import a Project.**

````
  - Click Browse, find OPENREFINE-Demographics.csv
  - Click next to open OPENREFINE-Demographics.csv
  - Refine gives you a preview - a chance to show you it understood the file. If, for example, your file was really tab-delimited, the preview might look strange, you would choose the correct separator in the box shown and click "update preview."
  - If all looks well, click _Create Project._
```

## Faceting

*Exploring data by applying multiple filters*

OpenRefine supports faceted browsing as a mechanism for

* seeing a big picture of your data, and
* filtering down to just the subset of rows that you want to change in bulk.

Typically, you create a facet on a particular column. The facet summarizes the cells in that column to give you a big picture on that column, and allows you to filter to some subset of rows for which their cells in that column satisfy some constraint. That's a bit abstract, so let's jump into some examples.

[More on faceting](https://github.com/OpenRefine/OpenRefine/wiki/Faceting)

````
  - Scroll over to the CHSI_State_Name column
  - Click the down arrow and choose > Facet > Text facet
  - In the left margin, you'll see a box containing every unique, distinct value in the CHSI_State_Name column and Refine shows you how many times that value occurs in the column (a count), and allows you to sort (order) your facets by name or count.
  - Edit. Note that at any time, in any cell of the Facet box, or data cell in the Refine window, you have access to "edit" and can fix an error immediately. Refine will even ask you if you'd like to make that same correction to every value it finds like that one (or not).
````

## Cluster

One of the most magical bits of Refine, the moment you realize what you've been missing. Refine has several clustering algorithms built in. Experiment with them, and learn more about these algorithms and how they work. 

[More on clustering](https://github.com/OpenRefine/OpenRefine/wiki/Clustering-In-Depth)

In OpenRefine, clustering refers to the operation of "finding groups of different values that might be alternative representations of the same thing". For example, the two strings "New York" and "new york" are very likely to refer to the same concept and just have capitalization differences. Likewise, "Gödel" and "Godel" probably refer to the same person.

````
  - In this example, in the CHSI_State_Name Text Facet we created in the step above, click the _Cluster_ button.
  - In the resulting pop-up window, you can change the algorithm method, and keying function. Try different combinations to see the difference.
  - For example, with this dataset, the _nearest neighbor_ method with the _PPM_ keying function shows the power of clustering the best. 
  - Intentional errors in these state names have been introduced, by me, to show how errors (typos) in any position can be found with this method. All errors can then be fixed by simply entering the correct value in the box on the right. Often, the algorithm has guessed correctly. 
  - After corrections are made in this window, you can either Merge and Close the Cluster pop-up, or Merge and Re-cluster.
````

## Split / Leading - Trailing Whitespace / Undo - Redo

If data in a column needs to be split into multiple columns, and the strings in the cells are separated by a common separator (say a comma, or a space), you can use that separator to divide up the bits into their own columns.

````
  - Go to the drop-down tab at the top of the column that we need to split into multiple columns
  - For example, go to the Strata_Determining_Factors column > from drop-down choose Edit Column > Split into several columns
  - In the pop-up, for the separator, leave the comma
  - Remove the check in the box that says "remove column after splitting"
  - You'll get a few extra columns called, in this case: Strata_Determining_Factors 1, Strata_Determining_Factors 2
  - Click on the Edit this cell button for population size, even though Open Refine hides leading whitespace, this will show you that it is there. If you examined the CSV, you would see that it is scattered throughout this section.
  - This is a problem because, sometimes, when you try to sort data with leading whitespace, the whitespace is sorted.
  - These can be easily removed with another Refine feature in the column drop-down choices. See drop-down: Edit cells > Common transforms > Remove leading and trailing whitespace
  - To Undo create columns, look to the tabs under the Open Refine Logo in the left pane of the of the interface. Click where it says Undo / Redo. Click back one step (all steps, all changes are saved here). Go back to the previous step and click. The extra columns will be gone.
````

Previous: [Getting Started with OpenRefine](00-getting-started.html)  Next: [Scripts from OpenRefine](02-scripts.html)
