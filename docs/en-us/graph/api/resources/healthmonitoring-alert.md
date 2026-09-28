<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alert?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-20 -->

# alert resource type

Namespace: microsoft.graph.healthMonitoring

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a system-detected health monitoring alert associated with common Microsoft Entra authentication and access management scenarios. Anomaly detection catches unusual patterns in health metrics data streams, for example, unusually high MFA sign-in failures, and surfaces these patterns in the form of alerts in Microsoft Entra Health monitoring.

This resource supports subscribing to [change notifications](https://learn.microsoft.com/en-us/graph/change-notifications-overview).

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/healthmonitoring-healthmonitoringroot-list-alerts?view=graph-rest-beta) | [microsoft.graph.healthMonitoring.alert](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alert?view=graph-rest-beta) collection | Get a list of the [microsoft.graph.healthMonitoring.alert](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alert?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/healthmonitoring-alert-get?view=graph-rest-beta) | [microsoft.graph.healthMonitoring.alert](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alert?view=graph-rest-beta) | Read the properties and relationships of a [microsoft.graph.healthMonitoring.alert](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alert?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/healthmonitoring-alert-update?view=graph-rest-beta) | [microsoft.graph.healthMonitoring.alert](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alert?view=graph-rest-beta) | Update the properties of a [microsoft.graph.healthMonitoring.alert](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alert?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| alertType | microsoft.graph.healthMonitoring.alertType | Indicates the type of alert. The possible values are: `unknown`, `mfaSignInFailure`, `managedDeviceSignInFailure`, `compliantDeviceSignInFailure`, `unknownFutureValue`, `conditionalAccessBlockedSignIn`, `samlSignInFailure`, `internetAppBlockedByPolicy`, `privateAppBlockedByConnector`, `remoteNetworkTunnelConnectivity`, `remoteNetworkBgpConnectivity`. Use the `Prefer: include-unknown-enum-members` request header to get the following value or values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `conditionalAccessBlockedSignIn`, `samlSignInFailure`, `internetAppBlockedByPolicy`, `privateAppBlockedByConnector`, `remoteNetworkTunnelConnectivity`, `remoteNetworkBgpConnectivity`. Supports `$filter` \(`eq`\). |
| category | microsoft.graph.healthMonitoring.category | The classification that groups the scenario. The possible values are: `unknown`, `authentication`, `unknownFutureValue`. |
| createdDateTime | DateTimeOffset | The time when Microsoft Entra Health monitoring generated the alert. Supports `$orderby`. |
| documentation | [microsoft.graph.healthMonitoring.documentation](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-documentation?view=graph-rest-beta) | A key-value pair that contains the name of and link to the documentation to aid in investigation of the alert. |
| enrichment | [microsoft.graph.healthMonitoring.enrichment](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-enrichment?view=graph-rest-beta) | Investigative information on the alert. This information typically includes counts of impacted objects, which include directory objects such as users, groups, and devices, and a pointer to supporting data. |
| id | String | The unique GUID identifier of this alert in the associated tenant. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| scenario | microsoft.graph.healthMonitoring.scenario | The area being monitored on the system that is emitting the source signals. The possible values are: `unknown`, `mfa`, `devices`, `unknownFutureValue`, `conditionalAccess`, `saml`, `gsa`. Use the `Prefer: include-unknown-enum-members` request header to get the following value or values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `conditionalAccess`, `saml`, `gsa`. |
| signals | [microsoft.graph.healthMonitoring.signals](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-signals?view=graph-rest-beta) | The collection of signals that were used in the generation of the alert. These signals are sourced from [serviceActivity APIs](https://learn.microsoft.com/en-us/graph/api/resources/serviceactivity?view=graph-rest-beta) and are added to the alert as key-value pairs. |
| state | microsoft.graph.healthMonitoring.alertState | The current lifecycle state of the alert. The possible values are: `active`, `resolved`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.healthMonitoring.alert",
  "id": "String (identifier)",
  "alertType": "String",
  "scenario": "String",
  "category": "String",
  "createdDateTime": "String (timestamp)",
  "state": "String",
  "enrichment": {
    "@odata.type": "microsoft.graph.healthMonitoring.enrichment"
  },
  "signals": {
    "@odata.type": "microsoft.graph.healthMonitoring.signals"
  },
  "documentation": {
    "@odata.type": "microsoft.graph.healthMonitoring.documentation"
  }
}
```
