<!-- Source: https://learn.microsoft.com/en-us/graph/templates/bicep/reference/groups?view=graph-bicep-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-13 -->

# Microsoft.Graph groups

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

Note

Permissions for personal Microsoft accounts cannot be used to deploy Microsoft Graph resources declared in Bicep files.

### Resource deployment

Choose the least privileged permission from the following table to create or update a Microsoft.Graph/groups resource.

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Group.ReadWrite.All | Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Group.ReadWrite.All | Directory.ReadWrite.All |

### Read existing resources only

Choose the least privileged permission from the following table to read a Microsoft.Graph/groups resource using the `existing` keyword.

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Group-NestingSupport.ReadWrite.All | Directory.Read.All, Directory.ReadWrite.All, Group-XTenantIdentitySync.Read.All, Group.ManageProtection.All, Group.Read.All, Group.ReadWrite.All, GroupMember.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Group-NestingSupport.ReadWrite.All | Directory.Read.All, Directory.ReadWrite.All, Group-XTenantIdentitySync.Read.All, Group.ManageProtection.All, Group.Read.All, Group.ReadWrite.All, GroupMember.Read.All |

## Resource format

To create a Microsoft.Graph/groups resource, add the following Bicep to your template.

```bicep
resource symbolicname 'Microsoft.Graph/groups@v1.0' = {
  classification: 'string'
  description: 'string'
  displayName: 'string'
  groupTypes: [
    'string'
  ]
  isAssignableToRole: bool
  isManagementRestricted: bool
  mailEnabled: bool
  mailNickname: 'string'
  members: {
    relationships: [
      {
        id: 'string'
      }
    ]
    relationshipSemantics: 'string'
  }
  membershipRule: 'string'
  membershipRuleProcessingState: 'string'
  owners: {
    relationships: [
      {
        id: 'string'
      }
    ]
    relationshipSemantics: 'string'
  }
  preferredDataLocation: 'string'
  preferredLanguage: 'string'
  securityEnabled: bool
  serviceProvisioningErrors: [
    {
      createdDateTime: 'string'
      isResolved: bool
      serviceInstance: 'string'
    }
  ]
  theme: 'string'
  uniqueName: 'string'
  visibility: 'string'
}
```

## Property values

### groups

