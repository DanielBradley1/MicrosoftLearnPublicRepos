<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/systemcredentialpreferences?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# systemCredentialPreferences resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Dynamically detects and prompts users with their preferred multifactor authentication method from the registered methods.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| excludeTargets | [excludeTarget](https://learn.microsoft.com/en-us/graph/api/resources/excludetarget?view=graph-rest-beta) collection | Users and groups excluded from the preferred authentication method experience of the system. |
| includeTargets | [includeTarget](https://learn.microsoft.com/en-us/graph/api/resources/includetarget?view=graph-rest-beta) collection | Users and groups included in the preferred authentication method experience of the system. |
| state | advancedConfigState | Indicates whether the feature is enabled or disabled. The possible values are: `default`, `enabled`, `disabled`, `unknownFutureValue`. The `default` value is used when the configuration hasn't been explicitly set, and uses the default behavior of Microsoft Entra ID for the setting. The default value is `disabled`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.systemCredentialPreferences",
  "excludeTargets": [
    {
      "@odata.type": "microsoft.graph.excludeTarget"
    }
  ],
  "includeTargets": [
    {
      "@odata.type": "microsoft.graph.includeTarget"
    }
  ],
  "state": "String"
}
```
