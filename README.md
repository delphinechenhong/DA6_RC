# About AvePoint Cloud Backup for Office 365

AvePoint Cloud Backup for Office 365 ensures resiliency of service in the event of a disaster and quickly recovers lost or corrupted content from your backup. AvePoint Cloud Backup for Office 365 offers backup capabilities for all Office 365 instances, such as Exchange Online, OneDrive for Business, SharePoint Online, Office 365 Groups, Teams, Project Online, and Public Folders to protect your data. These object types are backed up and restored independently of one another.


**\*Note** : To view what&#39;s new in this release and access the user guide, click the question mark () button on the navigation pane.

AvePoint Cloud Backup for Office 365 supports protecting your Office 365 tenant that has the Multi-Geo license. For details on how it should be configured through AvePoint Online Services platform and gets protected in the AvePoint Cloud Backup for Office 365 app, refer to [Does AvePoint Online Services Support Office 365 Tenants with Multi-Geo Licenses?](https://avepointcdn.azureedge.net/assets/webhelp/avepoint-online-services/index.htm#!Documents/usecasedoesavepointonlineservicessupportoffice365tenantswithMulti-geolicenses.htm) in AvePoint Online Services User Guide for a quick tour.

If your Office tenant has Multi-Geo enabled, users assigned with multiple regions will be asked to select a region when accessing the AvePoint Cloud Backup for Office 365 interface, and the users with only one region will be automatically redirected to the regional Cloud Backup instance.

For more information on the supported and unsupported data types of Office 365 Backup, refer to SharePoint Sites Data Types, Project Online Data Types, Exchange Online Data Types, Office 365 Groups Data Types, Teams Data Types, andDocument-Related Data Types.

**\*Note the following** :

-
  - AvePoint Cloud Backup service for OneDrive for Business will protect the **Documents** library and will protect the **Site Assets** library as well if the site feature **Site NoteBook** is activated.

The service only protects content and permissions for OneDrive for Business, since OneDrive for Business is the cloud service used to securely store, share, and access your files.

-
  - **Preservation Hold** library is not protected by AvePoint Cloud Backup for Office 365.
  - AvePoint Cloud Backup for SharePoint Online also supports protecting **Communication Sites**. When restoring a deleted Communication Site to its original location, AvePoint Cloud Backup supports restoring the custom design of the Communication Site in the backup. If the Communication Site is registered through App Profile, the Communication Site can only be restored with the default design. Note that the comments in Communication Sites are not currently supported.
  - For locked site collections, the backup job will fail since locked site collections are inaccessible; for read-only site collections, the full backup job that runs once every year will back up them, but since no changes can be made to read-only site collections, the incremental backup jobs will skip them.
  - Project Online data cannot be protected in app context (using app profile authentication). AvePoint Cloud Backup cannot fully support the data added through Office 365 subscription Project Online desktop client. For example, custom fields.
  - The service for Public Folders only supports restoring content and permissions of Public Folder data to the original location without properties and settings (metadata).
  - AvePoint Cloud Backup for Office 365 now can check the status of groups and teams in Office 365 and provides the option to help you restore the soft-deleted groups and teams (within the 30-day retention period) from Office 365 recycle bin.
  - AvePoint Cloud Backup uses the Graph API beta version for the backup and restore of Teams&#39; tabs, since the Graph API 1.0 currently has limitations on supporting tabs.

**Backup Schedule**

The backup service will perform scheduled backups automatically and compress and encrypt backup data by default. The schedule of an object type starts with the first backup job. A new backup job will run every 6 hours. You can update the backup job frequency and schedule for each object type after you start the backup service. If there is a backup job in progress, the automatic backup job scheduled to run will be skipped.

Backup jobs can also be run manually if there is data that failed to be backed up during the last backup job. For detailed instructions on manually running backup jobs, refer to Manually Run a Backup.

**Split-Off and Pause SharePoint Online Backup**

If a backup job for SharePoint Online has been running for 14 days, we will look into it and identify if there is a higher volume of changes or very large sites that are causing the job to run longer. Rather than let these large sites slow down the rest of your SharePoint backups, we will split off the running sites into their own backup process which will continue to run in the background. For any content we&#39;ve already finished protecting we&#39;ll mark this job as &quot;Partially Finished&quot; in the backup dashboard in order to set a valid restore point. Any sites that are still in the queue to be backed up will be skipped and will be automatically included in the next backup, which should be kicking off shortly in order to maintain the best SLA for your standard sites.

The site collections that are currently being backed up will keep running in the background for the next 14 days. You can go to **Job Analytics** \&gt; Backup Overview tab to check for the progress of the site collections being protected and download the job report from Job Monitor to check the backup of the site collections that are currently being protected and the site collections that have been skipped but will be automatically be included in the next backup job. If the backup job hasn&#39;t been completed after running for the entire four weeks, it will be paused. You will receive e-mail notifications to check the job report for the details of the list being paused and the remaining content will be automatically included in the next backup job.

**Storage Location**

You can choose to store the backup data to the default storage location provided by AvePoint or your custom storage location. If you are currently using the default storage location and you want to use your own storage afterwards, you can contact AvePoint support to update your license and change the default storage to your own storage. The storage type of the default storage location is Microsoft Azure Blob Storage. The custom storage location can be one of the following five storage types: **Amazon S3** , **Dropbox** , **FTP** , **Microsoft Azure Blob Storage** , and **SFTP**. The backup data will be purged from the storage after the data reaches the retention period. If you use the default storage location, you can purchase a license with retention period that is multiple years (between 1 and 99) or unlimited years.

You can restore the backup data of these object types to the original location where they are backed up, to another destination, or restore them to a custom storage location. For details, refer to Restore Options for Different Object Types and Restore and Recover Your Data.

**\*Note** : If your device is **Microsoft Azure Blob Storage** , you must ensure that the data blob you select to restore is not at the archive access tier. The API cannot retrieve the content of blobs at the archive access tier. Before performing a restore job, AvePoint recommends changing the blob access tier from **Archive** to **Cool**. For details about blob access tiers and how to change access tiers, refer to the Microsoft article: [Azure Blob storage: hot, cool, and archive access tiers](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blob-storage-tiers).

**Retention**

If you use your own storage device and have purchased an unlimited data retention agreement, you can customize the data retention period for each service type. Prior to any data deletion, AvePoint Cloud Backup will send a notification e-mail informing you of the service data which will be deleted. You will still have time to either extend your retention period or export your data (a paid service).

## What is New in this Release

**Release Date:** September 2019

-
  - You can now configure App Setup Policies to include AvePoint Virtual Assistant (AVA) as a pinned App in Teams. After you edit the global policy or assign a policy, changes will take effect within 24 hours. For details, refer to Pin AVA to the App Bar in Teams.
  - Added the AVA Report to enable monitoring of AVA&#39;s activities throughout the organization. For details, refer to Use AVA Report.
  - Export jobs now support exporting Channel conversations and files for Microsoft Teams data. For details, refer to Export Teams Data.
  - Export jobs for Exchange Online now support downloading the exported data for each mailbox individually.
  - Added the **Remove Unprotected Data** page in **Data Management** to show the data found in the unprotected scope. Cloud Backup will remove the backup data for unprotected scope from our storage for the sake of your data privacy. For details, refer to Remove Unprotected Data.
  - Domain mapping for Project Online restore is now supported.
  - Teams Announcement type posts can now be backed up and restored.

The following updates have also been made to this user guide for this release:

-
  - Added Teams App - AVA.
  - Added Export Teams Data.
  - Updated Download the Exported Data.
  - Updated Restore Project Online Data.
  - Added Data Management.
  - Added Remove Unprotected Data.
  - Updated SharePoint Sites Data Types.
  - Added Public Folders Data Types.
  - Updated Teams Data Types.
  - Updated Document-Related Data Types.
  - Updated Data Types for Data Exporting.

For additional technical information on the new functionality in this release, see [Release Notes](https://avepointcdn.azureedge.net/assets/product_updates/avepoint-cloud-backup-for-office365/index.htm).

## How to Videos

This section contains video tutorials that can be used to enhance your experience in the AvePoint Cloud Backup for Office 365 User Guide.

###
#
[ANNOTATION:

BY &#39;Esther Merel&#39;
ON &#39;2019-03-22T12:33:00&#39;EM
NOTE: &#39;https://www.youtube.com/watch?v=BzFq9PpjiNw&amp;list=PLyJFOtpJV3wNpVlhBynPoMncFc3sPjzOa&amp;index=8&amp;t=0s&#39;
NOTE: &#39;&#39;]
How to Setup and Run Your First Cloud Backup Job

#
[ANNOTATION:

BY &#39;Doc-To-Help&#39;
ON &#39;2019-09-13T10:03:00&#39;EM
NOTE: &#39;D2HML|C1H Conditional|platform=htmlany;passthrough=true&#39;]
\&lt;!-- Movie in YouTube Format --\&gt;\&lt;iframe src=&quot;https://www.youtube.com/embed/B2DaMF6vm08?autohide=0&amp;amp;autoplay=1&amp;amp;fs=0&amp;amp;rel=0&amp;amp;modestbranding=0&amp;amp;showinfo=0&quot; frameborder=&quot;0&quot; allowfullscreen=&quot;1&quot; width=&quot;560&quot; height=&quot;315&quot; title=&quot;&quot;\&gt;\&lt;/iframe\&gt;

### How to Perform a Restore

#
[ANNOTATION:

BY &#39;Doc-To-Help&#39;
ON &#39;2019-09-13T10:16:00&#39;EM
NOTE: &#39;D2HML|C1H Conditional|platform=htmlany;passthrough=true&#39;]
\&lt;!-- Movie in YouTube Format --\&gt;\&lt;iframe src=&quot;https://www.youtube.com/embed/DjCzrEovtJ0?autohide=0&amp;amp;autoplay=1&amp;amp;fs=0&amp;amp;rel=0&amp;amp;modestbranding=0&amp;amp;showinfo=0&quot; frameborder=&quot;0&quot; allowfullscreen=&quot;1&quot; width=&quot;560&quot; height=&quot;315&quot; title=&quot;&quot;\&gt;\&lt;/iframe\&gt;

###
#
[ANNOTATION:

BY &#39;Esther Merel&#39;
ON &#39;2019-03-22T12:33:00&#39;EM
NOTE: &#39;https://www.youtube.com/watch?v=BzFq9PpjiNw&amp;list=PLyJFOtpJV3wNpVlhBynPoMncFc3sPjzOa&amp;index=8&amp;t=0s&#39;
NOTE: &#39;&#39;]
How to Scan and Register Groups and Teams in Office 365

#
[ANNOTATION:

BY &#39;Doc-To-Help&#39;
ON &#39;2019-09-13T09:55:00&#39;EM
NOTE: &#39;D2HML|C1H Conditional|platform=htmlany;passthrough=true&#39;]
\&lt;!-- Movie in YouTube Format --\&gt;\&lt;iframe src=&quot;https://www.youtube.com/embed/vTAT1ElOrhM?autohide=0&amp;amp;autoplay=1&amp;amp;fs=0&amp;amp;rel=0&amp;amp;modestbranding=0&amp;amp;showinfo=0&quot; frameborder=&quot;0&quot; allowfullscreen=&quot;1&quot; width=&quot;560&quot; height=&quot;315&quot; title=&quot;&quot;\&gt;\&lt;/iframe\&gt;

###
#
[ANNOTATION:

BY &#39;Esther Merel&#39;
ON &#39;2019-03-22T12:33:00&#39;EM
NOTE: &#39;https://www.youtube.com/watch?v=BzFq9PpjiNw&amp;list=PLyJFOtpJV3wNpVlhBynPoMncFc3sPjzOa&amp;index=8&amp;t=0s&#39;
NOTE: &#39;&#39;]
How to Restore Groups and Teams

#
[ANNOTATION:

BY &#39;Doc-To-Help&#39;
ON &#39;2019-03-22T12:31:00&#39;EM
NOTE: &#39;D2HML|C1H Conditional|platform=htmlany;passthrough=true&#39;]
\&lt;!-- Movie in YouTube Format --\&gt;\&lt;iframe src=&quot;https://www.youtube.com/embed/BzFq9PpjiNw?autohide=0&amp;amp;autoplay=1&amp;amp;fs=0&amp;amp;rel=0&amp;amp;modestbranding=0&amp;amp;showinfo=0&quot; frameborder=&quot;0&quot; allowfullscreen=&quot;1&quot; width=&quot;560&quot; height=&quot;315&quot; title=&quot;&quot;\&gt;\&lt;/iframe\&gt;

For additional information on how to restore Groups and Teams with AvePoint Cloud Backup for Office 365, see Restore Teams Data and Restore Office 365 Groups Data.

### How to Bring Your Own Storage Location

#
[ANNOTATION:

BY &#39;Doc-To-Help&#39;
ON &#39;2019-09-13T10:19:00&#39;EM
NOTE: &#39;D2HML|C1H Conditional|platform=htmlany;passthrough=true&#39;]
\&lt;!-- Movie in YouTube Format --\&gt;\&lt;iframe src=&quot;https://www.youtube.com/embed/FnfDOC5obd0?autohide=0&amp;amp;autoplay=1&amp;amp;fs=0&amp;amp;rel=0&amp;amp;modestbranding=0&amp;amp;showinfo=0&quot; frameborder=&quot;0&quot; allowfullscreen=&quot;1&quot; width=&quot;560&quot; height=&quot;315&quot; title=&quot;&quot;\&gt;\&lt;/iframe\&gt;

###
#
[ANNOTATION:

BY &#39;Esther Merel&#39;
ON &#39;2019-03-22T12:35:00&#39;EM
NOTE: &#39;https://www.youtube.com/watch?v=Sh4g5m\_U3WI&amp;list=PLyJFOtpJV3wNpVlhBynPoMncFc3sPjzOa&amp;index=12&#39;
NOTE: &#39;&#39;]

#
[ANNOTATION:

BY &#39;Esther Merel&#39;
ON &#39;2019-03-22T12:35:00&#39;EM
NOTE: &#39;https://youtu.be/Sh4g5m\_U3WI&#39;]
How to Filter Objects

#
[ANNOTATION:

BY &#39;Doc-To-Help&#39;
ON &#39;2019-09-13T10:00:00&#39;EM
NOTE: &#39;D2HML|C1H Conditional|platform=htmlany;passthrough=true&#39;]
\&lt;!-- Movie in YouTube Format --\&gt;\&lt;iframe src=&quot;https://www.youtube.com/embed/Sh4g5m\_U3WI?autohide=0&amp;amp;autoplay=1&amp;amp;fs=0&amp;amp;rel=0&amp;amp;modestbranding=0&amp;amp;showinfo=0&quot; frameborder=&quot;0&quot; allowfullscreen=&quot;1&quot; width=&quot;560&quot; height=&quot;315&quot; title=&quot;&quot;\&gt;\&lt;/iframe\&gt;

### How to Install AvePoint Virtual Assistant

#
[ANNOTATION:

BY &#39;Doc-To-Help&#39;
ON &#39;2019-09-13T09:56:00&#39;EM
NOTE: &#39;D2HML|C1H Conditional|platform=htmlany;passthrough=true&#39;]
\&lt;!-- Movie in YouTube Format --\&gt;\&lt;iframe src=&quot;https://www.youtube.com/embed/31zN3ySD7ME?autohide=0&amp;amp;autoplay=1&amp;amp;fs=0&amp;amp;rel=0&amp;amp;modestbranding=0&amp;amp;showinfo=0&quot; frameborder=&quot;0&quot; allowfullscreen=&quot;1&quot; width=&quot;560&quot; height=&quot;315&quot; title=&quot;&quot;\&gt;\&lt;/iframe\&gt;

### How to Restore with AvePoint Virtual Assistant

#
[ANNOTATION:

BY &#39;Doc-To-Help&#39;
ON &#39;2019-09-13T09:56:00&#39;EM
NOTE: &#39;D2HML|C1H Conditional|platform=htmlany;passthrough=true&#39;]
\&lt;!-- Movie in YouTube Format --\&gt;\&lt;iframe src=&quot;https://www.youtube.com/embed/b183dgYA\_YE?autohide=0&amp;amp;autoplay=1&amp;amp;fs=0&amp;amp;rel=0&amp;amp;modestbranding=0&amp;amp;showinfo=0&quot; frameborder=&quot;0&quot; allowfullscreen=&quot;1&quot; width=&quot;560&quot; height=&quot;315&quot; title=&quot;&quot;\&gt;\&lt;/iframe\&gt;



## Use Cases

### Use Case - Want to Delegate Restore Permissions?



1. Click **Add apps**.
2. In the **Add pinned apps** panel, enter **AVA** in the search box, select the app, and then click **Add**.
3. Click **Add** at the bottom of the panel.

1. You can also set the order for the apps pinned in the app bar. Select the app and click **Move up** or **Move down**.
2. Click **Save** to save the app setup policy. The changes will take effect within 24 hours.

## FAQs

If I move from Classic DocAve Backup (Granular Backup &amp; Restore and Exchange Online Backup &amp; Restore) to AvePoint Cloud Backup for Office 365, can I still use the Classic DocAve Backup data to restore?

You may have the following use cases when moving from Classic DocAve Backup to AvePoint Cloud Backup:

-
  - Use AvePoint Cloud Backup to protect the same Office 365 tenant that Classic DocAve Backup has protected.
  - You are currently using Classic DocAve Backup to protect your Office 365 tenant A, but you want to move to Office 365 tenant B and use AvePoint Cloud Backup to protect the new Office 365 tenant.

In either of the use cases above, you can go to Classic DocAve Backup to restore the previous backup data if you have purchased the AvePoint Cloud Backup license. Check the following to ensure you are well on track:

-
  - The users who will be used to run the restore job, such as the service accounts, account pool users, or the user registered in app profile, still exist and have the required permissions and licenses.
  - You will only use AvePoint Cloud Backup for data protection, which means you can no longer run backup jobs in Classic DocAve Backup.

I am currently using AvePoint default storage to store backup data. If I end my subscription, would I ever be able to recover the backup data from AvePoint?

When a subscription ends, AvePoint will retain the backup data in AvePoint storage for 15 days, subject to the terms of your service agreement. The backup data in AvePoint storage can be exported to your own storage as a paid service. You must submit an export request if you wish to export your data from AvePoint storage.

If you have the BYOS (bring your own storage) license, the backup data will remain in your own storage until you delete it, and you will not need to pay an export fee.

Note that the backup data is stored in AvePoint format, and not as pure copies of Office 365 data. AvePoint recommends the following solutions to restore your backup data to readable content:

| DocAve 6 SP11 (with a free restore license) | SharePoint Online site collectionsOneDrive for BusinessOffice 365 Group team site |
| --- | --- |
| Stand-alone Data Export Tool | Exchange Online mailboxesPublic FoldersOffice 365 Group mailboxes |

If you would like additional details or assistance with this process, contact your AvePoint representative.

Does AvePoint Cloud Backup for Office 365 Support Data Deduplication and Compression?

AvePoint Cloud Backup for Office 365 applies standard .zip compression to data. Though our DAT files can support deduplication algorithms, we currently do not support deduplication on Blob storage as this necessitates a physical/virtual storage system which is not as cost effective as Azure Cool storage. Additionally, since our backup data is encrypted, and the encryption key is dynamic, the deduplication performance may not be optimal.

I have a document that had an external user shared to it. Does AvePoint Cloud Backup support restoring the external user and its permission that were part of that document?

For the external users that have been added to your Azure AD, its permissions will be kept when the document shared with it has been restored. However, AvePoint Cloud Backup does not support protecting the external sharing data of that document. The external sharing in Office 365 consists of two elements: the shared link and the external user and its permission. Currently, the shared links are not included in the backup scope, which means, after being restored, the external users can no longer use the shared link to access that document.

My organization plans to use the Customer Key feature in Office 365 so we will be in control of our own encryption keys for our data in Office 365. Will AvePoint Cloud Backup backs up and restores this data if it is enabled?

The customer key feature in Office 365 encrypts the data at rest in Office 365, which indicates that Microsoft cannot access this encrypted data. However, AvePoint Cloud Backup for Office 365 uses user credentials or app profile to access customer data with API, same as the end user accessing scenario where the data will be decrypted to real content. Therefore, the backup and restore service will not be affected. For more details, you can refer to [this FAQ](https://docs.microsoft.com/en-us/office365/securitycompliance/service-encryption-with-customer-key-faq#what-is-the-difference-between-customer-key-and-bring-your-own-key-byok-with-azure-information-protection-for-exchange-online) from Microsoft website.

How do I restore term store only data?

You can choose the following solutions:

-
  - If you want to restore global term store data, select any site collection in your tenant and use **Skip** as the conflict resolution for all to perform a restore job.
  - If you want to restore local term store data for a site collection, select that site collection to restore and use **Skip** as the conflict resolution for all to perform a restore job.
