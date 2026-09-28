<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-datasharingconsent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# dataSharingConsent resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Data sharing consent information.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List dataSharingConsents](https://learn.microsoft.com/en-us/graph/api/intune-devices-datasharingconsent-list?view=graph-rest-beta) | [dataSharingConsent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-datasharingconsent?view=graph-rest-beta) collection | List properties and relationships of the [dataSharingConsent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-datasharingconsent?view=graph-rest-beta) objects. |
| [Get dataSharingConsent](https://learn.microsoft.com/en-us/graph/api/intune-devices-datasharingconsent-get?view=graph-rest-beta) | [dataSharingConsent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-datasharingconsent?view=graph-rest-beta) | Read properties and relationships of the [dataSharingConsent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-datasharingconsent?view=graph-rest-beta) object. |
| [Create dataSharingConsent](https://learn.microsoft.com/en-us/graph/api/intune-devices-datasharingconsent-create?view=graph-rest-beta) | [dataSharingConsent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-datasharingconsent?view=graph-rest-beta) | Create a new [dataSharingConsent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-datasharingconsent?view=graph-rest-beta) object. |
| [Delete dataSharingConsent](https://learn.microsoft.com/en-us/graph/api/intune-devices-datasharingconsent-delete?view=graph-rest-beta) | None | Deletes a [dataSharingConsent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-datasharingconsent?view=graph-rest-beta). |
| [Update dataSharingConsent](https://learn.microsoft.com/en-us/graph/api/intune-devices-datasharingconsent-update?view=graph-rest-beta) | [dataSharingConsent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-datasharingconsent?view=graph-rest-beta) | Update the properties of a [dataSharingConsent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-datasharingconsent?view=graph-rest-beta) object. |
| [consentToDataSharing action](https://learn.microsoft.com/en-us/graph/api/intune-devices-datasharingconsent-consenttodatasharing?view=graph-rest-beta) | [dataSharingConsent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-datasharingconsent?view=graph-rest-beta) |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The data sharing consent Id |
| serviceDisplayName | String | The display name of the service work flow |
| termsUrl | String | The TermsUrl for the data sharing consent |
| granted | Boolean | The granted state for the data sharing consent |
| grantDateTime | DateTimeOffset | The time consent was granted for this account |
| grantedByUpn | String | The Upn of the user that granted consent for this account |
| grantedByUserId | String | The UserId of the user that granted consent for this account |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.dataSharingConsent",
  "id": "String (identifier)",
  "serviceDisplayName": "String",
  "termsUrl": "String",
  "granted": true,
  "grantDateTime": "String (timestamp)",
  "grantedByUpn": "String",
  "grantedByUserId": "String"
}
```
