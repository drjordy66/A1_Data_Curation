### Cleaned data

The cleaned data was created using the [raw data](../data_raw) on 10/19/2017.

The cleaned data file is in a `.csv` format and contains eight columns in with the following format:

column name | value
--- | ---
year | YYYY
month | MM
pagecount_all_views | int
pagecount_desktop_views | int
pagecount_mobile_views | int
pageview_all_vies | int
pageview_desktop_views | int
pageview_mobile_views | int

The integers for each column other than 'year' and 'month' represent the number of views for the respective column. For dates where no data was given for a particular API pull, a value of 0 will be used.