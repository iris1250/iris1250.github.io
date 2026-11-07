---
layout: project
name: UFO Sightings Data Analysis
tools: [Python, Pandas, Altair, vega-lite]
image: assets/pngs/ufo_preview.png
description: Interactive Altair visualizations analyzing modern UFO sighting trends and shapes (1990~).
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---

### Write-Up
I think my local Pandas version has removed .iteritems(), so I added the compatibility patch for Altair to work properly. For the first visualization, I created a horizontal bar chart displaying the top 8 most commonly reported UFO shapes from 1990 to the present day using the standardized UFO dataset. To prepare this data in Python, I loaded the CSV file without a header, assigned descriptive column names (because the original UFO dataset has no column names), converted the raw date strings into proper datetime objects, and filtered the rows to include years from 1990 and after. I then grouped and counted the occurrences of each shape to isolate the top 8 categories. Regarding design choices, I used nominal encoding for the UFO shapes on the y-axis and quantitative encoding for the sighting counts on the x-axis, sorting the bars in descending order by frequency to make comparisons intuitive. For coloring, I mapped the nominal shape variable to the categorical Tableau 10 color scheme, which distinctly separates each shape category without introducing any misleading ordinal hierarchy.

The second visualization is an interactive scatter plot illustrating the trend of UFO sightings over time, broken down by shape and aggregated yearly. In the Python analysis notebook, I performed data transformations by grouping the filtered dataset by both the year and the reported shape, computing the total annual sightings count for each category using pandas aggregation functions. For design encodings, I assigned the year to an ordinal x-axis and the sighting count to a quantitative y-axis, while employing the category20 color scheme to map the distinct UFO shapes. To enhance exploration, I integrated an interval selection brush across the timeline axis, which dynamically adjusts the opacity of data points (the unselected points will be greyish) so that unselected years dim to a low transparency while selected time windows remain fully highlighted. This interactivity makes the visualization significantly clearer and more attractive to isolate specific historical periods and trace how individual shape reporting trends evolve over decades.

### Visualizations

#### Top UFO Shapes
<vegachart schema-url="{{ '/assets/json/ufo_top_shapes.json' | relative_url }}" style="width: 100%"></vegachart>

### Sighting Trends Over Time
<vegachart schema-url="{{ '/assets/json/ufo_yearly_trend.json' | relative_url }}" style="width: 100%"></vegachart>

### Links & Resources

<div class="left">
{% include elements/button.html link="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/ufo-scrubbed-geocoded-time-standardized-00.csv" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://github.com/iris1250/iris1250.github.io/blob/main/IS445_Week10_1.ipynb" text="The Analysis" %}
</div>