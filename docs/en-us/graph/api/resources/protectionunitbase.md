<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-07 -->

# protectionUnitBase resource type

Namespace: microsoft.graph

Represents a site, drive, or mailbox that's protected by a [protection policy](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-1.0). All the protection units in a protection policy have same retention period by default.

This resource is an abstract type.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/protectionunitbase-get?view=graph-rest-1.0) | [protectionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0) | Read the properties and relationships of a [protectionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0) object. |
| [Offboard](https://learn.microsoft.com/en-us/graph/api/protectionunitbase-offboard?view=graph-rest-1.0) | [protectionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0) | Offboard a [protectionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0). |
| [Cancel offboard](https://learn.microsoft.com/en-us/graph/api/protectionunitbase-canceloffboard?view=graph-rest-1.0) | [protectionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0) | Cancel the offboarding of a [protectionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of the person who created the protection unit. |
| createdDateTime | DateTimeOffset | The time of creation of the protection unit. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | Contains error details if an error occurred while creating a protection unit. |
| id | String | The unique identifier of the protection unit. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of person who last modified the protection unit. |
| lastModifiedDateTime | DateTimeOffset | Timestamp of the last modification of this protection unit. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| offboardRequestedDateTime | DateTimeOffset | The date and time when protection unit offboard was requested. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| policyId | String | The unique identifier of the protection policy based on which protection unit was created. |
| protectionSources | protectionSource | Indicates the sources by which a protection unit is currently protected. A protection unit protected by multiple sources is indicated by comma-separated values. The possible values are: `none`, `manual`, `dynamicRule`, `unknownFutureValue`. |
| status | [protectionUnitStatus](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0#protectionunitstatus-values) | The status of the protection unit. The possible values are: `protectRequested`, `protected`, `unprotectRequested`, `unprotected`, `removeRequested`, `unknownFutureValue`, `offboardRequested`, `offboarded`, `cancelOffboardRequested`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `offboardRequested`, `offboarded`, `cancelOffboardRequested`. |

### protectionUnitStatus values

| Member | Description |
| :--- | :--- |
| protectRequested | Protection of the unit was requested. Applies when a policy is activated or new units are added to an active policy. |
| protected | The protection unit is successfully enabled. |
| unprotectRequested | Disabling protection of the unit was requested. |
| unprotected | The protection unit is successfully disabled. |
| removeRequested | A request to remove the protected unit from the policy was made. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| offboardRequested | A request to offboard the protection unit. |
| offboarded | The protection unit is successfully offboarded. |
| cancelOffboardRequested | A request to cancel the offboarding of a protection unit. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.protectionUnitBase",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "error": {"@odata.type": "microsoft.graph.publicError"},
  "id": "String (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "offboardRequestedDateTime": "String (timestamp)",
  "policyId": "String",
  "protectionSources": "String",
  "status": "String"
}
```
