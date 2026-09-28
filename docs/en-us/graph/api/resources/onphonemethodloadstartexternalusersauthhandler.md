<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onphonemethodloadstartexternalusersauthhandler?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-02-05 -->

# onPhoneMethodLoadStartExternalUsersAuthHandler resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A managed handler that defines what calling codes are enabled or disabled for telephony services in an [external identities user flow for Microsoft Entra external tenants](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-beta).

This configuration enumerates what region codes can be opted-in or out for SMS or voice MFA.

Inherits from [onPhoneMethodLoadStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/onphonemethodloadstarthandler?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| smsOptions | [phoneOptions](https://learn.microsoft.com/en-us/graph/api/resources/phoneoptions?view=graph-rest-beta) | Telephony options to enable or disable regions for SMS. |
| voiceOptions | [phoneOptions](https://learn.microsoft.com/en-us/graph/api/resources/phoneoptions?view=graph-rest-beta) | Telephony options to enable or disable regions for voice. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onPhoneMethodLoadStartExternalUsersAuthHandler",
  "smsOptions": {
    "@odata.type": "microsoft.graph.phoneOptions"
  },
  "voiceOptions": {
    "@odata.type": "microsoft.graph.phoneOptions"
  }
}
```
