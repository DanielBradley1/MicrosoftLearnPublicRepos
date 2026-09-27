<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/manage-collections -->
<!-- Sitemap-Last-Modified: 2023-02-22 -->

# How to manage collections in Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

Use the overview information in this article to help you run management tasks for collections in Configuration Manager.

For information about how to create Configuration Manager collections, see [How to create collections](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/create-collections).

## Collection actions

In the Configuration Manager console, go to the **Assets and Compliance** workspace. Select **Device Collections** or **User Collections**, select the collection to manage, and then select a management task.

### Manage device collections

#### Show Members

Displays all of the resources that are members of the selected collection in a temporary node under the **Devices** node.

#### Add Selected Items

Provides the following options:

- **Add Selected Items to Existing Device Collection**: Opens the **Select Collection** window. Select the collection to which you want to add the members of the selected collection. The selected collection is included in this collection by using an **Include Collections** membership rule.
- **Add Selected Items to New Device Collection**: Opens the **Create Device Collection Wizard** where you can create a new collection. The selected collection is included in this collection by using an **Include Collections** membership rule.

For more information, see [How to create collections](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/create-collections).

#### Install Client

Opens the **Install Client Wizard**. This wizard uses client push installation to install a Configuration Manager client on all computers in the selected collection. For more information, see [Client push installation](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientPush).

#### Run Script

Opens the **Run Script** wizard to run a PowerShell script on all of the clients in the collection. For more information, see [Create and run PowerShell scripts](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/create-deploy-scripts).

#### Start CMPivot

Opens CMPivot for this collection. Use CMPivot to query device information and take action in real time. For more information, see [CMPivot for real-time data](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/cmpivot).

#### Manage Affinity requests

Opens the **Manage User Device Affinity Requests** dialog box. Approve or reject pending requests to establish user device affinities for devices in the selected collection. For more information, see [Link users and devices with user device affinity](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/link-users-and-devices-with-user-device-affinity).

#### Clear Required PXE deployments

Clears any required PXE boot deployments from all members of the selected collection. For more information, see [Use PXE to deploy Windows over the network](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/use-pxe-to-deploy-windows-over-the-network).

#### Update membership

Evaluates the membership for the selected collection. For collections with many members, this update might take some time to finish. Use the **Refresh** action to update the display with the new collections members after the update is completed.

#### Synchronize membership

