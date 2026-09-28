<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/orgcontact?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-22 -->

# orgContact resource type

Namespace: microsoft.graph

Represents an organizational contact. Organizational contacts are managed by an organization's administrators and are different from [personal contacts](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0). Additionally, organizational contacts are either synchronized from on-premises directories or from Exchange Online, and are read-only in Microsoft Graph.

Inherits from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0).

This resource supports using [delta query](https://learn.microsoft.com/en-us/graph/delta-query-overview) to track incremental additions, deletions, and updates, by providing a [delta](https://learn.microsoft.com/en-us/graph/api/orgcontact-delta?view=graph-rest-1.0) function. This resource is an open type that allows additional properties beyond those documented here.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| **Organizational contacts** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/orgcontact-list?view=graph-rest-1.0) | [orgContact](https://learn.microsoft.com/en-us/graph/api/resources/orgcontact?view=graph-rest-1.0) | List properties of organizational contacts. |
| [Get](https://learn.microsoft.com/en-us/graph/api/orgcontact-get?view=graph-rest-1.0) | [orgContact](https://learn.microsoft.com/en-us/graph/api/resources/orgcontact?view=graph-rest-1.0) | Read properties and relationships of an organizational contact. |
| [Get delta](https://learn.microsoft.com/en-us/graph/api/orgcontact-delta?view=graph-rest-1.0) | [orgContact](https://learn.microsoft.com/en-us/graph/api/resources/orgcontact?view=graph-rest-1.0) collection | Get newly created, updated, or deleted organizational contacts without having to perform a full read of the entire collection. |
| [Get delta for directory object](https://learn.microsoft.com/en-us/graph/api/directoryobject-delta?view=graph-rest-1.0) | [direcyoryObject](https://learn.microsoft.com/en-us/graph/api/resources/orgcontact?view=graph-rest-1.0) collection | Get newly created, updated, or deleted organizational contacts via the directory object collection without having to perform a full read of the entire collection. |
| [List member of](https://learn.microsoft.com/en-us/graph/api/orgcontact-list-memberof?view=graph-rest-1.0) | String collection | Retrieve the list of groups and adminstrative units the contact is a member of. The check is transitive. |
| [List transitive members of](https://learn.microsoft.com/en-us/graph/api/orgcontact-list-transitivememberof?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | List the groups an organizational contact is a member of, including groups that the organizational contact is nested under. |
| [Check member groups](https://learn.microsoft.com/en-us/graph/api/directoryobject-checkmembergroups?view=graph-rest-1.0) | String collection | Check for membership of an organizational contact in a list of groups. The check is transitive. |
| [Get member groups](https://learn.microsoft.com/en-us/graph/api/directoryobject-getmembergroups?view=graph-rest-1.0) | String collection | Return all the groups that the organizational contact is a member of. The check is transitive. |
| [Check member objects](https://learn.microsoft.com/en-us/graph/api/directoryobject-checkmemberobjects?view=graph-rest-1.0) | String collection | Check for membership of an organizational contact in a list of groups, directory role, or administrative unit objects. |
| [Get member objects](https://learn.microsoft.com/en-us/graph/api/directoryobject-checkmemberobjects?view=graph-rest-1.0) | String collection | Return all groups, administrative units, and directory roles that the organizational contact is a member of. The check is transitive. |
| [Retry service provisioning](https://learn.microsoft.com/en-us/graph/api/orgcontact-retryserviceprovisioning?view=graph-rest-1.0) | None | Retry the orgContact service provisioning. |
| **Organizational hierarchy** |  |  |
| [Get manager](https://learn.microsoft.com/en-us/graph/api/orgcontact-get-manager?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Get the organizational contact's manager. |
| [List direct reports](https://learn.microsoft.com/en-us/graph/api/orgcontact-list-directreports?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | List the organizational contact's direct reports. |

## Properties

Important

Specific usage of `$filter` and the `$search` query parameter is supported only when you use the **ConsistencyLevel** header set to `eventual` and `$count`. For more information, see [Advanced query capabilities on directory objects](https://learn.microsoft.com/en-us/graph/aad-advanced-queries#organizational-contacts-properties).

| Property | Type | Description |
| :--- | :--- | :--- |
| addresses | [physicalOfficeAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicalofficeaddress?view=graph-rest-1.0) collection | Postal addresses for this organizational contact. For now a contact can only have one physical address. |
| companyName | String | Name of the company that this organizational contact belongs to. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`, `startsWith`, and `eq` for `null` values\). |
| department | String | The name for the department in which the contact works. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`, `startsWith`, and `eq` for `null` values\). |
| displayName | String | Display name for this organizational contact. Maximum length is 256 characters. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`, `startsWith`, and `eq` for `null` values\), `$search`, and `$orderby`. |
| givenName | String | First name for this organizational contact. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`, `startsWith`, and `eq` for `null` values\). |
| id | String | Unique identifier for this organizational contact. Supports `$filter` \(`eq`, `ne`, `not`, `in`\). |
| jobTitle | String | Job title for this organizational contact. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`, `startsWith`, and `eq` for `null` values\). |
| mail | String | The SMTP address for the contact, for example, "jeff@contoso.com". Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`, `startsWith`, and `eq` for `null` values\). |
| mailNickname | String | Email alias \(portion of email address pre-pending the @ symbol\) for this organizational contact. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`, `startsWith`, and `eq` for `null` values\). |
| serviceProvisioningErrors | [serviceProvisioningError](https://learn.microsoft.com/en-us/graph/api/resources/serviceprovisioningerror?view=graph-rest-1.0) collection | Errors published by a federated service describing a non-transient, service-specific error regarding the properties or link from an organizational contact object .  <br>  <br>Supports `$filter` \(`eq`, `not`, for isResolved and serviceInstance\). |
| onPremisesLastSyncDateTime | DateTimeOffset | Date and time when this organizational contact was last synchronized from on-premises AD. This date and time information uses ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`\). |
| onPremisesProvisioningErrors | [onPremisesProvisioningError](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesprovisioningerror?view=graph-rest-1.0) collection | List of any synchronization provisioning errors for this organizational contact. Supports `$filter` \(`eq`, `not` for **category** and **propertyCausingError**\), `/$count eq 0`, `/$count ne 0`. |
| onPremisesSyncEnabled | Boolean | `true` if this object is synced from an on-premises directory; `false` if this object was originally synced from an on-premises directory but is no longer synced and now mastered in Exchange; `null` if this object has never been synced from an on-premises directory \(default\).  <br>  <br>Supports `$filter` \(`eq`, `ne`, `not`, `in`, and `eq` for `null` values\). |
| phones | [phone](https://learn.microsoft.com/en-us/graph/api/resources/phone?view=graph-rest-1.0) collection | List of phones for this organizational contact. Phone types can be mobile, business, and businessFax. Only one of each type can ever be present in the collection. |
| proxyAddresses | String collection | For example: "SMTP: bob@contoso.com", "smtp: bob@sales.contoso.com". The **any** operator is required for filter expressions on multi-valued properties. Supports `$filter` \(`eq`, `not`, `ge`, `le`, `startsWith`, `/$count eq 0`, `/$count ne 0`\). |
| surname | String | Last name for this organizational contact. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`, `startsWith`, and `eq` for `null` values\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| directReports | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The contact's direct reports. \(The users and contacts that have their manager property set to this contact.\) Read-only. Nullable. Supports `$expand`. |
| manager | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The user or contact that is this contact's manager. Read-only. Supports `$expand` and `$filter` \(`eq`\) by **id**. |
| memberOf | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Groups that this contact is a member of. Read-only. Nullable. Supports `$expand`. |
| transitiveMemberOf | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Groups that this contact is a member of, including groups that the contact is nested under. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "addresses": [{"@odata.type": "microsoft.graph.physicalOfficeAddress"}],
  "companyName": "string",
  "department": "string",
  "displayName": "string",
  "givenName": "string",
  "id": "string (identifier)",
  "jobTitle": "string",
  "mail": "string",
  "mailNickname": "string",
  "onPremisesLastSyncDateTime": "string (timestamp)",
  "onPremisesProvisioningErrors": [{"@odata.type": "microsoft.graph.onPremisesProvisioningError"}],
  "onPremisesSyncEnabled": true,
  "phones": [{"@odata.type": "microsoft.graph.phone"}],
  "proxyAddresses": ["string"],
  "serviceProvisioningErrors": [
    { "@odata.type": "microsoft.graph.serviceProvisioningXmlError" }
  ],
  "surname": "string"
}
```
