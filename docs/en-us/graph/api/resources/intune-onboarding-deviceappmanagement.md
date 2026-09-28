<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceappmanagement?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceAppManagement resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Singleton entity that acts as a container for all device app management functionality.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-deviceappmanagement-get?view=graph-rest-1.0) | [deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceappmanagement?view=graph-rest-1.0) | Read properties and relationships of the [deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceappmanagement?view=graph-rest-1.0) object. |
| [Update deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-deviceappmanagement-update?view=graph-rest-1.0) | [deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceappmanagement?view=graph-rest-1.0) | Update the properties of a [deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceappmanagement?view=graph-rest-1.0) object. |
| [syncMicrosoftStoreForBusinessApps action](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-deviceappmanagement-syncmicrosoftstoreforbusinessapps?view=graph-rest-1.0) | None | Syncs Intune account with Microsoft Store For Business |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String |  |
| microsoftStoreForBusinessLastSuccessfulSyncDateTime | DateTimeOffset | The last time the apps from the Microsoft Store for Business were synced successfully for the account. |
| isEnabledForMicrosoftStoreForBusiness | Boolean | Whether the account is enabled for syncing applications from the Microsoft Store for Business. |
| microsoftStoreForBusinessLanguage | String | The locale information used to sync applications from the Microsoft Store for Business. Cultures that are specific to a country/region. The names of these cultures follow RFC 4646 \(Windows Vista and later\). The format is <languagecode2>-<country/regioncode2>, where <languagecode2> is a lowercase two-letter code derived from ISO 639-1 and <country/regioncode2> is an uppercase two-letter code derived from ISO 3166. For example, en-US for English \(United States\) is a specific culture. |
| microsoftStoreForBusinessLastCompletedApplicationSyncTime | DateTimeOffset | The last time an application sync from the Microsoft Store for Business was completed. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| vppTokens | [vppToken](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptoken?view=graph-rest-1.0) collection | List of Vpp tokens for this organization. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceAppManagement",
  "id": "String (identifier)",
  "microsoftStoreForBusinessLastSuccessfulSyncDateTime": "String (timestamp)",
  "isEnabledForMicrosoftStoreForBusiness": true,
  "microsoftStoreForBusinessLanguage": "String",
  "microsoftStoreForBusinessLastCompletedApplicationSyncTime": "String (timestamp)"
}
```
