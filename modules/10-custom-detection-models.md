---
lab:
    title: 'Custom Object Detection Models'
---
## Module 10: Custom Object Detection Models

### Create an Azure Storage Account
In this unit, you'll use the Azure portal to create a storage account for storing and loading image data for use in training an object detection model using Azure Machine Learning studio.

#### Create an Azure Storage Account
1. Sign in to the [Azure portal](https://portal.azure.com/) using the account that you've prepared for this learning path.
1. On the resource menu, or from the Home page, select the hamburger button in the upper left then select Storage accounts from the drop-down menu. The Storage accounts pane appears.
1. On the command bar, select Create. The Create a storage account pane appears.
1. On the Basics tab, enter the following values for each setting.
| Setting | Value |
|---------|-------|
| Project details | |
| Subscription | <Your Subscription> |
| Resource group | <Create New> OR <Select an Existing Resource Group> |
| Instance details | |
| Storage account name | Enter a unique name. This name will be used to generate the public URL to access the data in the account. The name must be unique across all existing storage account names in Azure. Names must have 3 to 24 characters and can contain only lowercase letters and numbers. Take note of the Storage Account Name as this value will be needed later on when we create a Datastore in Azure Machine Learning Studio.|
| Region | Select a location near to you from the dropdown list.
Performance	Standard. This option decides the type of disk storage used to hold the data in the Storage account. Standard uses traditional hard disks, and Premium uses solid-state drives (SSD) for faster access. |
| Redundancy | Select Locally redundant storage (LRS) from the dropdown list. This low-cost option will satisfy our requirements for this learning path, however, you're welcome to choose a different option depending on your individual needs. |

1. Select **Next : Advanced**. On the Advanced tab, enter the following values for each setting.
| Setting | Value |
|---------|-------|
| Security | |
| Require secure transfer for REST API operations | Check. This setting controls whether HTTP can be used for the REST APIs that access data in the storage account. Setting this option to enable forces all clients to use SSL (HTTPS). Most of the time, you'll want to set secure transfer to enable; using HTTPS over the network is considered a best practice. |
| Enable blob public access | Check. We'll allow clients to read data in that container without authorizing the request. |
| Enable storage account key access | Check. We'll allow clients to access data via SAS. |
| Default to Microsoft Entra authorization in the Azure portal |	Uncheck. Clients are public, not part of an Active Directory.
Minimum TLS version	Select Version 1.2 from dropdown list. TLS 1.2 is the most secure version of TLS and is used by Azure Storage on public HTTPS endpoints. TLS 1.1 and 1.0 is supported for backwards compatibility. See Warning at end of table. |
| Data Lake Storage Gen2 |  |
| Enable hierarchical namespace | Uncheck. Data Lake hierarchical namespace is for big-data applications that aren't relevant to this module. |
| Secure File Transfer Protocol (SFTP) |
Enable SFTP	Uncheck. SFTP is disabled by default and isn't relevant to this module. |
| Blob storage |  |	
| Enable network file share | Uncheck (default). |
| Allow cross-tenant replication | Uncheck. Active Directory isn't being used for this exercise. | 
| Access tier | Hot. This setting is only used for Blob storage. The Hot access tier is ideal for frequently accessed data; the Cool access tier is better for infrequently accessed data. This setting only sets the default value. When you create a Blob, you can set a different value for the data. In our case, we want our image data to load quickly, so we'll use the high-performance option for our blobs. |
| Azure Files | |
| Enable large file shares | Uncheck. Large file shares provide support up to a 100 TiB, however this type of storage account can't convert to a Geo-redundant storage offering, and upgrades are permanent. | 

> Warning
> If Enable large file shares is selected, it will enforce additional restrictions, and Azure files service connections without encryption will fail, including scenarios using SMB 2.1 or 3.0 on Linux. Because Azure storage doesn't support SSL for custom domain names, this option cannot be used with a custom domain name.

1. Select **Next : Networking**. On the Networking tab, enter the following values for each setting.
| Setting | Value |
|---------|-------|
| Network connectivity | |
 |Connectivity method | Public endpoint (all networks). We want to allow public Internet access. Our content is public facing, and we need to allow access from public clients.
Network routing	|
| Routing preference | Microsoft network routing. We want to make use of the Microsoft global network that is optimized for low-latency path selection. | 

1. Select **Next : Data protection**. On the Data protection tab, enter the following values for each setting.
| Setting | Value |
|---------|-------|
| Recovery | |
| Enable point-in-time restore for containers | Uncheck. Not necessary for this implementation. |
| Enable soft delete for blobs | Check. Soft delete lets you recover blob data in cases where blobs or blob snapshots are deleted accidentally or overwritten. |
| Enable soft delete for containers	Check. Soft delete lets you recover your containers that are deleted accidentally. |
|Enable soft delete for file shares | Check. File share soft delete lets you recover your blob data more easily at the folder level. |
| Tracking | 
Enable versioning for blobs	Uncheck. Not necessary for this implementation. |
| Enable blob change feed | Uncheck. Not necessary for this implementation. |
| Access control | |
| Enable version-level immutability support | Uncheck. Not necessary for this implementation. |

1. Select **Next : Encryption**. Accept the defaults.

1. Select **Next : Tags**. Here, you can associate key/value pairs with the account for your categorization to determine if a feature is available to selected Azure resources.

1. Select **Review + create** to validate your options and to ensure all the required fields are selected. If there are issues, this tab will identify them so you can correct them.

1. When validation passes successfully, select Create to deploy the storage account.

1. When deployment is complete, which may take up to two minutes, select **Go to resource** to view **Essential** details about your new storage account.

![Storage Overview](../images/10/3-storage-overview.png)

Take note of the Storage Account Name as this value will be needed later on when we create a Datastore in Azure Machine Learning Studio.

