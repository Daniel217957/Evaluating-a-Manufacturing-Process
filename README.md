# Identifying Outliers: Evaluating a Manufacturing Process
![cranks and cogwheels](Manufacturing%20Folder/manufacturing.jpg)
## Skills
SQL:Subquerying, Nested Queries, Window functions, Joins, Statistics, Sorting and Filtering(CASE WHEN, WHERE and ORDER BY clauses)
## Project Context
The manufacturing process is important for piecing together a finished product. Each part of the process must be monitored to produce items that meet certain key standards or criteria. This will ensure a smooth-running manufacturing process, consistently making high-quality products.
## What I Analyzed
The dataset titled [Parts](Manufacturing%20Folder/parts.csv) contained data about the items being manufactured, including item number, length, width and height, and the operating machine used for each. The goal was to determine whether the manufacturing process was progressing within acceptable limits. Hence, 2 limits were set for each product: an upper control limit (UCL) and a lower control limit (LCL).

The UCL defines the highest acceptable height for the parts, while the LCL defines the lowest acceptable height. Ideally, parts should fall between the two limits. So I  identified the points in the process that fell outside of the range and required adjustments.
