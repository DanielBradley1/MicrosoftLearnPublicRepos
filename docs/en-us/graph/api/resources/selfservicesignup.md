<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/selfservicesignup?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-06-21 -->

# selfServiceSignUp resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Details self-service sign-up activity of Microsoft Entra External ID users on a tenant.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/auditlogroot-list-signups?view=graph-rest-beta) | [selfServiceSignUp](https://learn.microsoft.com/en-us/graph/api/resources/selfservicesignup?view=graph-rest-beta) collection | Get a list of the [selfServiceSignUp](https://learn.microsoft.com/en-us/graph/api/resources/selfservicesignup?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/selfservicesignup-get?view=graph-rest-beta) | [selfServiceSignUp](https://learn.microsoft.com/en-us/graph/api/resources/selfservicesignup?view=graph-rest-beta) | Read the properties and relationships of a [selfServiceSignUp](https://learn.microsoft.com/en-us/graph/api/resources/selfservicesignup?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appDisplayName | String | App name displayed in the Microsoft Entra admin center.  <br>  <br>Supports `$filter` \(`eq`, `startsWith`\). |
| appId | String | Unique GUID that represents the app ID in the Microsoft Entra ID.  <br>  <br>Supports `$filter` \(`eq`\). |
| appliedEventListeners | [appliedAuthenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/appliedauthenticationeventlistener?view=graph-rest-beta) collection | Detailed information about the listeners, such as Azure Logic Apps and Azure Functions, which the corresponding events in the sign-up event triggered. |
| correlationId | String | The request ID sent from the client when the sign-up is initiated. Used to troubleshoot sign-up activity.  <br>  <br>Supports `$filter` \(`eq`\). |
| createdDateTime | DateTimeOffset | Date and time \(UTC\) the sign-up was initiated. Example: midnight on Jan 1, 2014 is reported as `2014-01-01T00:00:00Z`.  <br>  <br>Supports `$orderby`, `$filter` \(`eq`, `le`, and `ge`\). |
| id | String | Unique ID representing the sign-up activity.  <br>  <br>Supports `$filter` \(`eq`\). Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| signUpIdentity | [signUpIdentity](https://learn.microsoft.com/en-us/graph/api/resources/signupidentity?view=graph-rest-beta) | Unique identifier for self-service sign-up user. Supports `$filter` \(`eq`\) on the **signUpIdentifierType**. |
| signUpIdentityProvider | String | Describes the type of account for which the user registered. Values include `Email OTP`, `Email Password`, `Google`. |
| signUpStage | signUpStage | Describes the step in the sign-up flow. The possible values are: `credentialCollection`, `credentialValidation`, `credentialFederation`, `consent`, `attributeCollectionAndValidation`, `userCreation`, `tenantConsent`, `unknownFutureValue`. |
| status | [signUpStatus](https://learn.microsoft.com/en-us/graph/api/resources/signupstatus?view=graph-rest-beta) | Sign-up status. Includes the error code and description of the error \(if a sign-up failure or interrupt occurs\).  <br>  <br>Supports `$filter` \(`eq`\) on **errorCode** property. |
| userId | String | The identifier of the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta) object created during the sign-up. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.selfServiceSignUp",
  "id": "String (identifier)",
  "appDisplayName": "String",
  "appId": "String",
  "appliedEventListeners": [
    {
      "@odata.type": "microsoft.graph.appliedAuthenticationEventListener"
    }
  ],
  "correlationId": "String",
  "createdDateTime": "String (timestamp)",
  "signUpStage": "String",
  "status": {
    "@odata.type": "microsoft.graph.signUpStatus"
  },
  "signUpIdentity": {
    "@odata.type": "microsoft.graph.signUpIdentity"
  },
  "signUpIdentityProvider": "String",
  "userId": "String"
}
```
