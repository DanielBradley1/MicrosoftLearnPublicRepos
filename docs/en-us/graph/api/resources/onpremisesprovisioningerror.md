<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onpremisesprovisioningerror?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# onPremisesProvisioningError resource type

Namespace: microsoft.graph

Represents directory synchronization errors for the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0), [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) and [orgContact](https://learn.microsoft.com/en-us/graph/api/resources/orgcontact?view=graph-rest-1.0) resources when synchronizing on-premises directories to Microsoft Entra ID.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| category | String | Category of the provisioning error. Note: Currently, there is only one possible value. Possible value: *PropertyConflict* - indicates a property value is not unique. Other objects contain the same value for the property. |
| occurredDateTime | DateTimeOffset | The date and time at which the error occurred. |
| propertyCausingError | String | Name of the directory property causing the error. Current possible values: *UserPrincipalName* or *ProxyAddress* |
| value | String | Value of the property causing the error. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "category": "String",
  "occurredDateTime": "String (timestamp)",
  "propertyCausingError": "String",
  "value": "String"
}
```
