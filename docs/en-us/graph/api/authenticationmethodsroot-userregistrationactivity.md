<!-- Source: https://learn.microsoft.com/en-us/graph/api/authenticationmethodsroot-userregistrationactivity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-14 -->

# authenticationMethodsRoot: userRegistrationActivity

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the authentication methods and their corresponding number of successful and unsuccessful registration and reset activities as defined in the [userRegistrationActivity](https://learn.microsoft.com/en-us/graph/api/resources/userregistrationactivitysummary?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AuditLog.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Reports Reader
- Security Reader
- Security Administrator
- Global Reader

## HTTP request

```http
GET /reports/authenticationMethods/userRegistrationActivity(period='{period}')
```

## Function parameters

In the request URL, provide the following query parameters with values.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| period | aggregationPeriod | The aggregation window to get summary for. The possible values are: `d1` \(past 1 day\), `d7` \(past 7 days\), `d30` \(past 30 days\). Required |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [userRegistrationActivitySummary](https://learn.microsoft.com/en-us/graph/api/resources/userregistrationactivitysummary?view=graph-rest-beta) collection in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
GET https://graph.microsoft.com/beta/reports/authenticationMethods/userRegistrationActivity(period='d1')
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Reports.AuthenticationMethods.UserRegistrationActivityWithPeriod("d1").GetAsUserRegistrationActivityWithPeriodGetResponseAsync();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
period := "d1"
userRegistrationActivity, err := graphClient.Reports().AuthenticationMethods().UserRegistrationActivityWithPeriod(&period).GetAsUserRegistrationActivityWithPeriodGetResponse(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.reports().authenticationMethods().userRegistrationActivityWithPeriod("d1").get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let userRegistrationActivity = await client.api('/reports/authenticationMethods/userRegistrationActivity(period='d1')')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->reports()->authenticationMethods()->userRegistrationActivityWithPeriod('d1', )->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Reports

Invoke-MgBetaUserReportAuthenticationMethodRegistrationActivity -Period $periodId 
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.reports.authentication_methods.user_registration_activity_with_period("d1").get()
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "97d6cbb9-9323-4b6a-b89d-b2a60907ede4",
      "feature": "registration",
      "successfulActivityCount": 1,
      "failureActivityCount": 0,
      "authMethod": "windowsHelloForBusiness"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "8998b7bb-ece5-4255-8df9-4317c8a738b8",
      "feature": "registration",
      "successfulActivityCount": 83,
      "failureActivityCount": 214,
      "authMethod": "microsoftAuthenticatorPush"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "08a64d97-bc7f-412e-9555-bdd37d5a5718",
      "feature": "registration",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "email"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "22233ba5-c798-4580-ac6b-03011f290869",
      "feature": "registration",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "mobilePhone"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "d4794a86-5d93-4d6b-a5ba-4aa52920a97c",
      "feature": "registration",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "officePhone"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "436d1cbe-711a-4840-bef4-f4c69fa8ad74",
      "feature": "registration",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "alternateMobilePhone"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "3a7b2247-5a78-4c84-964d-2eb1d2e91aa0",
      "feature": "registration",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "securityQuestion"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "f096f3d7-aef9-4211-9e15-a30e27cbf66b",
      "feature": "registration",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "softwareOneTimePasscode"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "00ee088a-c208-4c6c-827c-6701fc761607",
      "feature": "registration",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "hardwareOneTimePasscode"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "8784730b-22ba-457c-a024-1b8361319377",
      "feature": "registration",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "fido2SecurityKey"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "aa3da958-fd4b-4a3e-b59c-48637acec161",
      "feature": "registration",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "temporaryAccessPass"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "c1926478-acad-497d-bd33-a395286486a1",
      "feature": "registration",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "microsoftAuthenticatorPasswordless"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "5b6c80a7-ada6-4f0d-8fa6-9cf9d76f2a37",
      "feature": "registration",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "macOsSecureEnclaveKey"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "520b7dff-73ca-411e-81ca-d65ac7587ba4",
      "feature": "registration",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "passKeyDeviceBound"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "983c4757-9a2d-43e9-8f24-5ee01515492d",
      "feature": "registration",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "passKeyDeviceBoundAuthenticator"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "0170d795-c5b8-4c32-b9e7-c33d17074337",
      "feature": "registration",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "passKeyDeviceBoundWindowsHello"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "aa8b0e59-2555-4b1b-a8fd-d3648620bbde",
      "feature": "registration",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "externalAuthMethod"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "93557928-5cbd-4968-8c88-de78f433080a",
      "feature": "reset",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "email"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "5570a753-6dd8-4063-b33a-3b6b0c77871f",
      "feature": "reset",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "mobilePhone"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "38a1efb3-5ab1-4f54-a0fb-9cd328525fcd",
      "feature": "reset",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "officePhone"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "0bcc380d-f6d3-418e-8743-027fee8b038e",
      "feature": "reset",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "alternateMobilePhone"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "6caf72c9-e0c9-4f79-aa4d-e8625a73cd27",
      "feature": "reset",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "securityQuestion"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "505b68c1-7db0-4eae-83a7-3e5f1f1baa30",
      "feature": "reset",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "microsoftAuthenticatorPush"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "0a597d38-3a54-4300-a3f2-e7f8357b51c6",
      "feature": "reset",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "sms"
    },
    {
      "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
      "id": "97ee074d-1a4a-4c96-b84b-edd902849062",
      "feature": "reset",
      "successfulActivityCount": 0,
      "failureActivityCount": 0,
      "authMethod": "oneTimePasscode"
    }
  ]
}
```
