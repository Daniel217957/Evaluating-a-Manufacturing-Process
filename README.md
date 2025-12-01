# Identifying Outliers: Evaluating a Manufacturing Process
![cranks and cogwheels](Manufacturing%20Folder/manufacturing.jpg)
## Skills
SQL:Subquerying, Nested Queries, Window functions, Joins, Statistics, Sorting and Filtering(CASE WHEN, WHERE and ORDER BY clauses)
## Project Context
The manufacturing process is important for piecing together a finished product. Each part of the process must be monitored to produce items that meet certain key standards or criteria. This will ensure a smooth-running manufacturing process, consistently making high-quality products.
## What I Analyzed
The dataset titled [manufacturing_parts](Manufacturing%20Folder/manufacturing_parts.csv) contained data (500 rows) about the items being manufactured, including item number, length, width and height, and the operating machine used for each. The goal was to determine whether the manufacturing process was progressing within acceptable limits. Hence, 2 limits were set for each product: an upper control limit (UCL) and a lower control limit (LCL).

<img width="427" height="109" alt="image" src="https://github.com/user-attachments/assets/fb4390f0-cfc5-4289-9f55-1e9c108739a2" />

The UCL defines the highest acceptable height for the parts, while the LCL defines the lowest acceptable height. Ideally, parts should fall between the two limits. So I  identified the points in the process that fell outside of the range and required adjustments.
## The Query:
<img width="1113" height="363" alt="image" src="https://github.com/user-attachments/assets/494048dd-6979-4ee4-a5f9-ef4605b61673" />
<img width="1109" height="342" alt="image" src="https://github.com/user-attachments/assets/66a03027-5f64-41d6-9263-71031f182952" />

The window was set to 5 because the query is implementing a moving window of 5 consecutive observations for Statistical Process Control (SPC). That is, a moving average and moving standard deviation over the last 5 items for each operator. The window_count makes sure that each row only uses a full rolling window of 5 observations, not a partial one.

A CROSS JOIN was used to attach the computed control limits (UCL and LCL) to every row without losing or reshaping any of the main query's data.
## Result
The result displayed: operator, row_number, height, avg_height, stddev_height, ucl, lcl, alert and ordered by the item_no (as highlighted in the query). 

The alert column read "True" for products that fell outside the acceptable range (below the LCL or above the UCL) and "False" for items within range. View the results [here](Manufacturing%20Folder/results.csv).

I used SQL window functions to compute moving averages and standard deviations, and to establish dynamic control limits to monitor the consistency of manufactured parts.

By comparing part dimensions against these thresholds, I successfully identified and flagged outliers that deviated from acceptable quality standards.
