# Python Azure Billing Usage and Rate Card

This is a jupyter notebook for exploring Azure Usage. It leverages the [Azure Billing REST 
API](https://msdn.microsoft.com/en-us/library/azure/mt218998.aspx). 

These API's have several issues:

* The Usage API hasn't been updated since 2015, the Rate Card API was updated in 2016 based on the API version names of `2015-06-01-preview` and `2016-08-31-preview` respectively
* Both APIs are in 'Preview' 
* Neither API supports paging, and the Usage API has a 1000 item limit which is easily exceeded by aggregating usage hourly on a small subscription.
* These API's do not work for Enterprise Agreement subscriptions, they are only useful for pay-as-you-go

There is an alternative azure python package, [azure-mgmt-billing](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt-billing) in the [azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python), this is a sparsely documented python package, with no known working examples. Since the API version name is `2018-03-01-preview`, it appears to be under active development as opposed to the API this repository uses. 
 
![alt text](dataflow.svg)

## Notebooks

* [Explore Rate Card and Usage.ipynb](Explore Rate Card and Usage.ipynb) - A general exploration of the Azure billing and usage API 
* [Load Azure Daily Usage for Month to Match Invoice.ipynb](Load Azure Daily Usage for Month to Match Invoice.ipynb) - Loads daily usage by resouce from the Azure Micorsoft.Commerct/UsageAgrregates API endpoint. 
* [Load Azure Usage CSV.ipynb](Load Azure Usage CSV.ipynb) - Loads daily usage from a CSV downloaded from the Azure portal. 
* [Reconcile API Usage with CSV Usage.ipynb](Reconcile%20API%20Usage%20with%20CSV%20Usage.ipynb) - Compares the differences between the two data access methods.