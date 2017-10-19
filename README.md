# A1_Data_Curation

### Goal

The goal of this assignment is to construct, analyze, and publish a dataset of monthly traffic on English Wikipedia from January 1 2008 through September 30 2017.

### License and link

Data was gathered from the Wikimedia REST API, Wikimedia Foundation, 2017. CC-BY-SA 3.0

https://wikimediafoundation.org/wiki/Terms_of_Use/en

### Relevant API documentation

1. The legacy __Pagecounts API__ ([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts), <a href="https://wikimedia.org/api/rest_v1/#!/Pagecounts_data_(legacy)/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end">endpoint</a>) provides access to desktop and mobile traffic data from January 2008 through July 2016.

	Data accessible via this endpoint is available under the CC0 1.0 license.

2. The __Pageviews API__ ([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews), [endpoint](https://wikimedia.org/api/rest_v1/#!/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end)) provides access to desktop, mobile web, and mobile app traffic data from July 2015 through September 2017.

	Data accessible via this endpoint is available under the CC0 1.0 license.

### Cleaned data

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

### Issues/special considerations

The pagecounts (legacy) data includes spiders/crawlers, whereas the pageviews data does not include spiders/crawlers.

While the data requested from the API pull spans 01/01/2008 to 10/01/2017 (MM/DD/YYYY), the pagecounts data only spans 01/01/2008 to 08/01/2016. During this final month, the number of views appear significantly lower such that they could be deemed an outlier as the API pull may not have pulled views for the entire month of 08/2016 (MM/YYYY). As such, this month was included in the cleaned data, but is removed when visualizing during the analysis.

### Additional attribution(s)

Relevant information pertaining to this assignment and API documentation was gathered from HCDS (Fall 2017) Assignments. CC-BY-SA 3.0