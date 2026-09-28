<!-- Source: https://learn.microsoft.com/en-us/graph/templates/terraform/reference/beta/groups -->
<!-- Sitemap-Last-Modified: 2025-08-04 -->

# groups

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

Note

Permissions for personal Microsoft accounts cannot be used to deploy Microsoft Graph resources declared in Terraform files.

### Resource deployment

Choose the least privileged permission from the following table to create or update a `groups` resource.

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Group.ReadWrite.All | Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Group.ReadWrite.All | Directory.ReadWrite.All |

### Read existing resources only

Choose the least privileged permission from the following table to read a `groups` resource using the `msgraph_resource` data source.

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Group-NestingSupport.ReadWrite.All | Directory.Read.All, Directory.ReadWrite.All, Group-XTenantIdentitySync.Read.All, Group.ManageProtection.All, Group.Read.All, Group.ReadWrite.All, GroupMember.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Group-NestingSupport.ReadWrite.All | Directory.Read.All, Directory.ReadWrite.All, Group-XTenantIdentitySync.Read.All, Group.ManageProtection.All, Group.Read.All, Group.ReadWrite.All, GroupMember.Read.All |

## Resource format

To create a `groups` resource, add the following Terraform configuration to your Terraform configuration.

```terraform
resource "msgraph_resource" "symbolicname" {
  url = "groups@beta"
  body = {
    allowExternalSenders = bool
    assignedLabels = [
      {
        displayName = "string"
        labelId = "string"
      }
    ]
    assignedLicenses = [
      {
        disabledPlans = "string"
        skuId = "string"
      }
    ]
    autoSubscribeNewMembers = bool
    classification = "string"
    createdDateTime = "string"
    deletedDateTime = "string"
    description = "string"
    displayName = "string"
    expirationDateTime = "string"
    groupTypes = [
      "string"
    ]
    hasMembersWithLicenseErrors = bool
    hideFromAddressLists = bool
    hideFromOutlookClients = bool
    id = "string"
    isArchived = bool
    isAssignableToRole = bool
    isManagementRestricted = bool
    isSubscribedByMail = bool
    licenseProcessingState = {
      state = "string"
    }
    mail = "string"
    mailEnabled = bool
    mailNickname = "string"
    membershipRule = "string"
    membershipRuleProcessingState = "string"
    onPremisesDomainName = "string"
    onPremisesLastSyncDateTime = "string"
    onPremisesNetBiosName = "string"
    onPremisesProvisioningErrors = [
      {
        category = "string"
        occurredDateTime = "string"
        propertyCausingError = "string"
        value = "string"
      }
    ]
    onPremisesSamAccountName = "string"
    onPremisesSecurityIdentifier = "string"
    onPremisesSyncEnabled = bool
    preferredDataLocation = "string"
    preferredLanguage = "string"
    proxyAddresses = [
      "string"
    ]
    renewedDateTime = "string"
    securityEnabled = bool
    securityIdentifier = "string"
    serviceProvisioningErrors = [
      {
        createdDateTime = "string"
        isResolved = bool
        serviceInstance = "string"
      }
    ]
    theme = "string"
    uniqueName = "string"
    unseenCount = int
    visibility = "string"
  }
}
```

## Property values

### groups

