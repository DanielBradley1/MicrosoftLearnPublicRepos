<!-- Source: https://learn.microsoft.com/en-us/graph/api/auditlogroot-list-signups?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-06-27 -->

# List signUps

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Retrieve the Microsoft Entra External ID user [selfServiceSignUps](https://learn.microsoft.com/en-us/graph/api/resources/selfservicesignup?view=graph-rest-beta) events for your tenant.

The maximum and default page size is 1,000 objects and by default, the most recent sign-ups are returned first. Only sign-up events that occurred within the Microsoft Entra ID [default retention period](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/reference-reports-data-retention#how-long-does-microsoft-entra-id-store-the-data) are available.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AuditLog.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AuditLog.Read.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Reader
- Reports Reader
- Security Administrator
- Security Operator
- Security Reader

## HTTP request

```http
GET /auditLogs/signUps
```

## Optional query parameters

This method supports the `$top`, `$skiptoken`, and `$filter` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

To avoid having the request time out, apply the `$filter` parameter with a time range for which to get all sign-ins, as shown in [Example 1](https://learn.microsoft.com/en-us/graph/api/signin-list?view=graph-rest-beta#example-1-list-all-sign-ins-during-a-specific-time-period).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [selfServiceSignUp](https://learn.microsoft.com/en-us/graph/api/resources/selfservicesignup?view=graph-rest-beta) objects in the response body. The collection of objects is listed in descending order based on **createdDateTime**.

## Examples

### Request

This example lists all sign-up events during a specific time period. Four signup events related to one sign-up attempt are returned. The response object shows the user signed up using Email OTP, and includes an interrupt involving verification of user's identity \(by entering the OTP sent to the user's email\).

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/beta/auditLogs/signUps?$filter=createdDateTime ge 2024-07-01T00:00:00Z and createdDateTime le 2024-07-14T23:59:59Z
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.AuditLogs.SignUps.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "createdDateTime ge 2024-07-01T00:00:00Z and createdDateTime le 2024-07-14T23:59:59Z";
});
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
	  graphauditlogs "github.com/microsoftgraph/msgraph-beta-sdk-go/auditlogs"
	  //other-imports
)


requestFilter := "createdDateTime ge 2024-07-01T00:00:00Z and createdDateTime le 2024-07-14T23:59:59Z"

requestParameters := &graphauditlogs.AuditLogsSignUpsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphauditlogs.AuditLogsSignUpsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
signUps, err := graphClient.AuditLogs().SignUps().Get(context.Background(), configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SelfServiceSignUpCollectionResponse result = graphClient.auditLogs().signUps().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "createdDateTime ge 2024-07-01T00:00:00Z and createdDateTime le 2024-07-14T23:59:59Z";
});
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let signUps = await client.api('/auditLogs/signUps')
	.version('beta')
	.filter('createdDateTime ge 2024-07-01T00:00:00Z and createdDateTime le 2024-07-14T23:59:59Z')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\AuditLogs\SignUps\SignUpsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new SignUpsRequestBuilderGetRequestConfiguration();
$queryParameters = SignUpsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "createdDateTime ge 2024-07-01T00:00:00Z and createdDateTime le 2024-07-14T23:59:59Z";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->auditLogs()->signUps()->get($requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Reports

Get-MgBetaAuditLogSignUp -Filter "createdDateTime ge 2024-07-01T00:00:00Z and createdDateTime le 2024-07-14T23:59:59Z" 
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.audit_logs.sign_ups.sign_ups_request_builder import SignUpsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = SignUpsRequestBuilder.SignUpsRequestBuilderGetQueryParameters(
		filter = "createdDateTime ge 2024-07-01T00:00:00Z and createdDateTime le 2024-07-14T23:59:59Z",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.audit_logs.sign_ups.get(request_configuration = request_configuration)
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#auditLogs/signUps",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET auditLogs/signUps?$select=appDisplayName,appId",
    "value": [
        {
            "appDisplayName": "TestApp4",
            "appId": "94559aba-b733-468e-aaec-44cc4e7f0b58",
            "correlationId": "f4414243-b0ee-4030-9c0c-d661c716a6b8",
            "createdDateTime": "2024-10-15T01:58:09.287604Z",
            "id": "921e63bd-a516-4976-a537-a6710d6a0000",
            "signUpStage": "userCreation",
            "signUpIdentityProvider": "Email OTP",
            "appliedEventListeners": [],
            "status": {
                "errorCode": 0,
                "failureReason": null,
                "additionalDetails": null
            },
            "signUpIdentity": {
                "signUpIdentifier": "testuser@fabrikam.com",
                "signUpIdentifierType": "emailAddress"
            },
            "userId": "9fb7a577-9469-4489-912d-bc58a5bca276"
        },
        {
            "appDisplayName": "TestApp4",
            "appId": "94559aba-b733-468e-aaec-44cc4e7f0b58",
            "correlationId": "f4414243-b0ee-4030-9c0c-d661c716a6b8",
            "createdDateTime": "2024-10-15T01:58:08.383114Z",
            "id": "5b515b07-411f-4759-a389-bce8289f0000",
            "signUpStage": "attributeCollectionAndValidation",
            "signUpIdentityProvider": "Email OTP",
            "userId": null,
            "appliedEventListeners": [],
            "status": {
                "errorCode": 0,
                "failureReason": null,
                "additionalDetails": null
            },
            "signUpIdentity": {
                "signUpIdentifier": "testuser@fabrikam.com",
                "signUpIdentifierType": "emailAddress"
            }
        },
        {
            "appDisplayName": "TestApp4",
            "appId": "94559aba-b733-468e-aaec-44cc4e7f0b58",
            "correlationId": "f4414243-b0ee-4030-9c0c-d661c716a6b8",
            "createdDateTime": "2024-10-15T01:57:49.368731Z",
            "id": "1ce058e4-d023-4ae4-9236-0c9d0f0f0200",
            "signUpStage": "credentialValidation",
            "signUpIdentityProvider": "Email OTP",
            "userId": null,
            "appliedEventListeners": [],
            "status": {
                "errorCode": 1002013,
                "failureReason": null,
                "additionalDetails": null
            },
            "signUpIdentity": {
                "signUpIdentifier": "testuser@fabrikam.com",
                "signUpIdentifierType": "emailAddress"
            }
        },
        {
            "appDisplayName": null,
            "appId": "94559aba-b733-468e-aaec-44cc4e7f0b58",
            "correlationId": "f4414243-b0ee-4030-9c0c-d661c716a6b8",
            "createdDateTime": "2024-10-15T01:57:36.362145Z",
            "id": "921e63bd-a516-4976-a537-a671036a0000",
            "signUpStage": "credentialCollection",
            "signUpIdentityProvider": "Email OTP",
            "userId": null,
            "appliedEventListeners": [],
            "status": {
                "errorCode": 0,
                "failureReason": null,
                "additionalDetails": null
            },
            "signUpIdentity": {
                "signUpIdentifier": "testuser@fabrikam.com",
                "signUpIdentifierType": "emailAddress"
            }
        }
    ]
}
```
