<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/auditactivityinitiator?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# auditActivityInitiator resource type

Namespace: microsoft.graph

Identity the resource object that initiates the activity. The initiator can be a user, an app, or a system \(which is considered an app\). For more information, see [Linkable identifiers in Microsoft Entra](https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-authentication-track-linkable-identifiers). This object is configured in the **initiatedBy** property of [directoryAudit](https://learn.microsoft.com/en-us/graph/api/resources/directoryaudit?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| app | [appIdentity](https://learn.microsoft.com/en-us/graph/api/resources/appidentity?view=graph-rest-1.0) | If the resource initiating the activity is an app, this property indicates all the app related information like **appId** and name. |
| user | [userIdentity](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-1.0) | If the resource initiating the activity is a user, this property Indicates all the user related information like user ID and **userPrincipalName**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "app": {"@odata.type": "microsoft.graph.appIdentity"},
  "user": {"@odata.type": "microsoft.graph.userIdentity"}
}
```
