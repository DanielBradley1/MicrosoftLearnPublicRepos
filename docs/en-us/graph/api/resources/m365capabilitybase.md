<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/m365capabilitybase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-09 -->

# m365CapabilityBase resource type

Namespace: microsoft.graph

Represents an abstract base type for cross-tenant Microsoft 365 capabilities. This type can't be instantiated directly. Instances are created using specific derived types. All capability instances in a collection are differentiated by the **@odata.type** property.

The following types derive from **m365CapabilityBase**:

- [anonymousCalendarSharingFreeBusyDetail](https://learn.microsoft.com/en-us/graph/api/resources/anonymouscalendarsharingfreebusydetail?view=graph-rest-1.0)
- [anonymousCalendarSharingFreeBusyReviewer](https://learn.microsoft.com/en-us/graph/api/resources/anonymouscalendarsharingfreebusyreviewer?view=graph-rest-1.0)
- [anonymousCalendarSharingFreeBusySimple](https://learn.microsoft.com/en-us/graph/api/resources/anonymouscalendarsharingfreebusysimple?view=graph-rest-1.0)
- [crossTenantCalendarAvailabilityBasic](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantcalendaravailabilitybasic?view=graph-rest-1.0)
- [crossTenantCalendarAvailabilityLimitedDetails](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantcalendaravailabilitylimiteddetails?view=graph-rest-1.0)
- [crossTenantCalendarSharingFreeBusyDetail](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantcalendarsharingfreebusydetail?view=graph-rest-1.0)
- [crossTenantCalendarSharingFreeBusyReviewer](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantcalendarsharingfreebusyreviewer?view=graph-rest-1.0)
- [crossTenantCalendarSharingFreeBusySimple](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantcalendarsharingfreebusysimple?view=graph-rest-1.0)
- [crossTenantMailTipsAll](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmailtipsall?view=graph-rest-1.0)
- [crossTenantMailTipsLimited](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmailtipslimited?view=graph-rest-1.0)
- [crossTenantMigration](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigration?view=graph-rest-1.0)
- [crossTenantOpenProfileCard](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantopenprofilecard?view=graph-rest-1.0)
- [crossTenantPlacesDeskBooking](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantplacesdeskbooking?view=graph-rest-1.0)
- [crossTenantPlacesRoomBooking](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantplacesroombooking?view=graph-rest-1.0)

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| inboundAccess | [m365CapabilityInboundAccess](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilityinboundaccess?view=graph-rest-1.0) | The inbound access settings for the capability. |
| lastModifiedDateTime | DateTimeOffset | The automatically updated last modified timestamp for the capability. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. |
| name | String | The name or identifier of the capability. Key. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.m365CapabilityBase",
  "name": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "inboundAccess": {"@odata.type": "microsoft.graph.m365CapabilityInboundAccess"}
}
```
