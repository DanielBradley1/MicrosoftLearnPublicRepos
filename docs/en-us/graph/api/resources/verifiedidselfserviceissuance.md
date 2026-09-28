<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/verifiedidselfserviceissuance?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-04 -->

# verifiedIdSelfServiceIssuance resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains settings for self-service Verified ID issuance through the **selfServiceIssuance** property of a [verifiedIdProfile](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofile?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isEnabled | Boolean | Indicates whether self-service issuance is enabled. |
| issuanceUrl | String | The HTTPS URL where users can start self-service issuance to obtain the credential when required by the credential type. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.verifiedIdSelfServiceIssuance",
  "isEnabled": "Boolean",
  "issuanceUrl": "String"
}
```
