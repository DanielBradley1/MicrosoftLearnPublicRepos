<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/userregistrationmethodcount?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# userRegistrationMethodCount resource type

Namespace: microsoft.graph

Represents the number of users registered for an authentication method.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationMethod | String | Name of the authentication method. |
| userCount | Int64 | Number of users registered. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userRegistrationMethodCount",
  "authenticationMethod": "String",
  "userCount": "Int64"
}
```
