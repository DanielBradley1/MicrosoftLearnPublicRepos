<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-devicecloudlicensing?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# deviceCloudLicensing resource type

Namespace: microsoft.graph.cloudLicensing

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the relationships of a [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-beta) to cloud licensing resources.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [microsoft.graph.cloudLicensing.assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) collection | The list of assignments that are directly assigned to this device. |
| usageRights | [microsoft.graph.cloudLicensing.usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta) collection | The rights of the device to use various services, granted by the combination of its assigned licenses. |
| waitingMembers | [microsoft.graph.cloudLicensing.waitingMember](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-waitingmember?view=graph-rest-beta) collection | List of over-assigned devices that are in the waiting room for an allotment due to license capacity limits. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudLicensing.deviceCloudLicensing"
}
```
