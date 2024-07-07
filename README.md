
# User Journey Analysis in Python

In this User Journey Analysis in Python project,  I'll be exploring real-world data from online subscription-based learning platform and analyze user behavior. Generally, ‘user journey’ refers to each user’s experience while exploring your product or platform. In other words, it’s the sequence of pages each user visited before purchasing a subscription.

Analyzing this type of data is an essential task for businesses because it can let them identify key pages (or sequences of pages) that help users convert into paying customers. It can also give insight into how users behave so they can structure their marketing campaigns or identify unnecessary pages.


The project focuses more on building all the right tools and functions in Python to generate helpful metrics. 
## Documentation
Overview

This documentation provides an overview of the preprocessing and analysis steps used in the User Journey Analysis project. The project involves transforming raw user journey data into a clean, analyzable format and then performing various analyses to understand user behavior.


A. Preprocessing the Data

File:
(https://github.com/akshayamaujey/User_Journey_Analysis/blob/main/User_journey_preprocessing.ipynb)

The preprocessing notebook is used to clean and prepare raw data (user_journey_raw.csv) for analysis. The output is a clean dataset (clean_data.csv).

1. remove_page_duplicates

Purpose: Removes consecutive duplicate pages in user journeys.

Functionality: Splits each journey into a list of pages, removes consecutive duplicates, and joins them back into a string. Applied to clean_data.

2. group_data

Purpose: Aggregates user journeys based on the specified session parameter.

Parameters:
session: Determines which part of the user journey to consider.
'all': Takes the entire user journey.
'all_except_last': Excludes the last entry.
'last': Takes the last specified number of entries.
'first': Takes the first specified number of entries.
group_column: Column to group by, default is user_id.

Functionality: Aggregates user journeys into a single string and stores the results in empty_df.

3. remove_pages

Purpose: Removes specified pages (actions) from user journeys.

Parameters:
pages: List of pages to be removed.

Functionality: Splits each journey string into a list of pages, filters out unwanted pages, and joins them back into a string. Applied to clean_data with an empty list of pages (no pages removed in this case).

Analysis

File:(https://github.com/akshayamaujey/User_Journey_Analysis/blob/main/User_journey_analysis.ipynb)

The analysis notebook is used to understand user behavior based on their subscription types by analyzing their journey through various pages in the cleaned dataset (clean_data.csv).

Functions Used:

1. filter_vai_subscription

Purpose: Filters the dataset based on subscription type.

Parameters:
data: Dataset to be filtered.
filter: Subscription type to filter by (e.g., 'Annual', 'Monthly'). Defaults to "all".
target_column: Column indicating the subscription type. Defaults to subscription_type.

Functionality: Returns the filtered dataset based on the specified subscription type.

2. split_user_journey

Purpose: Splits user journey strings into lists of individual pages.

Parameters:
data: Dataset containing user journeys.
target_column: Column holding the user journey as a string. Defaults to user_journey.

Functionality: Splits the strings in the target_column on the "-" character, converting them into lists of pages.

3. page_count

Purpose: Counts the occurrences of each page in user journeys.

Parameters:
data: Dataset containing user journeys.
target_column: Column containing the user journeys as lists of pages. Defaults to user_journey.
subscription_type: Type of subscription to filter by before counting pages. Defaults to 'all'.
sort: Boolean indicating whether to sort the counts in ascending order. Defaults to False.

Functionality: Filters the data based on subscription type, flattens all user journeys into a single list of pages, counts the occurrences of each page, and returns a sorted DataFrame.

4. page_presence

Purpose: Counts the presence of each page across all user journeys.
Parameters:
data: Dataset containing user journeys.
target_column: Column containing the user journeys as lists of pages. Defaults to user_journey.
subscription_type: Type of subscription to filter by before counting page presence. Defaults to 'all'.
sort: Boolean indicating whether to sort the presence counts in ascending order. Defaults to False.
Functionality: Filters the data based on subscription type, converts each user journey to a set (to avoid counting duplicate pages within a single journey), counts the presence of each page, and returns a sorted DataFrame.

5. page_destination

Purpose: Analyzes transitions between pages in user journeys.

Parameters:
data: Dataset containing user journeys.
target_column: Column containing the user journeys as lists of pages. Defaults to user_journey.
subscription_type: Type of subscription to filter by before analyzing transitions. Defaults to 'all'.
sort: Boolean indicating whether to sort the transitions in ascending order. Defaults to False.

Functionality: Filters the data based on subscription type, records transitions from one page to the next, counts occurrences of each transition, and returns a dictionary of transitions.

6. page_sequence

Purpose: Analyzes sequences of pages of a specified length within user journeys.

Parameters:
data: Dataset containing user journeys.
target_column: Column containing the user journeys as lists of pages. Defaults to user_journey.
sequence: Length of the page sequence to analyze. Defaults to 3.
subscription_type: Type of subscription to filter by before analyzing sequences. Defaults to 'all'.
sort: Boolean indicating whether to sort the sequence counts in ascending order. Defaults to False.

Functionality: Filters the data based on subscription type, extracts all possible sequences of the specified length, counts occurrences of each sequence, and returns a sorted dictionary of these sequences.

***Purpose of These Functions

The functions are designed to provide a comprehensive analysis of user behavior on a website or platform. By filtering and analyzing user journeys based on subscription types, the following insights can be gained:

1. Page Count: Identifies the most frequently visited pages.
2. Page Presence: Determines how often each page appears in user journeys.
3. Page Destination: Analyzes the most common transitions between pages.
4. Page Sequence: Identifies frequent sequences of pages users navigate through.

## Authors

- @akshayamaujey(https://github.com/akshayamaujey)


