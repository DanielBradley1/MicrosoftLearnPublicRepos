<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmanagedlicenseoperation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# cloudPcManagedLicenseOperation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that represents an asynchronous operation on the [cloudPcManagedLicense](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmanagedlicense?view=graph-rest-beta) collection. This complex type is used by the **operation** parameter of the [submitManagedLicenseOperation](https://learn.microsoft.com/en-us/graph/api/cloudpcmanagedlicense-submitmanagedlicenseoperation?view=graph-rest-beta) action and returned by that action and the [retrieveManagedLicenseOperation](https://learn.microsoft.com/en-us/graph/api/cloudpcmanagedlicense-retrievemanagedlicenseoperation?view=graph-rest-beta) function.

Base type of [cloudPcManagedLicenseExtendAccess](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmanagedlicenseextendaccess?view=graph-rest-beta). Use the **@odata.type** property to identify the concrete operation type in requests and responses.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the service accepts the operation. The value uses ISO 8601 format and is always in UTC. For example, `2026-10-09T09:00:00Z`. Read-only. Not nullable. |
| operationRequestId | String | The unique, service-generated identifier for the operation. The service generates this value when it accepts the operation. The value is a GUID with a maximum length of 36 characters and remains stable for the lifetime of the accepted operation. This value isn't an entity key. Use it with [retrieveManagedLicenseOperation](https://learn.microsoft.com/en-us/graph/api/cloudpcmanagedlicense-retrievemanagedlicenseoperation?view=graph-rest-beta) to retrieve the operation status and results. Read-only. Not nullable. |
| servicePlanId | String | The unique identifier of the service plan that selects the target license SKU. The maximum length is 36 characters. Required in the operation submitted to [submitManagedLicenseOperation](https://learn.microsoft.com/en-us/graph/api/cloudpcmanagedlicense-submitmanagedlicenseoperation?view=graph-rest-beta). Not nullable. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcManagedLicenseOperation",
  "createdDateTime": "String (timestamp)",
  "operationRequestId": "String",
  "servicePlanId": "String"
}
```
