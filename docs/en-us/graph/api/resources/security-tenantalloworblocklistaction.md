<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-tenantalloworblocklistaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# tenantAllowOrBlockListAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the tenant allow-or-block list action. When an admin creates an email threat submission, a tenant allow-or-block list operation can also be provided. When a tenant allow-or-block list operation is provided, the threat submission will automatically add related items \(URLs, attachments, senders\) to the tenant allow-or-block list.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | tenantAllowBlockListAction | Specifies whether the tenant allow-or-block list is an allow or block. The possible values are: `allow`, `block`, and `unkownFutureValue`. |
| expirationDateTime | DateTimeOffset | Specifies when the tenant allow-block-list expires in date time. |
| note | String | Specifies the note added to the tenant allow-or-block list entry in the format of string. |
| results | Collection\([security.tenantAllowBlockListEntryResult](https://learn.microsoft.com/en-us/graph/api/resources/security-tenantallowblocklistentryresult?view=graph-rest-beta)\) | Contains the result of the submission that lead to the tenant allow-block-list entry creation. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.tenantAllowOrBlockListAction",
  "action": "String",
  "results": [
    {
      "@odata.type": "microsoft.graph.security.tenantAllowBlockListEntryResult"
    }
  ],
  "expirationDateTime": "String (timestamp)",
  "note": "String"
}
```
