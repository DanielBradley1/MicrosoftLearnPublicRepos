<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-comanagementeligibledevicessummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# comanagementEligibleDevicesSummary resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| comanagedCount | Int32 | Count of devices already Co-Managed |
| eligibleCount | Int32 | Count of devices fully eligible for Co-Management |
| scheduledForEnrollmentCount | Int32 | Count of devices scheduled for Co-Management enrollment. Valid values 0 to 9999999 |
| eligibleButNotAzureAdJoinedCount | Int32 | Count of devices eligible for Co-Management but not yet joined to Azure Active Directory |
| needsOsUpdateCount | Int32 | Count of devices that will be eligible for Co-Management after an OS update |
| ineligibleCount | Int32 | Count of devices ineligible for Co-Management |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.comanagementEligibleDevicesSummary",
  "comanagedCount": 1024,
  "eligibleCount": 1024,
  "scheduledForEnrollmentCount": 1024,
  "eligibleButNotAzureAdJoinedCount": 1024,
  "needsOsUpdateCount": 1024,
  "ineligibleCount": 1024
}
```