| Name | Description | Value |
| --- | --- | --- |
| allowExternalSenders | Indicates if people external to the organization can send messages to the group. The default value is false. Supported only on the Get group API \(GET /groups/{ID}\). | bool |
| apiVersion | The resource api version | 'beta' \(ReadOnly\) |
| assignedLabels | The list of sensitivity label pairs \(label ID, label name\) associated with a Microsoft 365 group. This property can be updated only in delegated scenarios where the caller requires both the Microsoft Graph permission and a supported administrator role. | [MicrosoftGraphAssignedLabel](#microsoftgraphassignedlabel)\[\] |
| assignedLicenses | The licenses that are assigned to the group. | [MicrosoftGraphAssignedLicense](#microsoftgraphassignedlicense)\[\] |
| autoSubscribeNewMembers | Indicates if new members added to the group are autosubscribed to receive email notifications. You can set this property in a PATCH request for the group; don't set it in the initial POST request that creates the group. Default value is false. Supported only on the Get group API \(GET /groups/{ID}\). | bool |
| classification | Describes a classification for the group \(such as low, medium, or high business impact\). | string |
| createdDateTime | Timestamp of when the group was created. The value can't be modified and is automatically populated when the group is created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on January 1, 2014 is 2014-01-01T00:00:00Z. Read-only. | string |
| deletedDateTime | Date and time when this object was deleted. Always null when the object hasn't been deleted. | string |
| description | An optional description for the group. | string |
| displayName | The display name for the group. This property is required when a group is created and can't be cleared during updates. Maximum length is 256 characters. | string |
| expirationDateTime | Timestamp of when the group is set to expire. It's null for security groups, but for Microsoft 365 groups, it represents when the group is set to expire as defined in the groupLifecyclePolicy. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on January 1, 2014 is 2014-01-01T00:00:00Z. Read-only. | string |
| groupTypes | Specifies the group type and its membership. If the collection contains Unified, the group is a Microsoft 365 group; otherwise, it's either a security group or a distribution group. For details, see groups overview.If the collection includes DynamicMembership, the group has dynamic membership; otherwise, membership is static. | string\[\] |
| hasMembersWithLicenseErrors | Indicates whether there are members in this group that have license errors from its group-based license assignment. This property is never returned on a GET operation. See an example. | bool |
| hideFromAddressLists | True if the group isn't displayed in certain parts of the Outlook UI: the Address Book, address lists for selecting message recipients, and the Browse Groups dialog for searching groups; otherwise, false. The default value is false. Supported only on the Get group API \(GET /groups/{ID}\). | bool |
| hideFromOutlookClients | True if the group isn't displayed in Outlook clients, such as Outlook for Windows and Outlook on the web; otherwise, false. The default value is false. Supported only on the Get group API \(GET /groups/{ID}\). | bool |
| id | The unique identifier for an entity. Read-only. | string |
| isArchived | When a group is associated with a team, this property determines whether the team is in read-only mode.To read this property, use the /group/{groupId}/team endpoint or the Get team API. To update this property, use the archiveTeam and unarchiveTeam APIs. | bool |
| isAssignableToRole | Indicates whether this group can be assigned to a Microsoft Entra role. Optional. This property can only be set while creating the group and is immutable. If set to true, the securityEnabled property must also be set to true, visibility must be Hidden, and the group can't be a dynamic group \(that is, groupTypes can't contain DynamicMembership\). Only callers with at least the Privileged Role Administrator role can set this property. The caller must also be assigned the RoleManagement.ReadWrite.Directory permission to set this property or update the membership of such groups. For more, see Using a group to manage Microsoft Entra role assignmentsUsing this feature requires a Microsoft Entra ID P1 license. | bool |
| isManagementRestricted |  | bool |
| isSubscribedByMail | Indicates whether the signed-in user is subscribed to receive email conversations. The default value is true. Supported only on the Get group API \(GET /groups/{ID}\). | bool |
| licenseProcessingState | Indicates the status of the group license assignment to all group members. The default value is false. Read-only. Read-only. | [MicrosoftGraphLicenseProcessingState](#microsoftgraphlicenseprocessingstate) |
| mail | The SMTP address for the group, for example, 'serviceadmins@contoso.com'. Read-only. | string |
| mailEnabled | Specifies whether the group is mail-enabled. Required. | bool |
| mailNickname | The mail alias for the group, unique for Microsoft 365 groups in the organization. Maximum length is 64 characters. This property can contain only characters in the ASCII character set 0 - 127 except the following characters: @ \(\) / \[\] ' ; : <> , SPACE. Required. | string |
| membershipRule | The rule that determines members for this group if the group is a dynamic group \(groupTypes contains DynamicMembership\). For more information about the syntax of the membership rule, see Membership Rules syntax. | string |
| membershipRuleProcessingState | Indicates whether the dynamic membership processing is on or paused. Possible values are On or Paused. | string |
| onPremisesDomainName | Contains the on-premises domain FQDN, also called dnsDomainName synchronized from the on-premises directory. Read-only. | string |
| onPremisesLastSyncDateTime | Indicates the last time at which the group was synced with the on-premises directory. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on January 1, 2014 is 2014-01-01T00:00:00Z. Read-only. | string |
| onPremisesNetBiosName | Contains the on-premises netBios name synchronized from the on-premises directory. Read-only. | string |
| onPremisesProvisioningErrors | Errors when using Microsoft synchronization product during provisioning. | [MicrosoftGraphOnPremisesProvisioningError](#microsoftgraphonpremisesprovisioningerror)\[\] |
| onPremisesSamAccountName | Contains the on-premises SAM account name synchronized from the on-premises directory. Read-only. | string |
| onPremisesSecurityIdentifier | Contains the on-premises security identifier \(SID\) for the group synchronized from on-premises to the cloud. Read-only. | string |
| onPremisesSyncEnabled | true if this group is synced from an on-premises directory; false if this group was originally synced from an on-premises directory but is no longer synced; null if this object has never synced from an on-premises directory \(default\). Read-only. | bool |
| preferredDataLocation | The preferred data location for the Microsoft 365 group. By default, the group inherits the group creator's preferred data location. To set this property, the calling app must be granted the Directory.ReadWrite.All permission and the user be assigned at least one of the following Microsoft Entra roles: User Account Administrator Directory Writer Exchange Administrator SharePoint Administrator For more information about this property, see OneDrive Online Multi-Geo. Nullable. | string |
| preferredLanguage | The preferred language for a Microsoft 365 group. Should follow ISO 639-1 Code; for example, en-US. | string |
| proxyAddresses | Email addresses for the group that direct to the same group mailbox. For example: \['SMTP: bob@contoso.com', 'smtp: bob@sales.contoso.com'\]. The any operator is required to filter expressions on multi-valued properties. Read-only. Not nullable. | string\[\] |
| renewedDateTime | Timestamp of when the group was last renewed. This value can't be modified directly and is only updated via the renew service action. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on January 1, 2014 is 2014-01-01T00:00:00Z. Read-only. | string |
| securityEnabled | Specifies whether the group is a security group. Required. | bool |
| securityIdentifier | Security identifier of the group, used in Windows scenarios. Read-only. | string |
| serviceProvisioningErrors | Errors published by a federated service describing a nontransient, service-specific error regarding the properties or link from a group object. | [MicrosoftGraphServiceProvisioningError](#microsoftgraphserviceprovisioningerror)\[\] |
| theme | Specifies a Microsoft 365 group's color theme. Possible values are Teal, Purple, Green, Blue, Pink, Orange, or Red. | string |
| type | The resource type | 'Microsoft.Graph/groups' \(ReadOnly\) |
| uniqueName | The unique identifier that can be assigned to a group and used as an alternate key. Immutable. | string \(Required\) |
| unseenCount | Count of conversations that received new posts since the signed-in user last visited the group. Supported only on the Get group API \(GET /groups/{ID}\). | int |
| visibility | Specifies the group join policy and group content visibility for groups. Possible values are: Private, Public, or HiddenMembership. HiddenMembership can be set only for Microsoft 365 groups when the groups are created. It can't be updated later. Other values of visibility can be updated after group creation. If visibility value isn't specified during group creation on Microsoft Graph, a security group is created as Private by default, and the Microsoft 365 group is Public. Groups assignable to roles are always Private. To learn more, see group visibility options. Nullable. | string |

### MicrosoftGraphAssignedLabel

| Name | Description | Value |
| --- | --- | --- |
| displayName | The display name of the label. Read-only. | string |
| labelId | The unique identifier of the label. | string |

### MicrosoftGraphAssignedLicense

| Name | Description | Value |
| --- | --- | --- |
| disabledPlans | A collection of the unique identifiers for plans that have been disabled. IDs are available in servicePlans > servicePlanId in the tenant's subscribedSkus or serviceStatus > servicePlanId in the tenant's companySubscription. | string  <br>  <br>Constraints:  <br>Min length = 36  <br>Max length = 36  <br>Pattern = `^[0-9a-fA-F]{8}-([0-9a-fA-F]{4}-){3}[0-9a-fA-F]{12}$`  <br> |
| skuId | The unique identifier for the SKU. Corresponds to the skuId from subscribedSkus or companySubscription. | string  <br>  <br>Constraints:  <br>Min length = 36  <br>Max length = 36  <br>Pattern = `^[0-9a-fA-F]{8}-([0-9a-fA-F]{4}-){3}[0-9a-fA-F]{12}$`  <br> |

### MicrosoftGraphLicenseProcessingState

| Name | Description | Value |
| --- | --- | --- |
| state |  | string |

### MicrosoftGraphOnPremisesProvisioningError

| Name | Description | Value |
| --- | --- | --- |
| category | Category of the provisioning error. Note: Currently, there is only one possible value. Possible value: PropertyConflict - indicates a property value is not unique. Other objects contain the same value for the property. | string |
| occurredDateTime | The date and time at which the error occurred. | string |
| propertyCausingError | Name of the directory property causing the error. Current possible values: UserPrincipalName or ProxyAddress. | string |
| value | Value of the property causing the error. | string |

### MicrosoftGraphServiceProvisioningError

| Name | Description | Value |
| --- | --- | --- |
| createdDateTime | The date and time at which the error occurred. | string |
| isResolved | Indicates whether the error has been attended to. | bool |
| serviceInstance | Qualified service instance \(for example, 'SharePoint/Dublin'\) that published the service error information. | string |
