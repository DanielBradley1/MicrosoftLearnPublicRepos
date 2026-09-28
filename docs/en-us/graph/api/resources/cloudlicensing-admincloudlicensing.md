<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-admincloudlicensing?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-02-06 -->

# adminCloudLicensing resource type

Namespace: microsoft.graph.cloudLicensing

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the root of the cloud licensing API for the entire organization.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List allotments](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-admincloudlicensing-list-allotments?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.allotment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-allotment?view=graph-rest-beta) collection | Get a list of the [allotment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-allotment?view=graph-rest-beta) objects and their properties. |
| [List assignmentErrors](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-admincloudlicensing-list-assignmenterrors?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.assignmentError](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignmenterror?view=graph-rest-beta) collection | Get a list of the [assignmentError](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignmenterror?view=graph-rest-beta) objects within an organization or affecting a specific user. |
| [List assignments](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-admincloudlicensing-list-assignments?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) collection | Get a list of license [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) objects within an organization. |
| [Create assignment](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-admincloudlicensing-post-assignments?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) | Create a new license [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) by posting to the **assignments** collection of an organization. |

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| allotments | [microsoft.graph.cloudLicensing.allotment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-allotment?view=graph-rest-beta) collection | The set of all allotments within the organization. Read-only. |
| assignmentErrors | [microsoft.graph.cloudLicensing.assignmentError](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignmenterror?view=graph-rest-beta) collection | The set of all asynchronous allotment assignment errors that affect the organization. Read-only. |
| assignments | [microsoft.graph.cloudLicensing.assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) collection | The set of all license assignments within the organization. Not nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudLicensing.adminCloudLicensing"
}
```
