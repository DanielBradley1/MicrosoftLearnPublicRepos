<!-- Source: https://learn.microsoft.com/en-us/graph/api/authenticationmethodsroot-usersigninsbyauthmethodsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-20 -->

# authenticationMethodsRoot: userSignInsByAuthMethodSummary

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Gets a list of the number of successful sign ins for each authentication method that is available.

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
GET /reports/authenticationMethods/userSignInsByAuthMethodSummary(period='{period}')
```

## Function parameters

In the request URL, provide the following query parameters with values.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| period | aggregationPeriod | The aggregation window to get summary for. The possible values are: `d1` \(1 day\), `d7` \(7 days\), `d30` \(30 days\). |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [userSignInUsageByAuthMethodActivity](https://learn.microsoft.com/en-us/graph/api/resources/usersigninusagebyauthmethodactivity?view=graph-rest-beta) collection in the response body.

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
GET https://graph.microsoft.com/beta/reports/authenticationMethods/userSignInsByAuthMethodSummary(period='d1')
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Reports.AuthenticationMethods.UserSignInsByAuthMethodSummaryWithPeriod("d1").GetAsUserSignInsByAuthMethodSummaryWithPeriodGetResponseAsync();
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
userSignInsByAuthMethodSummary, err := graphClient.Reports().AuthenticationMethods().UserSignInsByAuthMethodSummaryWithPeriod(&period).GetAsUserSignInsByAuthMethodSummaryWithPeriodGetResponse(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.reports().authenticationMethods().userSignInsByAuthMethodSummaryWithPeriod("d1").get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let userSignInsByAuthMethodSummary = await client.api('/reports/authenticationMethods/userSignInsByAuthMethodSummary(period='d1')')
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


$result = $graphServiceClient->reports()->authenticationMethods()->userSignInsByAuthMethodSummaryWithPeriod('d1', )->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Reports

Invoke-MgBetaSignReportAuthenticationMethod -Period $periodId 
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.reports.authentication_methods.user_sign_ins_by_auth_method_summary_with_period("d1").get()
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
      "@odata.type": "#microsoft.graph.userSignInUsageByAuthMethodActivity",
      "authenticationMethod": "password",
      "successActivityCount": 1470
    },
    {
      "@odata.type": "#microsoft.graph.userSignInUsageByAuthMethodActivity",
      "authenticationMethod": "sms",
      "successActivityCount": 0
    },
    {
      "@odata.type": "#microsoft.graph.userSignInUsageByAuthMethodActivity",
      "authenticationMethod": "smsSignIn",
      "successActivityCount": 0
    },
    {
      "@odata.type": "#microsoft.graph.userSignInUsageByAuthMethodActivity",
      "authenticationMethod": "mobilePhone",
      "successActivityCount": 0
    },
    {
      "@odata.type": "#microsoft.graph.userSignInUsageByAuthMethodActivity",
      "authenticationMethod": "alternateMobilePhone",
      "successActivityCount": 0
    },
    {
      "@odata.type": "#microsoft.graph.userSignInUsageByAuthMethodActivity",
      "authenticationMethod": "officePhone",
      "successActivityCount": 0
    },
    {
      "@odata.type": "#microsoft.graph.userSignInUsageByAuthMethodActivity",
      "authenticationMethod": "microsoftAuthenticatorPush",
      "successActivityCount": 8
    },
    {
      "@odata.type": "#microsoft.graph.userSignInUsageByAuthMethodActivity",
      "authenticationMethod": "oneTimePasscode",
      "successActivityCount": 0
    },
    {
      "@odata.type": "#microsoft.graph.userSignInUsageByAuthMethodActivity",
      "authenticationMethod": "microsoftAuthenticatorPasswordless",
      "successActivityCount": 504
    },
    {
      "@odata.type": "#microsoft.graph.userSignInUsageByAuthMethodActivity",
      "authenticationMethod": "windowsHelloForBusiness",
      "successActivityCount": 0
    },
    {
      "@odata.type": "#microsoft.graph.userSignInUsageByAuthMethodActivity",
      "authenticationMethod": "fido2SecurityKey",
      "successActivityCount": 0
    },
    {
      "@odata.type": "#microsoft.graph.userSignInUsageByAuthMethodActivity",
      "authenticationMethod": "temporaryAccessPass",
      "successActivityCount": 90
    },
    {
      "@odata.type": "#microsoft.graph.userSignInUsageByAuthMethodActivity",
      "authenticationMethod": "macOsSecureEnclaveKey",
      "successActivityCount": 0
    },
    {
      "@odata.type": "#microsoft.graph.userSignInUsageByAuthMethodActivity",
      "authenticationMethod": "passKeyDeviceBound",
      "successActivityCount": 843
    },
    {
      "@odata.type": "#microsoft.graph.userSignInUsageByAuthMethodActivity",
      "authenticationMethod": "passKeySynced",
      "successActivityCount": 0
    },
    {
      "@odata.type": "#microsoft.graph.userSignInUsageByAuthMethodActivity",
      "authenticationMethod": "externalAuthMethod",
      "successActivityCount": 0
    }
  ]
}
```
