<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/about-software-updates-deployments -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# About Software Updates Deployments

Software updates are delivered to client computers in Configuration Manager by creating software update deployments. It is a multistep process to create software update deployments by using the Configuration Manager SDK interfaces. A basic approach to deploying software updates, by using the Configuration Manager SDK interfaces, is outlined below.

For more information about software updates, see [Deploy and manage software updates](https://learn.microsoft.com/en-us/intune/configmgr/sum/understand/software-updates-introduction).

Note

Deleting updates or update bundles is not supported by the Configuration Manager SDK.

Select which software updates to install. This can be something such as running a query to identify which updates should be installed.

For information about queries that use criteria, such as selecting software updates for a specific knowledge base article, or selecting software updates that are a specific severity level, see [How to Enumerate Updates Matching a Specific Criteria](https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-enumerate-updates-matching-a-specific-criteria).

Obtain the configuration item identification \(CI\_ID\) values. The CI\_ID value identifies the software updates information across several classes. For the purposes of using the Configuration Manager SDK interfaces, the CI\_ID value is vital.

The CI\_ID value is a property of several classes and can be readily identified by using the [SMS\_SoftwareUpdate](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdate-server-wmi-class) class.

For more information about a number of queries that include the CI\_ID, see [How to Enumerate Updates Matching a Specific Criteria](https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-enumerate-updates-matching-a-specific-criteria).

Download the software update content. Software update content must be downloaded manually. To identify which contents must be downloaded, query the [SMS\_CIToContent](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_citocontent-server-wmi-class) class and obtain the list of `ContentID` properties that match the specific language criteria. After you have the list of `ContentID` properties, you can obtain the associated download URL and the related properties for the content files from the [SMS\_CIContentFiles](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cicontentfiles-server-wmi-class) class by using the `ContentID` properties you obtained earlier.

Create a software updates deployment package. The software updates deployment package holds the software updates content. For information about creating a deployment package, see [How to Create a Deployment Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-create-a-deployment-package).

Add update content to the software updates package. After a software updates deployment package has been created, software updates contents can be added to the package by using the [AddUpdateContent](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/addupdatecontent-method-in-class-sms_softwareupdatespackage) method in the [SMS\_SoftwareUpdatesPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatespackage-server-wmi-class) class. For information about adding software updates content to a deployment package, see [How to Add Updates to a Deployment Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-add-updates-to-a-deployment-package).

Create a software updates deployment to distribute the software updates. Distribute software updates by creating a software updates deployment. For information about the process for creating a software updates deployment, see [How to Configure and Deploy Updates](https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-configure-and-deploy-updates).

## See Also

[How to Enumerate Updates Matching a Specific Criteria](https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-enumerate-updates-matching-a-specific-criteria) [How to Create an Update List](https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-create-an-update-list) [How to Create a Deployment Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-create-a-deployment-package) [How to Add Updates to a Deployment Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-add-updates-to-a-deployment-package) [How to Delete Updates from a Deployment Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-delete-updates-from-a-deployment-package) [How to Configure and Deploy Updates](https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-configure-and-deploy-updates)
