
# Create an Azure Data Lake Store account
1. Sign on to the new Azure portal.
2. Click NEW, click Data + Storage, and then click Azure Data Lake Store. Read the information in the Azure Data Lake Store blade, and then click Create in the bottom left corner of the blade.
3. In the New Data Lake Store blade, provide the values as follows:

  * Name. Enter a unique name for the Data Lake Store account.
  * Subscription. Select the subscription under which you want to create a new Data Lake Store account.
  * Resource Group. Select an existing resource group, or select the Create new option to create one. 
  * Location: Select a location where you want to create the Data Lake Store account.
  * Encryption Settings. There are three options:

    + Do not enable encryption.
    + Use keys managed by Azure Data Lake. if you want Azure Data Lake Store to manage your encryption keys.
    + Use keys from your own Key Vault. You can select an existing Azure Key Vault or create a new Key Vault. To use the keys from a Key Vault, you must assign permissions for the Azure Data Lake Store account to access the Azure Key Vault. 

4. Click OK in the Encryption Settings blade.
5. Click Create. If you chose to pin the account to the dashboard, you are taken back to the dashboard and you can see the progress of your Data Lake Store account provisioning. Once the Data Lake Store account is provisioned, the account blade shows up.

# Create folders in Azure Data Lake Store account
You can create folders under your Data Lake Store account to manage and store data.

6. Open the Data Lake Store account that you created. From the left pane, click Browse, click Data Lake Store, and then from the Data Lake Store blade, click the account name under which you want to create folders. If you pinned the account to the startboard, click that account tile.
7. In your Data Lake Store account blade, click Data Explorer.
8. Create folders in Data Lake Store account
9. From Data Explorer blade, click New Folder, enter a name for the new folder, and then click OK.
10. The newly created folder is listed in the Data Explorer blade. You can create nested folders upto any level.

# Upload data to Azure Data Lake Store account and perform actions against it
There are different ways to ingest data into a Data Lake Store account. We will explore a few here.

![Ingest data into Data Lake Store](https://docs.microsoft.com/en-us/azure/data-lake-store/media/data-lake-store-data-scenarios/ingest-data.png)

## Portal and Tools
You can upload your data to an Azure Data Lake Store account directly at the root level or to a folder that you created within the account.

11. From the Data Explorer blade, click Upload.
12. In the Upload files blade, navigate to the files you want to upload, and then click Add selected files. You can also select more than one file to upload.
13. Click the ellipsis icon against a file, and from the pop-up menu, click the action you want to perform on the data.

## ADLCopy

Azure Data Lake Store provides a command line tool, AdlCopy, to copy data from the following sources:
  + From Azure Storage Blobs into Data Lake Store. You cannot use AdlCopy to copy data from Data Lake Store to Azure Storage blobs.
  + Between two Azure Data Lake Store accounts.

Also, you can use the AdlCopy tool in two different modes:
  + Standalone, where the tool uses Data Lake Store resources to perform the task.
  + Using a Data Lake Analytics account, where the units assigned to your Data Lake Analytics account are used to perform the copy operation. You might want to use this option when you are looking to perform the copy tasks in a predictable manner.

14. Open the Azure portal and click on All Resources.
15. Select an Azure Storage account and click on it.
16. Click on Blobs -> Container -> Container properties.
17. Copy the URL.
18. See if the container has any data. If not, upload the Flights data to it using any of the methods discussed earlier.
19. Download and install AdlCopy(http://aka.ms/downloadadlcopy).
20. Navigate to the location where it was installed. (Try C:\Users\username\Documents\AdlCopy)
21. Type the following and hit Enter.

AdlCopy /Source BlobURL /dest ADLURL /sourcekey BlobKey /Account ADLAaccount /Units 10 /Pattern *.csv
