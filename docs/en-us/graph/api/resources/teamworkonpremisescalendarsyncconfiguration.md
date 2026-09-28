<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkonpremisescalendarsyncconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamworkOnPremisesCalendarSyncConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details about the account used to sync calendars in the Microsoft Teams client of a Microsoft Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| domain | String | The fully qualified domain name \(FQDN\) of the Skype for Business Server. Use the Exchange domain if the Skype for Business SIP domain is different from the Exchange domain of the user. |
| domainUserName | String | The domain and username of the console device, for example, `Seattle\\RanierConf`. |
| smtpAddress | String | The Simple Mail Transfer Protocol \(SMTP\) address of the user account. This is only required if a different user principal name \(UPN\) is used to sign in to Exchange other than Microsoft Teams and Skype for Business. This is a common scenario in a hybrid environment where an on-premises Exchange server is used. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkOnPremisesCalendarSyncConfiguration",
  "domain": "String",
  "domainUserName": "String",
  "smtpAddress": "String"
}
```
