_The below steps directly reference the .ipynb in this directory_

Import necessary libraries that will be used

## Step 1: Data acquisition

Below is a function that takes two inputs, the API endpoint (either 'pagecounts' or 'pageviews') and the access parameter. For pagecounts the access parameter can be 'all-sites', 'desktop-site', or 'mobile-site'. For pageviews the access parameter can be 'desktop', 'mobile-app', or 'mobile-web'. The function fills in all other parameters for an API call (thanks Jonathan and Oliver!), and returns the API response.

Run the above function to call the API and assign the responses to variables

Export the API raw data files. This section has been commented out in order to not continuously overwrite the raw data files. The raw data files have already been created and will be imported in the next step.

## Step 2: Data processing

Import the raw .json files to process and create a new file for analysis.

### Functions for processing

`get_views` and `get_counts` take the raw .json files as inputs, strip the timestamps and views/counts, and return arrays with two columns (timestamp, views/counts) and a row with each month's worth of data.

`lookup_val` takes the arrays created from the prior functions as one input and a date as a second input. It uses the date to find the index within the array from column 1 (timestamp) and returns the value from that same index in column 2 (counts/views). If the date is not within the array, then a value of 0 is assigned.

Run the above functions to get all of the views/counts for both the legacy and current API

### Processing

First, all of the formatted arrays from the API responses are concatenated and the first column (timestamp) is taken as a `set()` to remove any duplicate timestamps. From here we can easily parse the timestamps into a list of just the years and a list of just the months. This gives us our first two columns of our cleaned data, 'year' and 'month'.

Second, we initialize five (one for each API response) lists where we will obtain just the counts/views from the two column arrays. We will then loop through all of the dates (no duplicates) that we found from the previous step and use the `lookup_val` function to find the corresponding counts/views for each API response and append these to lists we initialized.

Third, we need to aggregate the two mobile sets of data from pageviews to get the total mobile data. For both pagecounts and pageviews we aggregate the desktop counts/views and mobile counts/views to get the total views for each.

Convert to pandas DataFrame for easy export.

Export data in single csv. This section has been commented out in order to not continuously overwrite the cleaned data file. The cleaned data file has already been created and will be imported in the next step.

## Step 3: Analysis

Import the cleaned data file to use for analysis.

### Plot the data

The dates from the csv are converted to a datetime format in order to be plotted neatly. The points from the data are plotted, filtering out non-zero values in y-axis data.

The figure is then saved as a .png file.