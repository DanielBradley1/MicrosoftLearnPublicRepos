<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/microsoftapplicationdataaccesssettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# microsoftApplicationDataAccessSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents *settings* that specify access from Microsoft applications to Microsoft 365 data belonging to users in an organization. For example, given the proper authorization, whether only Microsoft 365 apps \(such as Word and Excel\) can access users' Microsoft 365 data, or whether other Microsoft apps \(such as Windows\) can access the data as well.

Examples of Microsoft 365 data in an organization include Word, Excel, and PowerPoint documents, Outlook messages, and Teams meeting recordings, for which the user in the Microsoft app has been properly authorized to access.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/organizationsettings-list-microsoftapplicationdataaccess?view=graph-rest-beta) | [microsoftApplicationDataAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/microsoftapplicationdataaccesssettings?view=graph-rest-beta) | Get the *settings* in a [microsoftApplicationDataAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/microsoftapplicationdataaccesssettings?view=graph-rest-beta) object that specify access from Microsoft applications to Microsoft 365 user data in an organization. |
| [Update](https://learn.microsoft.com/en-us/graph/api/microsoftapplicationdataaccesssettings-update?view=graph-rest-beta) | [microsoftApplicationDataAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/microsoftapplicationdataaccesssettings?view=graph-rest-beta) | Update the settings in a [microsoftApplicationDataAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/microsoftapplicationdataaccesssettings?view=graph-rest-beta) object that specify access from Microsoft applications to Microsoft 365 user data in an organization. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isEnabledForAllMicrosoftApplications | Boolean | When set to `true`, all users in the organization can access in a Microsoft app any Microsoft 365 data that the user has been authorized to access. The Microsoft app can be a Microsoft 365 app \(for example, Excel, Outlook\) or non-Microsoft 365 app \(for example, Edge\). The default is `true`.  <br>It is possible to disable this access for a subset of users in a Microsoft Entra security group, by specifying the group in the **disabledForGroup** property.  <br>When set to `false`, all users can access authorized Microsoft 365 data only in a Microsoft 365 app. |
| disabledForGroup | String | The ID of a Microsoft Entra security group for which the members are allowed to access Microsoft 365 data using only Microsoft 365 apps, but not other Microsoft apps such as Edge.  <br>This is only applicable if **isEnabledForAllMicrosoftApplications** is set to `true`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.microsoftApplicationDataAccessSettings",
  "isEnabledForAllMicrosoftApplications": "Boolean",
  "disabledForGroup": "String"
}
```
