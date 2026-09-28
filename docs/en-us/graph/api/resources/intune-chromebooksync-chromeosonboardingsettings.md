<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-chromebooksync-chromeosonboardingsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# chromeOSOnboardingSettings resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity that represents a Chromebook tenant settings

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List chromeOSOnboardingSettingses](https://learn.microsoft.com/en-us/graph/api/intune-chromebooksync-chromeosonboardingsettings-list?view=graph-rest-beta) | [chromeOSOnboardingSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-chromebooksync-chromeosonboardingsettings?view=graph-rest-beta) collection | List properties and relationships of the [chromeOSOnboardingSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-chromebooksync-chromeosonboardingsettings?view=graph-rest-beta) objects. |
| [Get chromeOSOnboardingSettings](https://learn.microsoft.com/en-us/graph/api/intune-chromebooksync-chromeosonboardingsettings-get?view=graph-rest-beta) | [chromeOSOnboardingSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-chromebooksync-chromeosonboardingsettings?view=graph-rest-beta) | Read properties and relationships of the [chromeOSOnboardingSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-chromebooksync-chromeosonboardingsettings?view=graph-rest-beta) object. |
| [Create chromeOSOnboardingSettings](https://learn.microsoft.com/en-us/graph/api/intune-chromebooksync-chromeosonboardingsettings-create?view=graph-rest-beta) | [chromeOSOnboardingSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-chromebooksync-chromeosonboardingsettings?view=graph-rest-beta) | Create a new [chromeOSOnboardingSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-chromebooksync-chromeosonboardingsettings?view=graph-rest-beta) object. |
| [Delete chromeOSOnboardingSettings](https://learn.microsoft.com/en-us/graph/api/intune-chromebooksync-chromeosonboardingsettings-delete?view=graph-rest-beta) | None | Deletes a [chromeOSOnboardingSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-chromebooksync-chromeosonboardingsettings?view=graph-rest-beta). |
| [Update chromeOSOnboardingSettings](https://learn.microsoft.com/en-us/graph/api/intune-chromebooksync-chromeosonboardingsettings-update?view=graph-rest-beta) | [chromeOSOnboardingSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-chromebooksync-chromeosonboardingsettings?view=graph-rest-beta) | Update the properties of a [chromeOSOnboardingSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-chromebooksync-chromeosonboardingsettings?view=graph-rest-beta) object. |
| [connect action](https://learn.microsoft.com/en-us/graph/api/intune-chromebooksync-chromeosonboardingsettings-connect?view=graph-rest-beta) | [chromeOSOnboardingStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-chromebooksync-chromeosonboardingstatus?view=graph-rest-beta) |  |
| [disconnect action](https://learn.microsoft.com/en-us/graph/api/intune-chromebooksync-chromeosonboardingsettings-disconnect?view=graph-rest-beta) | [chromeOSOnboardingStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-chromebooksync-chromeosonboardingstatus?view=graph-rest-beta) |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ChromebookTenant's Id |
| ownerUserPrincipalName | String | The ChromebookTenant's OwnerUserPrincipalName |
| onboardingStatus | [onboardingStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-chromebooksync-onboardingstatus?view=graph-rest-beta) | The ChromebookTenant's OnboardingStatus. Possible values are: `unknown`, `inprogress`, `onboarded`, `failed`, `offboarding`, `unknownFutureValue`. |
| lastModifiedDateTime | DateTimeOffset | The ChromebookTenant's LastModifiedDateTime |
| lastDirectorySyncDateTime | DateTimeOffset | The ChromebookTenant's LastDirectorySyncDateTime |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.chromeOSOnboardingSettings",
  "id": "String (identifier)",
  "ownerUserPrincipalName": "String",
  "onboardingStatus": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "lastDirectorySyncDateTime": "String (timestamp)"
}
```
