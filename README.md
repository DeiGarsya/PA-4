# Programming Assignment 4
NAME : Deirojel Martin M. Garcia

SECTION : 2ECE-A

SUBMITTED / Last updated: September 18, 2024

***
## Intended Learning Outcomes

  - To identify the codes and functions needed in cleaning and visualizing data
  - To be able to apply and use the different codes and functions in creating a Python program that will
be used in data wrangling and data visualization

***
## Problem 1: ECE BOARD EXAM PROBLEM

Using data wrangling and data visualization technique with
storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given.

First, we have to import pandas for data analysis.
``` python
import pandas as np
```
Next, we have to import the given excel file which contains the data to be analyzed.
``` python
main = pd.read_excel('board2.xlsx')
main
```

1. Create the following data frames based on the format provided:

   a. Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as
Instrumentation and hometown Luzon

In  this problem, we have to create a table that contain the parameters “Name”, “GEAS”, and the Electronics that contain a grade greater than 70. The contents of the table must be part of the track "Instrumentation" and must live in the hometown of Luzon. This can be implemented with this code:
``` python
Instru= main.loc[(main['Hometown']=='Luzon')&(main['Electronics']>70)&(main['Track']=='Instrumentation'),['Name','GEAS','Electronics']]
Instru
```
b. Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is
constant as Mindanao and gender Female

In  this problem, we have to create a table that contain the parameters “Name”, “Track”, "Electronics", And Average of the grade that contain a grade greater than or equal to 55. The contents of the table must live in the hometown of Luzon and must be Female. 

First, we need to create a new column which contains the average grade of each student. This can be done with this code:
``` python
main['Average']=(main.Electronics + main.GEAS + main.Math + main.Communication)/4
```
Next, we can now plot the table
``` python
Mindy = main.loc[(main['Hometown']=='Mindanao')&(main['Gender']=='Female')&(main['Average']>=55),['Name','Track','Electronics','Average']] 
Mindy
```

2. Create a visualization that shows how the different features contributes to average grade. Does
chosen track in college, gender, or hometown contributes to a higher average score?

Before we even code for plotting the visualizations, We first need to import the library that allows us to make these graphs
``` python
import matplotlib.pyplot as plt
```

Now we can plot for the different features.

Lets start with the table for Track. It can be implemented with this code:
``` python
plt.figure(figsize=(7, 5))
plt.bar(main['Track'], main['Average'])
```
Gender:
``` python
plt.figure(figsize=(5, 5))
plt.bar(main['Gender'], main['Average'])
```
Hometown:
``` python
plt.figure(figsize=(7, 5))
plt.bar(main['Hometown'], main['Average'])
```
