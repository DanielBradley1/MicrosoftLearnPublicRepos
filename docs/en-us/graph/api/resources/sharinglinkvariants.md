<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharinglinkvariants?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-04 -->

# sharingLinkVariants resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the status of potential sharing link variants. The variants generate a separate sharing link from the link that would otherwise be generated, but with identical role and scope.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| addressBarLinkPermission | sharingRole | Indicates the most permissive role with which an address bar link can be created. The possible values are: `none`, `view`, `edit`, `manageList`, `review`, `restrictedView`, `submitOnly`, `unknownFutureValue`. |
| allowEmbed | [sharingOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/sharingoperationstatus?view=graph-rest-beta) | Indicates whether a link can be embedded. |
| passwordProtected | [sharingOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/sharingoperationstatus?view=graph-rest-beta) | Indicates whether a link can be password protected, meaning that link users would need to enter a password to access the item for which the sharing link is produced. Creating a passwordProtected link for the first time requires providing a password. |
| requiresAuthentication | [sharingOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/sharingoperationstatus?view=graph-rest-beta) | Indicates whether a link requires identity authentication for recipients. Users can be verified through either an email address or identity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharingLinkVariants",
  "passwordProtected": {
    "@odata.type": "microsoft.graph.sharingOperationStatus"
  },
  "requiresAuthentication": {
    "@odata.type": "microsoft.graph.sharingOperationStatus"
  },
  "addressBarLinkPermission": "String",
  "allowEmbed": {
    "@odata.type": "microsoft.graph.sharingOperationStatus"
  }
}
```
