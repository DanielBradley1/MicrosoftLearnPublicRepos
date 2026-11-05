<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdomainjoinplaintextuseridentity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# cloudPcDomainJoinPlainTextUserIdentity resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an Active Directory user identity whose user principal name is specified directly in a request.

Inherits from [cloudPcDomainJoinUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdomainjoinuseridentity?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| domainUserPrincipalName | String | The user principal name of an Active Directory account that has sufficient permissions to join devices to the domain. The value must be in UPN format, for example, `domainjoin@ad.contoso.com`. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcDomainJoinPlainTextUserIdentity",
  "domainUserPrincipalName": "String"
}
```
