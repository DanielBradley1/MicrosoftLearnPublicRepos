<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudappsecuritysessioncontrol?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# cloudAppSecuritySessionControl resource type

Namespace: microsoft.graph

Session control used to enforce cloud app security checks. Inehrits from [Conditional Access Session Control](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesssessioncontrol?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| cloudAppSecurityType | cloudAppSecuritySessionControlType | The possible values are: `mcasConfigured`, `monitorOnly`, `blockDownloads`, `unknownFutureValue`. For more information, see [Deploy Conditional Access App Control for featured apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad). |
| isEnabled | Boolean | Specifies whether the session control is enabled. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "isEnabled": true,
  "cloudAppSecurityType": "String"
}
```
