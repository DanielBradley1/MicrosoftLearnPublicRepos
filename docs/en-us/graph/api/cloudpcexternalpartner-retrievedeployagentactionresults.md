<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcexternalpartner-retrievedeployagentactionresults?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# cloudPcExternalPartner: retrieveDeployAgentActionResults

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Retrieve the status of a specific deployment action on a specific Cloud PC device. If both activityId and cloudPcId are empty, the paging results are returned, and the pagination size is 100.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.Read.All | CloudPC.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.Read.All | CloudPC.ReadWrite.All |

## HTTP request

```http
GET /deviceManagement/virtualEndpoint/externalPartners/{cloudPcExternalPartnerId}/retrieveDeployAgentActionResults(activityId='{activitId}',cloudPcId='{cloudPcId}')
```

## Function parameters

In the request URL, provide the following OData function-call parameters with values.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| activityId | String | The activity ID of agent deployment. |
| cloudPcId | String | The Cloud PC ID that belongs the given deployment activity. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [cloudPcExternalPartnerActionResult](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartneractionresult?view=graph-rest-beta) collection in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [JavaScript](#tabpanel_1_javascript)

```http
GET https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/externalPartners/b3548526-e615-3785-3118-be70b3968ec5/retrieveDeployAgentActionResults(activityId='9adc7d86-6411-407e-b936-abfa0470dccf',cloudPcId='')
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.VirtualEndpoint.ExternalPartners["{cloudPcExternalPartner-id}"].RetrieveDeployAgentActionResults().GetAsRetrieveDeployAgentActionResultsGetResponseAsync();
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
retrieveDeployAgentActionResults, err := graphClient.DeviceManagement().VirtualEndpoint().ExternalPartners().ByCloudPcExternalPartnerId("cloudPcExternalPartner-id").RetrieveDeployAgentActionResultsWithActivityIdWithCloudPcId(&activityId, &cloudPcId).GetAsRetrieveDeployAgentActionResultsGetResponse(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let retrieveDeployAgentActionResults = await client.api('/deviceManagement/virtualEndpoint/externalPartners/b3548526-e615-3785-3118-be70b3968ec5/retrieveDeployAgentActionResults(activityId='9adc7d86-6411-407e-b936-abfa0470dccf',cloudPcId='')')
	.version('beta')
	.get();
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
        "activityId": "9adc7d86-6411-407e-b936-abfa0470dccf",
        "cloudPcId": "30d0e128-de93-41dc-89ec-33d84bb662a0",
        "state": "canceled",
        "startDateTime": "2025-12-13T03:22:53.0681671Z",
        "lastModifiedDateTime": "2025-12-13T03:22:53Z",
        "errorCode": "deviceNotFound",
        "errorMessage": "Cloud PC not found or invalid"
    },
    {
        "activityId": "9adc7d86-6411-407e-b936-abfa0470dccf",
        "cloudPcId": "7c82a3e3-9459-44e4-94d9-b92f93bf78dd",
        "state": "succeeded",
        "startDateTime": "2025-12-14T03:22:53.0681671Z",
        "lastModifiedDateTime": "2025-12-14T03:22:53Z",
        "errorCode": "none",
        "errorMessage": ""
    }
  ]
}
```
