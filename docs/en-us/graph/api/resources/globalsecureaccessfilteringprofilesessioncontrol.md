<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/globalsecureaccessfilteringprofilesessioncontrol?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-04-04 -->

# globalSecureAccessFilteringProfileSessionControl resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Session control to link to a Global Secure Access security profile or filtering profile. Inherits from [conditionalAccessSessionControl](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesssessioncontrol?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isEnabled | Boolean | Specifies whether the session control is enabled. Inherited from [conditionalAccessSessionControl](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesssessioncontrol?view=graph-rest-beta). |
| profileId | String | Specifies the distinct identifier that is assigned to the security profile or filtering profile. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.globalSecureAccessFilteringProfileSessionControl",
  "isEnabled": "Boolean"
}
```
