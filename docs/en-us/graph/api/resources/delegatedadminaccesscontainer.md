<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccesscontainer?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# delegatedAdminAccessContainer resource type

Namespace: microsoft.graph

An admin access container through which directory roles are assigned via an access assignment.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessContainerId | String | The identifier of the access container \(for example, a security group\). For "securityGroup" access containers, this must be a valid ID of a Microsoft Entra security group in the Microsoft partner's tenant. |
| accessContainerType | delegatedAdminAccessContainerType | The type of access container \(for example, security group\) that will be assigned one or more roles through a delegated admin relationship. The possible values are: `securityGroup`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.delegatedAdminAccessContainer",
  "accessContainerId": "String",
  "accessContainerType": "String"
}
```
