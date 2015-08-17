# Opportunity Tracker Angular Application in Sharepoint

This is an Angular application that displays opportunity/demand data using using the Sharepoint REST API to pull data from Sharepoint.

The Application is built on two Sharepoint lists:

OpportunityTracker
OpportunityTrackerTasks


The Application builds a model that:

1. Links each Task to its opportunity.
2. Builds a summary model for the opportunities (to facilitate the graph views).
3. Builds a filter into the opportunities


The View has 3 parts:

1. Graph of the summary opportunity data. These views also allow you to set filters.
2. A filter block that is only shown if there is at least 1 active filter. This view allows you to remove the filter.
3. A Bootstrap accordian that displays the opportunity and task data. 

The links to add and edit opportunity and tasks are just links to the out-of-box Sharepoint form pages.

 





