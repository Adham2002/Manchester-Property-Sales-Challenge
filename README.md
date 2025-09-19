# My solution to The Manchester Property Sales Challenge
This repository provides my data-wrangling pipeline for 
It includes quality controls checks that generalise to data provided in the format of [Prices Paid Data](https://github.com/MaxwellB13/manchester_property_sales/blob/master/data/pp_data_man.parquet) and [Postcodes](https://github.com/MaxwellB13/manchester_property_sales/blob/master/data/pc_man.parquet) parquet files.


## My approach
My initial thought was to develop the pipeline using TDD however from experience I know this is time consuming and the time constraints made this impractical. Ideally this is how would I have developed the pipeline and quality control checks.

1. Having experience with Pandas but never having used Polars I first read the [Getting started](https://docs.pola.rs/user-guide/getting-started) and [Coming from Pandas](https://docs.pola.rs/user-guide/migration/pandas/#column-assignment-based-on-predicate) pages from the Polars documentation.
2. Understand the data.
3. Create pipeline to clean problems in the current datasets.
4. Add cleaning functionalities to pipeline that can generalize to any data of this format.
5. Filter and transform the data for the task at hand.
   1. Filter by county and time range specified in the challenge.
   2. Convert to correct data types.
   3. Create new columns (postal sector column).
6. Add quality control checks to ensure data is clean, formatted well and has the correct data types.
7. Export cleaned data to PowerBI for analysis and visualizations.

## Utilizing Polars
- Lazy loading of parquet files.
- Grouping operations into expressions for query optimization using parallelization.
- Cleaning functions should return expressions so they can be grouped into 1 expression and optimized.

## Cleaning data
Problems found in the data:
- Big outliers in price (a couple properties sold for trillions and some sold for under 10.000).
- Invalid postcodes formats (empty strings, valid formats with leading or trailing white space).
- freehold_or_leasehold col has a U option (presumably demarcating 'Unknown').
- Duplicate rows.

## Files and folder
- logs: directory for log files. A log file is created every time the pipeline in run and has it's timestamp in it's name.
- manchester_property_sales: directory containing data cloned from [The Manchester Property Sales Challenge repo]("https://github.com/MaxwellB13/manchester_property_sales/tree/master").
- outputs: folder to store output of pipeline.
- Manchester Property Sales Dashboard.pbix: PowerBi dashboard for general trend analysis and visualization.
- Questions and analysis.ipynb: answers to questions in [The Manchester Property Sales Challenge README.md](https://github.com/MaxwellB13/manchester_property_sales/blob/master/README.md).
- wrangling_pipeline_prototype.ipynb: notebook containing pipeline and all cleaning and transformation methods required to run it.
