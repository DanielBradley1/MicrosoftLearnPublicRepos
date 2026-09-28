<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customappmanagementapplicationconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# customAppManagementApplicationConfiguration resource type

Namespace: microsoft.graph

Custom app management application configuration object that contains properties which can be configured to enable various restrictions specific to application objects.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identifierUris | [identifierUriConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identifieruriconfiguration?view=graph-rest-1.0) | Configuration for identifierUris restrictions. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customAppManagementApplicationConfiguration",
  "identifierUris": {
    "@odata.type": "microsoft.graph.identifierUriConfiguration"
  }
}
```
