<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/httprequestendpoint?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# httpRequestEndpoint resource type

Namespace: microsoft.graph

Defines the HTTP endpoint that Microsoft Entra ID calls for a custom extension, such as a [roleManagementCustomCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/rolemanagementcustomcalloutextension?view=graph-rest-1.0).

Inherits from [customExtensionEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionendpointconfiguration?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| targetUrl | String | The URL of the HTTP endpoint that Microsoft Entra ID calls for the custom extension. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.httpRequestEndpoint",
  "targetUrl": "String"
}
```
