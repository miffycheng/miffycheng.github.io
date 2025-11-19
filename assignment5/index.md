---
layout: default
title: HW3 – Building Inventory Visualizations
---

# Homework 5 – Submit Jekyll webpage link

## The Data
[Building Inventory CSV](https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/building_inventory.csv)

## The Analysis
You can view the full notebook here:  
[hw3_building_inventory.ipynb](https://github.com/miffycheng/miffycheng.github.io/blob/main/python_notebooks/building_inventory.ipynb)

---

## Plot 1 – Building Usage Over Time

<p>
<iframe src="plot1.html" width="800" height="500"></iframe>
</p>

In this visualization, I display how the number of buildings in Illinois has changed across decades and how this distribution varies by building usage. Each area in the stacked chart represents a “Usage Description,” such as academic, residential, or storage facilities, allowing viewers to see both overall construction trends and shifts in usage composition over time. To create the decade variable used on the x-axis, I transformed the Year Constructed field by converting it to numeric form, removing invalid values, and grouping each year into its corresponding decade using integer division.

From a design perspective, I use the decade as an ordinal encoding on the x-axis because decades represent a natural time interval for understanding long-term construction trends. The y-axis uses a quantitative encoding of the number of buildings in each decade–usage group, which I computed using a groupby aggregation. For color encoding, I apply a nominal color scheme to represent the different usage categories. A categorical palette is appropriate here because it visually separates the usage types, helping viewers compare the relative presence of each category. I also include tooltips showing the decade, usage type, and count to support detailed data inspection.

For interactivity, I implemented two mechanisms to help users explore patterns more clearly. First, hovering over an area highlights its usage category by increasing opacity, while dimming all others. This makes it easier to focus on a single usage category in the context of the stacked layout. Second, clicking a category in the legend triggers a single-selection filter that isolates only that usage, removing all others from the chart. This dual interaction allows intuitive exploration: hover provides quick comparisons, while clicking supports deeper analysis without visual clutter.

---

## Plot 2 – Average Building Size by Usage

<p>
<iframe src="plot2.html" width="800" height="500"></iframe>
</p>

This visualization highlights which building usage categories in Illinois have the largest average square footage. To create this chart, I first cleaned the Square Footage field by converting it to a numeric type and removing any invalid or missing values. I then grouped the dataset by Usage Description and computed the mean square footage for each category. Since some categories have very small counts or extremely long labels, I sorted these averages in descending order and selected the top fifteen categories to keep the visualization readable and focused on the largest building types.

From a design perspective, I used a horizontal bar chart with average square footage encoded on the quantitative x-axis and the building usage categories encoded as nominal values on the y-axis. Horizontal bars were chosen because many category names are long, and this layout avoids label overlap while making comparisons straightforward. I chose a single-color bar design (a neutral blue) to place emphasis on bar length rather than color differences, reinforcing the chart’s purpose as a simple ranking visualization. Unlike the first figure, which uses interactive selection and hover highlighting to explore trends over time, this plot is intentionally non-interactive. Its purpose is to present a clean, static summary of which building types occupy the most physical space on average.
