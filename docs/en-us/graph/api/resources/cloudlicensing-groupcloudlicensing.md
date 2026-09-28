<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-groupcloudlicensing?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-02-06 -->

# groupCloudLicensing resource type

Namespace: microsoft.graph.cloudLicensing

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the relationships of a [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta) to cloud licensing resources.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [microsoft.graph.cloudLicensing.assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) collection | The set of assignments that are directly assigned to this group. |
| usageRights | [microsoft.graph.cloudLicensing.usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta) collection | The rights that all direct members of the group have to use various services, granted by the combination of its assigned licenses. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudLicensing.groupCloudLicensing"
}
```
