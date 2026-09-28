<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/enumeratedaccountswithaccess?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# enumeratedAccountsWithAccess resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Contains information on specified external AWS accounts that have access to a storage bucket.

Inherits from [accountsWithAccess](https://learn.microsoft.com/en-us/graph/api/resources/accountswithaccess?view=graph-rest-beta).

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| accounts | [authorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta) collection | An AWS account. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.enumeratedAccountsWithAccess"
}
```
