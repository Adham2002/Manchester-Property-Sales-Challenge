# My solution to The Manchester Property Sales Challenge
This repository provides my data-wrangling pipeline for 
It includes quality controls checks that generalise to data provided in the format of [Prices Paid Data](https://github.com/MaxwellB13/manchester_property_sales/blob/master/data/pp_data_man.parquet) and [Postcodes](https://github.com/MaxwellB13/manchester_property_sales/blob/master/data/pc_man.parquet) parquet files


## Data wrangling
### My approach
My initial thought was to develop the pipeline using TDD however from experience I know this is time consuming and the time constraints made this impractical. Ideally this is how I have developed the pipeline and quality checks

1. Having experience with Pandas and never having used Polars I first read the [Getting started](https://docs.pola.rs/user-guide/getting-started) and [Coming from Pandas](https://docs.pola.rs/user-guide/migration/pandas/#column-assignment-based-on-predicate) pages from the Polars documentation
2. Understand the data
3. Clean the data so the current dataset is clean
4. Add cleaning functionalities that can generalize to any data of this format
5. Filter and transform the data for the task at hand
   1. Filter by county and time range specified in the challenge
   2. Convert to correct data types
   3. Create new columns (postal sector column)
6. Add quality control checks to ensure data is clean, formatted well and has the best datatypes
7. Export cleaned data to PowerBI for analysis and visualizations

### Utilizing Polars
Lazy loading
Grouping operations into expressions for query optimization using parallelization

### Cleaning data
- Big outliers in price
- Invalid postcodes formats (empty strings, new lines)
- Freehold and leasehold col has a U option
- Repeated rows