If you configured this collection for cloud sync, synchronize the current membership with a Microsoft Entra group. For more information, see [Create collections](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/create-collections#bkmk_aadcollsync).

#### Add resources

Opens the **Add Resources to Collection** window. Search for new resources to add to the selected collection. The icon for the selected collection displays an hourglass symbol while the update is in progress.

#### Client notification

For more information, see [Client notifications](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/client-notification).

#### Client diagnostics

Displays the following options:

- **Enable verbose logging**
- **Disable verbose logging**
- **Collect client logs**

For more information, see [Client diagnostics](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/client-notification#client-diagnostics).

#### Endpoint Protection

For more information, see [Client notifications: Endpoint protection](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/client-notification#endpoint-protection).

#### Export

Opens the **Export Collection Wizard** that helps you export this collection to a Managed Object Format \(MOF\) file. You can then archive this file, or import it to another Configuration Manager site. When you export a collection, referenced collections aren't exported. A referenced collection is referenced by the selected collection by using an **Include** or **Exclude** rule.

#### Copy

Creates a copy of the selected collection. The new collection uses the selected collection as a limiting collection.

#### Refresh

Refresh the view.

#### Delete

Deletes the selected collection. You can also delete all of the resources in the collection from the site database.

You can't delete the collections that are built into Configuration Manager. For a list of the built-in collections, see [Introduction to collections](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/introduction-to-collections#built-in-collections).

Starting in version 2203, when you delete a collection, you can review and delete its dependent collections at the same time. For more information, see [Delete collection references](#delete-collection-references).

#### Simulate deployment

Opens the **Simulate Application Deployment Wizard**. This wizard lets you test the results of an application deployment without installing or uninstalling the application. For more information, see [How to simulate application deployments](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/simulate-application-deployments).

#### Deploy

Displays the following options:

- **Application**: Opens the **Deploy Software Wizard**. Select and configure an application deployment to the selected collection. For more information, see [How to deploy applications](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/deploy-applications).
- **Program**: Opens the **Deploy Software Wizard**. Select and configure a package and program deployment to the selected collection. For more information, see [Packages and programs](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/packages-and-programs).
- **Configuration Baseline**: Opens the **Deploy Configuration Baselines** window. Configure the deployment of one or more configuration baselines to the selected collection. For more information, see [How to deploy configuration baselines](https://learn.microsoft.com/en-us/intune/configmgr/compliance/deploy-use/deploy-configuration-baselines).
- **Task Sequence**: Opens the **Deploy Software Wizard**. Select and configure a task sequence deployment to the selected collection. For more information, see [Deploy a task sequence](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/deploy-a-task-sequence).
- **Software Updates**: Opens the **Deploy Software Updates Wizard**. Configure the deployment of software updates to resources in the selected collection. For more information, see [Deploy software updates](https://learn.microsoft.com/en-us/intune/configmgr/sum/deploy-use/deploy-software-updates).

#### View relationships

For more information, see [View collection relationships](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/view-relationships).

#### Move

Move the selected collection to another folder in the **Device Collections** node.

#### Properties

For more information, see [Collection properties](#collection-properties).

### Delete collection references

Previously, when you would delete a collection with dependent collections, you first had to delete the dependencies. The process of finding and deleting all of these collections could be difficult and time consuming. Starting in version 2203, when you delete a collection, you can review and delete its dependent collections at the same time.

A new **Details** window shows more information about the relationship types, and lets you [view collection relationships](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/view-relationships) in a graphical chart.

[![View collection dependencies in list and graphical form when deleting a collection](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/media/9708999-delete-collection-references.png)](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/media/9708999-delete-collection-references.png#lightbox)

1. Delete a collection that has dependent collections.
2. In the **Delete Collection Error** window, select **Details**.
3. Once the relationship types finish loading, select **View Relationships** to see the graph.
4. If all of the dependent collections can be deleted, select **Delete all listed collections**.
5. Review the list of collections and any software deployments that the site will also remove. You also can **Delete each collection member from the database**.

There are several reasons why the site can't delete a dependent collection:

- **Assigned to user**: For more information, see [Modify the administrative scope of an administrative user](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/configure-role-based-administration#modify-the-administrative-scope-of-an-administrative-user).
- **Used by cloud attach**: For more information, see [Enable cloud attach for Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/cloud-attach/enable).
- **Use for upload to Microsoft Intune**: For more information, see [Make Configuration Manager collections available to assign Endpoint security policies](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/endpoint-security-get-started#bkmk_collections).

The details window lists collections that can't be deleted with the reason why.

#### Known issue when deleting collection references

Consider the scenario where you're deleting collections with references, and another administrative user is simultaneously creating a reference to a collection that you're deleting. When this behavior occurs, the console displays an error, and the collection isn't deleted.

### Manage user collections

The following actions are available on user collections. The behaviors are the same as with device collections, other than they apply to user collections and the users within. For more information, see the corresponding action under [Manage device collections](#manage-device-collections).

- Show Members
- Add Selected Items

  - Add Selected Items to Existing User Collection
  - Add Selected Items to New User Collection

- Manage Affinity Requests
- Update Membership
- Synchronize Membership
- Add Resources
- Export
- Copy
- Refresh
- Delete
- Simulate Deployment
- Deploy

  - Application
  - Program
  - Configuration Baseline

- View Relationships
- Move
- Properties

## Collection properties

When you view properties for a collection, you can view and configure the following options:

- **General**: View and configure general information about the selected collection including the collection name, the limiting collection, the collection ID, and last update times.
- **Membership Rules**: Configure the membership rules that define the membership of this collection. For more information, see [How to create collections](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/create-collections).
- **Power Management**: Configure power management plans that you've assigned to computers in the selected collection. For more information, see [Introduction to power management](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/power/introduction-to-power-management).
- **Deployments**: Displays any software that you've deployed to members of the selected collection.
- **Maintenance Windows**: View and configure maintenance windows that are applied to members of the selected collection. For more information, see [How to use maintenance windows](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/use-maintenance-windows).
- **Collection Variables**: Configure variables that apply to this collection and can be used by task sequences. For more information, see [How to set task sequence variables](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/using-task-sequence-variables#bkmk_set).
- **Distribution Point Groups**: Associate one or more distribution point groups to members of the selected collection. For more information, see [Manage content and content infrastructure](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/manage-content-and-content-infrastructure).
- **Cloud Sync**: Synchronize collection membership results to Microsoft Entra groups. For more information, see [Create collections](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/create-collections#bkmk_aadcollsync).

  Starting in version 2006, you can also make this collection available to assign endpoint security policies when you tenant-attach the site. For more information, see [Tenant attach: Onboard Configuration Manager clients to Microsoft Defender for Endpoint from the admin center](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/atp-onboard).
- **Security**: Displays the administrative users who have permissions for the selected collection from associated roles and security scopes. For more information, see [Fundamentals of role-based administration](https://learn.microsoft.com/en-us/intune/configmgr/core/understand/fundamentals-of-role-based-administration).
- **Alerts**: Configure when alerts are generated for client status and endpoint protection. For more information, see [How to configure client status](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/configure-client-status) and [How to monitor endpoint protection](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/monitor-endpoint-protection).

## Automate with Windows PowerShell

You can use the following PowerShell cmdlets to manage collections:

### Generic cmdlets for all collection types

#### Basic cmdlets

- [Get-CMCollection](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/get-cmcollection)
- [New-CMCollection](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/new-cmcollection)
- [Remove-CMCollection](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/remove-cmcollection)
- [Set-CMCollection](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/set-cmcollection)

#### Other actions

- [Copy-CMCollection](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/copy-cmcollection)
- [Export-CMCollection](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/export-cmcollection)
- [Get-CMCollectionMember](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/get-cmcollectionmember)
- [Get-CMCollectionSetting](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/get-cmcollectionsetting)
- [Import-CMCollection](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/import-cmcollection)
- [Invoke-CMCollectionUpdate](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/invoke-cmcollectionupdate)

#### Get membership rules

- [Get-CMCollectionDirectMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/get-cmcollectiondirectmembershiprule)
- [Get-CMCollectionExcludeMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/get-cmcollectionexcludemembershiprule)
- [Get-CMCollectionIncludeMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/get-cmcollectionincludemembershiprule)
- [Get-CMCollectionQueryMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/get-cmcollectionquerymembershiprule)

#### Remove membership rules

- [Remove-CMCollectionDirectMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/remove-cmcollectiondirectmembershiprule)
- [Remove-CMCollectionExcludeMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/remove-cmcollectionexcludemembershiprule)
- [Remove-CMCollectionIncludeMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/remove-cmcollectionincludemembershiprule)
- [Remove-CMCollectionQueryMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/remove-cmcollectionquerymembershiprule)

### Device collection-specific cmdlets

#### Basic actions for device collections

- [Get-CMDeviceCollection](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/get-cmdevicecollection)
- [New-CMDeviceCollection](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/new-cmdevicecollection)

#### Device collection variables

- [Get-CMDeviceCollectionVariable](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/get-cmdevicecollectionvariable)
- [New-CMDeviceCollectionVariable](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/new-cmdevicecollectionvariable)
- [Remove-CMDeviceCollectionVariable](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/remove-cmdevicecollectionvariable)
- [Set-CMDeviceCollectionVariable](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/set-cmdevicecollectionvariable)

#### Add device collection membership rules

- [Add-CMDeviceCollectionDirectMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/add-cmdevicecollectiondirectmembershiprule)
- [Add-CMDeviceCollectionExcludeMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/add-cmdevicecollectionexcludemembershiprule)
- [Add-CMDeviceCollectionIncludeMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/add-cmdevicecollectionincludemembershiprule)
- [Add-CMDeviceCollectionQueryMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/add-cmdevicecollectionquerymembershiprule)

#### Get device collection membership rules

- [Get-CMDeviceCollectionDirectMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/get-cmdevicecollectiondirectmembershiprule)
- [Get-CMDeviceCollectionExcludeMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/get-cmdevicecollectionexcludemembershiprule)
- [Get-CMDeviceCollectionIncludeMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/get-cmdevicecollectionincludemembershiprule)
- [Get-CMDeviceCollectionQueryMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/get-cmdevicecollectionquerymembershiprule)

#### Remove device collection membership rules

- [Remove-CMDeviceCollectionDirectMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/remove-cmdevicecollectiondirectmembershiprule)
- [Remove-CMDeviceCollectionExcludeMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/remove-cmdevicecollectionexcludemembershiprule)
- [Remove-CMDeviceCollectionIncludeMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/remove-cmdevicecollectionincludemembershiprule)
- [Remove-CMDeviceCollectionQueryMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/remove-cmdevicecollectionquerymembershiprule)

### User collection-specific cmdlets

- [Get-CMUserCollection](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/get-cmusercollection)
- [New-CMUserCollection](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/new-cmusercollection)

#### Add user collection membership rules

- [Add-CMUserCollectionDirectMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/add-cmusercollectiondirectmembershiprule)
- [Add-CMUserCollectionExcludeMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/add-cmusercollectionexcludemembershiprule)
- [Add-CMUserCollectionIncludeMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/add-cmusercollectionincludemembershiprule)
- [Add-CMUserCollectionQueryMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/add-cmusercollectionquerymembershiprule)

#### Get user collection membership rules

- [Get-CMUserCollectionDirectMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/get-cmusercollectiondirectmembershiprule)
- [Get-CMUserCollectionExcludeMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/get-cmusercollectionexcludemembershiprule)
- [Get-CMUserCollectionIncludeMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/get-cmusercollectionincludemembershiprule)
- [Get-CMUserCollectionQueryMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/get-cmusercollectionquerymembershiprule)

#### Remove user collection membership rules

- [Remove-CMUserCollectionDirectMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/remove-cmusercollectiondirectmembershiprule)
- [Remove-CMUserCollectionExcludeMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/remove-cmusercollectionexcludemembershiprule)
- [Remove-CMUserCollectionIncludeMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/remove-cmusercollectionincludemembershiprule)
- [Remove-CMUserCollectionQueryMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/remove-cmusercollectionquerymembershiprule)

## Next steps

[Client notifications](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/client-notification)

[View collection relationships](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/view-relationships)
