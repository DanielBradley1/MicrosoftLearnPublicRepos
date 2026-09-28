<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/m365capabilityresourcescope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-21 -->

# m365CapabilityResourceScope resource type

Namespace: microsoft.graph

Specifies the resource that a cross-tenant capability policy applies to. This type defines which specific user or group a policy affects. This resource is used by the **included** and **excluded** properties of the [m365CapabilityResourceScopes](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilityresourcescopes?view=graph-rest-1.0) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| resourceId | String | The ID of the resource to modify. The value is either `All`, to apply the capability to all resources of the type specified by **resourceType** \(all users or all groups\), or the GUID of a specific user or group. |
| resourceType | [m365ResourceType](#m365resourcetype-values) | The type of resource. The possible values are: `none`, `group`, `user`, `unknownFutureValue`. |

### m365ResourceType values

The following table lists the members of an [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations).

| Member | Description |
| --- | --- |
| none | Indicates that no resource type is selected. |
| group | The resource ID is a group ID. |
| user | The resource ID is a user ID. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.m365CapabilityResourceScope",
  "resourceId": "String",
  "resourceType": "String"
}
```