| Name | Description | Value |
| --- | --- | --- |
| apiVersion | The resource api version | 'v1.0' \(ReadOnly\) |
| classification | Describes a classification for the group \(such as low, medium, or high business impact\). | string |
| createdDateTime | Timestamp of when the group was created. The value can't be modified and is automatically populated when the group is created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on January 1, 2014 is 2014-01-01T00:00:00Z. Read-only. | string \(ReadOnly\) |
| deletedDateTime | Date and time when this object was deleted. Always null when the object hasn't been deleted. | string \(ReadOnly\) |
| description | An optional description for the group. | string |
| displayName | The display name for the group. This property is required when a group is created and can't be cleared during updates. Maximum length is 256 characters. | string \(Required\) |
| expirationDateTime | Timestamp of when the group is set to expire. It's null for security groups, but for Microsoft 365 groups, it represents when the group is set to expire as defined in the groupLifecyclePolicy. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on January 1, 2014 is 2014-01-01T00:00:00Z. Read-only. | string \(ReadOnly\) |
| groupTypes | Specifies the group type and its membership. If the collection contains Unified, the group is a Microsoft 365 group; otherwise, it's either a security group or a distribution group. For details, see groups overview.If the collection includes DynamicMembership, the group has dynamic membership; otherwise, membership is static. | string\[\] |
| id | The unique identifier for an entity. Read-only. | string \(ReadOnly\) |
| isAssignableToRole | Indicates whether this group can be assigned to a Microsoft Entra role. Optional. This property can only be set while creating the group and is immutable. If set to true, the securityEnabled property must also be set to true, visibility must be Hidden, and the group can't be a dynamic group \(that is, groupTypes can't contain DynamicMembership\). Only callers with at least the Privileged Role Administrator role can set this property. The caller must also be assigned the RoleManagement.ReadWrite.Directory permission to set this property or update the membership of such groups. For more, see Using a group to manage Microsoft Entra role assignmentsUsing this feature requires a Microsoft Entra ID P1 license. | bool |
| isManagementRestricted | Indicates whether the group is a member of a restricted management administrative unit. If not set, the default value is null and the default behavior is false. Read-only. To manage a group member of a restricted management administrative unit, the administrator or calling app must be assigned a Microsoft Entra role at the scope of the restricted management administrative unit. | bool |
| mail | The SMTP address for the group, for example, 'serviceadmins@contoso.com'. Read-only. | string \(ReadOnly\) |
| mailEnabled | Specifies whether the group is mail-enabled. Required. | bool \(Required\) |
| mailNickname | The mail alias for the group, unique for Microsoft 365 groups in the organization. Maximum length is 64 characters. This property can contain only characters in the ASCII character set 0 - 127 except the following characters: @ \(\) / \[\] ' ; : <> , SPACE. Required. | string \(Required\) |
| members | The members of this group, who can be users, devices, other groups, or service principals. Supports the List members, Add member, and Remove member operations. Nullable. | [MicrosoftGraphRelationship](#microsoftgraphrelationship) |
| membershipRule | The rule that determines members for this group if the group is a dynamic group \(groupTypes contains DynamicMembership\). For more information about the syntax of the membership rule, see Membership Rules syntax. | string |
| membershipRuleProcessingState | Indicates whether the dynamic membership processing is on or paused. Possible values are On or Paused. | string |
| onPremisesDomainName | Contains the on-premises domain FQDN, also called dnsDomainName synchronized from the on-premises directory. Read-only. | string \(ReadOnly\) |
| onPremisesLastSyncDateTime | Indicates the last time at which the group was synced with the on-premises directory. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on January 1, 2014 is 2014-01-01T00:00:00Z. Read-only. | string \(ReadOnly\) |
| onPremisesNetBiosName | Contains the on-premises netBios name synchronized from the on-premises directory. Read-only. | string \(ReadOnly\) |
| onPremisesProvisioningErrors | Errors when using Microsoft synchronization product during provisioning. | [MicrosoftGraphOnPremisesProvisioningError](#microsoftgraphonpremisesprovisioningerror)\[\] \(ReadOnly\) |
| onPremisesSamAccountName | Contains the on-premises SAM account name synchronized from the on-premises directory. Read-only. | string \(ReadOnly\) |
| onPremisesSecurityIdentifier | Contains the on-premises security identifier \(SID\) for the group synchronized from on-premises to the cloud. Read-only. | string \(ReadOnly\) |
| onPremisesSyncEnabled | true if this group is synced from an on-premises directory; false if this group was originally synced from an on-premises directory but is no longer synced; null if this object has never synced from an on-premises directory \(default\). Read-only. | bool \(ReadOnly\) |
| owners | The owners of the group who can be users or service principals. Limited to 100 owners. Nullable. If this property isn't specified when creating a Microsoft 365 group the calling user \(admin or non-admin\) is automatically assigned as the group owner. A non-admin user can't explicitly add themselves to this collection when they're creating the group. For more information, see the related known issue. For security groups, the admin user isn't automatically added to this collection. For more information, see the related known issue. | [MicrosoftGraphRelationship](#microsoftgraphrelationship) |
| preferredDataLocation | The preferred data location for the Microsoft 365 group. By default, the group inherits the group creator's preferred data location. To set this property, the calling app must be granted the Directory.ReadWrite.All permission and the user be assigned at least one of the following Microsoft Entra roles: User Account Administrator Directory Writer Exchange Administrator SharePoint Administrator For more information about this property, see OneDrive Online Multi-Geo. Nullable. | string |
| preferredLanguage | The preferred language for a Microsoft 365 group. Should follow ISO 639-1 Code; for example, en-US. | string |
| proxyAddresses | Email addresses for the group that direct to the same group mailbox. For example: \['SMTP: bob@contoso.com', 'smtp: bob@sales.contoso.com'\]. The any operator is required to filter expressions on multi-valued properties. Read-only. Not nullable. | string\[\] \(ReadOnly\) |
| renewedDateTime | Timestamp of when the group was last renewed. This value can't be modified directly and is only updated via the renew service action. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on January 1, 2014 is 2014-01-01T00:00:00Z. Read-only. | string \(ReadOnly\) |
| securityEnabled | Specifies whether the group is a security group. Required. | bool \(Required\) |
| securityIdentifier | Security identifier of the group, used in Windows scenarios. Read-only. | string \(ReadOnly\) |
| serviceProvisioningErrors | Errors published by a federated service describing a nontransient, service-specific error regarding the properties or link from a group object. | [MicrosoftGraphServiceProvisioningError](#microsoftgraphserviceprovisioningerror)\[\] |
| theme | Specifies a Microsoft 365 group's color theme. Possible values are Teal, Purple, Green, Blue, Pink, Orange, or Red. | string |
| type | The resource type | 'Microsoft.Graph/groups' \(ReadOnly\) |
| uniqueName | The unique identifier that can be assigned to a group and used as an alternate key. Immutable. | string \(Required\) |
| visibility | Specifies the group join policy and group content visibility for groups. The possible values are: Private, Public, or HiddenMembership. HiddenMembership can be set only for Microsoft 365 groups when the groups are created. It can't be updated later. Other values of visibility can be updated after group creation. If visibility value isn't specified during group creation on Microsoft Graph, a security group is created as Private by default, and the Microsoft 365 group is Public. Groups assignable to roles are always Private. To learn more, see group visibility options. Nullable. | string |

### MicrosoftGraphRelationshipMember

| Name | Description | Value |
| --- | --- | --- |
| appId | The application ID of the relationship member. This field is only populated for service principal objects and will be null/undefined for other object types \(users, groups, etc.\). This is a read-only property populated by the system. | string \(ReadOnly\) |
| displayName | The display name of the relationship member. This is a read-only property populated by the system. | string \(ReadOnly\) |
| id | The unique identifier of the relationship member. | string \(Required\) |
| type | The type of the relationship member \(e.g., user, group, servicePrincipal\). This is a read-only property populated by the system. | string \(ReadOnly\) |
| uniqueName | A unique name that can be used to reference this relationship member in templates. This is a read-only property populated by the system. | string \(ReadOnly\) |
| userPrincipalName | The user principal name \(UPN\) of the relationship member. This field is only populated for user objects and will be null/undefined for other object types \(groups, service principals, etc.\). This is a read-only property populated by the system. | string \(ReadOnly\) |

### MicrosoftGraphRelationship

| Name | Description | Value |
| --- | --- | --- |
| relationships | The list of relationship members with their IDs and types. | [MicrosoftGraphRelationshipMember](#microsoftgraphrelationshipmember)\[\] \(Required\) |
| relationshipSemantics | Specifies the semantics used by the Microsoft Graph Bicep extension to process the relationships. The 'append' semantics means that the relationship items in the template are added to the existing list. The 'replace' semantics means that the relationship items in the template will replace all existing items in the Entra resource. The default value \(if not set\) is 'append' | string |

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

## Related content

- [Microsoft Graph API reference](https://learn.microsoft.com/en-us/graph/api/resources/group)
