<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcstatussummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-03 -->

# cloudPcStatusSummary resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the number of Cloud PCs for each status.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| count | Int32 | The count of Cloud PCs with this status. |
| status | [cloudPcStatus](https://learn.microsoft.com/en-us/graph/api/resources/cloudpc?view=graph-rest-beta#cloudpcstatus-values) | The status of the Cloud PC. The possible values are: `notProvisioned`, `provisioning`, `provisioned`, `inGracePeriod`, `deprovisioning`, `failed`, `provisionedWithWarnings`, `resizing`, `restoring`, `pendingProvision`, `unknownFutureValue`, `movingRegion`, `resizePendingLicense`, `modifyingSingleSignOn`, `refreshPolicyConfiguration`, `preparing`, `failoverInProgress`, `failbackInProgress`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `movingRegion`, `resizePendingLicense`, `modifyingSingleSignOn`, `refreshPolicyConfiguration`, `preparing`, `failoverInProgress`, `failbackInProgress`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcStatusSummary",
  "count": "Int32",
  "status": "String"
}
```
