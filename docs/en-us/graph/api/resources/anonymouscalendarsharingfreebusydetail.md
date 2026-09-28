<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/anonymouscalendarsharingfreebusydetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-09 -->

# anonymousCalendarSharingFreeBusyDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents authorization for anonymous external users to view detailed calendar free/busy information, including meeting subject and location.

Inherits from [m365CapabilityBase](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilitybase?view=graph-rest-beta).

## Methods

This resource is part of a polymorphic collection managed by the [m365CapabilityBase](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilitybase?view=graph-rest-beta) base type. Operations are performed through the base type endpoints on the [crossTenantAccessPolicyConfigurationDefault](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationdefault?view=graph-rest-beta) or [crossTenantAccessPolicyConfigurationPartner](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationpartner?view=graph-rest-beta) resources.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| inboundAccess | [m365CapabilityInboundAccess](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilityinboundaccess?view=graph-rest-beta) | The inbound access settings for the capability. Inherited from [m365CapabilityBase](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilitybase?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The automatically updated last modified timestamp for the capability. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. Inherited from [m365CapabilityBase](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilitybase?view=graph-rest-beta). |
| name | String | The name or identifier of the capability. Inherited from [m365CapabilityBase](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilitybase?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.anonymousCalendarSharingFreeBusyDetail",
  "name": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "inboundAccess": {"@odata.type": "microsoft.graph.m365CapabilityInboundAccess"}
}
```
