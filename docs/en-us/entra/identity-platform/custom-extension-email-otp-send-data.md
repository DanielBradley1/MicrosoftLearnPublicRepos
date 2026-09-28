<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-email-otp-send-data -->
<!-- Sitemap-Last-Modified: 2025-07-24 -->

# Email OTP send event reference

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

To configure a custom email provider for [email one time passcode \(OTP\) send](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-email-otp-get-started) events, you create a custom authentication extension and invoke it at specific points in the user flow. When the **emailOtpSend** event is activated, Microsoft Entra sends a one-time passcode to the specified REST API you own.

The REST API then uses your chosen email provider, such as Azure Communication Service or SendGrid to send the one-time passcode with your custom email template, from address, email subject and more. This article describes the REST API schema for the emailOtpSend event.

## Request to the external REST API

The custom authentication extension you defined in Microsoft Entra ID makes an HTTP call to your REST API with a JSON payload. The JSON payload contains the user's email address and the one-time-passcode. The request also includes authentication context attributes and information about the application the user intends to sign in.

The following HTTP request demonstrates how Microsoft Entra invokes your REST API. This HTTP request can be used to debug your REST API by simulating a request from Microsoft Entra.

```http
POST https://example.azureWebsites.net/api/functionName

Content-Type: application/json

[Request payload]
```

The following JSON document provides an example of a request payload:

```json
{
    "type": "microsoft.graph.authenticationEvent.emailOtpSend",
    "source": "/tenants/ffff5f5f-aa6a-bb7b-cc8c-dddddd9d9d9d/applications/bbbbbbbb-cccc-dddd-2222-333333333333",
    "data": {
        "@odata.type": "microsoft.graph.onOtpSendCalloutData",
        "otpContext": {
            "identifier": "someone@example.com",
            "oneTimeCode": "12345678"
        },
        "tenantId": "aaaabbbb-0000-cccc-1111-dddd2222eeee",
        "authenticationEventListenerId": "00001111-aaaa-2222-bbbb-3333cccc4444",
        "customAuthenticationExtensionId": "11112222-bbbb-3333-cccc-4444dddd5555",
        "authenticationContext": {
            "correlationId": "aaaa0000-bb11-2222-33cc-444444dddddd",
            "client": {
                "ip": "192.168.0.0",
                "locale": "en-us",
                "market": "en-us"
            },
            "protocol": "OAUTH2.0",
            "requestType": "signUp",
            "clientServicePrincipal": {
                "id": "aaaaaaaa-bbbb-cccc-1111-222222222222",
                "appId": "00001111-aaaa-2222-bbbb-3333cccc4444",
                "appDisplayName": "My Test application",
                "displayName": "My Test application"
            },
            "resourceServicePrincipal": {
                "id": "aaaaaaaa-bbbb-cccc-1111-222222222222",
                "appId": "00001111-aaaa-2222-bbbb-3333cccc4444",
                "appDisplayName": "My Test application",
                "displayName": "My Test application"
            }
        }
    }
}
```

### Response from the external REST API

Microsoft Entra ID expects a REST API response in the following HTTP.

```http
HTTP/1.1 200 OK

Content-Type: application/json

[JSON document]
```

In the HTTP response, provide the following JSON document:

```json
{
    "data": {
        "@odata.type": "microsoft.graph.OnOtpSendResponseData",
        "actions": [
            {
                "@odata.type": "microsoft.graph.OtpSend.continueWithDefaultBehavior"
            }
        ]
    }
}
```

## Next steps

Lean how to [configure a custom email provider for one time passcode send events](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-email-otp-get-started).
