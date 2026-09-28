<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/loginpagetextvisibilitysettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-03-17 -->

# loginPageTextVisibilitySettings resource type

Namespace: microsoft.graph

Represents the various text strings that can be hidden on the sign-in page for a tenant. This resource is configured as part of the [organizationalBranding resource](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbranding?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| hideAccountResetCredentials | Boolean | Option to hide the self-service password reset \(SSPR\) hyperlinks such as "Can't access your account?", "Forgot my password" and "Reset it now" on the sign-in form. |
| hideCannotAccessYourAccount | Boolean | Option to hide the self-service password reset \(SSPR\) "Can't access your account?" hyperlink on the sign-in form. |
| hideForgotMyPassword | Boolean | Option to hide the self-service password reset \(SSPR\) "Forgot my password" hyperlink on the sign-in form. |
| hidePrivacyAndCookies | Boolean | Option to hide the "Privacy & Cookies" hyperlink in the footer. |
| hideResetItNow | Boolean | Option to hide the self-service password reset \(SSPR\) "reset it now" hyperlink on the sign-in form. |
| hideTermsOfUse | Boolean | Option to hide the "Terms of Use" hyperlink in the footer. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.loginPageTextVisibilitySettings",
  "hideAccountResetCredentials": "Boolean",
  "hideCannotAccessYourAccount": "Boolean",
  "hideForgotMyPassword": "Boolean",
  "hidePrivacyAndCookies": "Boolean",
  "hideResetItNow": "Boolean",
  "hideTermsOfUse": "Boolean"
}
```
