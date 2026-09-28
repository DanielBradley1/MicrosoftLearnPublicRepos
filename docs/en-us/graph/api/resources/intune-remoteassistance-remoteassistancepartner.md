<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancepartner?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# remoteAssistancePartner resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

RemoteAssistPartner resources represent the metadata and status of a given Remote Assistance partner service.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List remoteAssistancePartners](https://learn.microsoft.com/en-us/graph/api/intune-remoteassistance-remoteassistancepartner-list?view=graph-rest-1.0) | [remoteAssistancePartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancepartner?view=graph-rest-1.0) collection | List properties and relationships of the [remoteAssistancePartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancepartner?view=graph-rest-1.0) objects. |
| [Get remoteAssistancePartner](https://learn.microsoft.com/en-us/graph/api/intune-remoteassistance-remoteassistancepartner-get?view=graph-rest-1.0) | [remoteAssistancePartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancepartner?view=graph-rest-1.0) | Read properties and relationships of the [remoteAssistancePartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancepartner?view=graph-rest-1.0) object. |
| [Create remoteAssistancePartner](https://learn.microsoft.com/en-us/graph/api/intune-remoteassistance-remoteassistancepartner-create?view=graph-rest-1.0) | [remoteAssistancePartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancepartner?view=graph-rest-1.0) | Create a new [remoteAssistancePartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancepartner?view=graph-rest-1.0) object. |
| [Delete remoteAssistancePartner](https://learn.microsoft.com/en-us/graph/api/intune-remoteassistance-remoteassistancepartner-delete?view=graph-rest-1.0) | None | Deletes a [remoteAssistancePartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancepartner?view=graph-rest-1.0). |
| [Update remoteAssistancePartner](https://learn.microsoft.com/en-us/graph/api/intune-remoteassistance-remoteassistancepartner-update?view=graph-rest-1.0) | [remoteAssistancePartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancepartner?view=graph-rest-1.0) | Update the properties of a [remoteAssistancePartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancepartner?view=graph-rest-1.0) object. |
| [beginOnboarding action](https://learn.microsoft.com/en-us/graph/api/intune-remoteassistance-remoteassistancepartner-beginonboarding?view=graph-rest-1.0) | None | A request to start onboarding. Must be coupled with the appropriate TeamViewer account information |
| [disconnect action](https://learn.microsoft.com/en-us/graph/api/intune-remoteassistance-remoteassistancepartner-disconnect?view=graph-rest-1.0) | None | A request to remove the active TeamViewer connector |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the partner. |
| displayName | String | Display name of the partner. |
| onboardingUrl | String | URL of the partner's onboarding portal, where an administrator can configure their Remote Assistance service. |
| onboardingStatus | [remoteAssistanceOnboardingStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistanceonboardingstatus?view=graph-rest-1.0) | A friendly description of the current TeamViewer connector status. The possible values are: `notOnboarded`, `onboarding`, `onboarded`. |
| lastConnectionDateTime | DateTimeOffset | Timestamp of the last request sent to Intune by the TEM partner. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.remoteAssistancePartner",
  "id": "String (identifier)",
  "displayName": "String",
  "onboardingUrl": "String",
  "onboardingStatus": "String",
  "lastConnectionDateTime": "String (timestamp)"
}
```
