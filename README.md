---
services: data-factory
platforms: python
author: spelluru
---

# Sample: copy data one folder to another folder in an Azure Blob Storage
In this sample you do the following steps by using Python SDK:

1. Create a data factory.
2. Create a linked service to link your Azure Storage account to the data factory.
3. Create a dataset that represents input/output data used by the copy activity.
4. Create a pipeline with a copy activity that copies data.

## Prerequisites

* **Azure subscription**. If you don't have a subscription, you can create a [free trial](http://azure.microsoft.com/pricing/free-trial/) account.
* **Azure Storage account**. You use the blob storage as **source** and **sink** data store. If you don't have an Azure storage account, see the [Create a storage account](https://docs.microsoft.com/en-us/azure/storage/common/storage-create-storage-account) article for steps to create one. 
* **Create an application in Azure Active Directory** following [this instruction](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal.md#create-an-azure-active-directory-application). Make note of the following values that you use in later steps: **application ID**, **authentication key**, and **tenant ID**. Assign application to "**Contributor**" role by following instructions in the same article.
* Create a **blob container** in Blob Storage, create an input **folder** in the container, and upload some files to the folder. The sample code use the **inputpy** and **outputpy** as input and output folder names. If you use different folders, update these values in the source code. 

## Install the Python package
1. Open a terminal or command prompt with administrator privileges. 
2. First, install the Python package for Azure management resources:

    ```
    pip install azure-mgmt-resource
    ```
3. To install the Python package for Data Factory, run the following command:

    ```
    pip install azure-mgmt-datafactory
    ```

    The [Python SDK for Data Factory](https://github.com/Azure/azure-sdk-for-python) supports Python 2.7, 3.3, 3.4, 3.5 and 3.6.

## Set values for placeholders
In the source code, set values to replace the following placeholders:

```python
# Specify your Azure subscription ID
subscription_id = '<Azure subscription ID>'

# Specify a name for the Azure resource group. 
rg_name = '<Azure resource group name>'

# Specify a name for the data factory. It must be globally unique.
df_name = '<Data factory name>'        

# Specify your Active Directory application ID, application authentication key, and tenant ID
credentials = ServicePrincipalCredentials(client_id='<AAD client ID>', secret='<AAD app authentication key>', tenant='<AAD tenant ID>')

# Specify your Azure storage account name and key
storage_string = SecureString('DefaultEndpointsProtocol=https;AccountName=<Azure storage account>;AccountKey=<Azure storage authentication key>')
```

## See Also
For step-by-steps instructions to create this sample from scratch, see [Quickstart: create a data factory and pipeline using Python](https://docs.microsoft.com/en-us/azure/data-factory/quickstart-create-data-factory-python).