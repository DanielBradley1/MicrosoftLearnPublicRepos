<!-- Source: https://learn.microsoft.com/en-us/graph/api/accesspackageassignment-additionalaccess?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# accessPackageAssignment: additionalAccess

Namespace: microsoft.graph

In [Microsoft Entra Entitlement Management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0), retrieve a collection of [accessPackageAssignment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-1.0) objects that indicate a target user has an assignment to a specified access package and also an assignment to another, potentially incompatible, access package. This can be used to prepare to configure the incompatible access packages for a specific access package.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EntitlementManagement.Read.All | EntitlementManagement.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EntitlementManagement.Read.All | EntitlementManagement.ReadWrite.All |

Tip

For delegated access using work or school accounts, the signed-in user must be assigned an administrator role with supported role permissions through one of the following options:

- A [role in the Entitlement Management system](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) where the least privileged roles are:

  - *Catalog reader*. **This is the least privileged option**
  - *Catalog creator*
  - *Access package manager*

- More privileged [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) supported for this operation:

  - Security Reader
  - Global Reader
  - Compliance Administrator
  - Security Administrator
  - Identity Governance Administrator

In app-only scenarios, the calling app can be assigned one of the preceding supported roles instead of the `EntitlementManagement.Read.All` application permission. The *Catalog reader* role is less privileged than the `EntitlementManagement.Read.All` application permission.

For more information, see [Delegation and roles in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) and [how to delegate access governance to access package managers in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate-managers).

## HTTP request

```http
GET /identityGovernance/entitlementManagement/assignments/additionalAccess(accessPackageId='parameterValue',incompatibleAccessPackageId='parameterValue')
```

## Function parameters

The following table shows the parameters that must be supplied with this function. The two access package IDs must be distinct.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| accessPackageId | String | Indicates the ID of an access package for which the caller would like to retrieve the assignments. Required. |
| incompatibleAccessPackageId | String | The specific incompatible access package for which the caller would like to retrieve only those assignments where the user also has an assignment to this incompatible access package. Required. |

## Optional query parameters

This method supports the `$select`, `$filter`, and `$expand` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [accessPackageAssignment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-1.0) objects in the response body.

When a result set spans multiple pages, Microsoft Graph returns that page with an `@odata.nextLink` property in the response that contains a URL to the next page of results. If that property is present, continue making additional requests with the `@odata.nextLink` URL in each response, until all the results are returned. For more information, see [paging Microsoft Graph data in your app](https://learn.microsoft.com/en-us/graph/paging).

## Examples

The following example gets the access package assignments for users who have assignments to both access packages.

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/assignments/additionalAccess(accessPackageId='2506aef1-3929-4d24-a61e-7c8b83d95e6f',incompatibleAccessPackageId='d5d99728-8c0b-4ede-83d2-cf9b0e8dabfb')?$expand=target
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.Assignments.AdditionalAccessWithAccessPackageIdWithIncompatibleAccessPackageId("{accessPackageId}","{incompatibleAccessPackageId}").GetAsAdditionalAccessWithAccessPackageIdWithIncompatibleAccessPackageIdGetResponseAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Expand = new string []{ "target" };
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/identitygovernance"
	  //other-imports
)

requestParameters := &graphidentitygovernance.EntitlementManagementAssignmentsAdditionalAccessWithAccessPackageIdWithIncompatibleAccessPackageIdRequestBuilderGetQueryParameters{
	Expand: [] string {"target"},
}
configuration := &graphidentitygovernance.EntitlementManagementAssignmentsAdditionalAccessWithAccessPackageIdWithIncompatibleAccessPackageIdRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageId := "{accessPackageId}"
incompatibleAccessPackageId := "{incompatibleAccessPackageId}"
additionalAccess, err := graphClient.IdentityGovernance().EntitlementManagement().Assignments().AdditionalAccessWithAccessPackageIdWithIncompatibleAccessPackageId(&accessPackageId, &incompatibleAccessPackageId).GetAsAdditionalAccessWithAccessPackageIdWithIncompatibleAccessPackageIdGetResponse(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.identityGovernance().entitlementManagement().assignments().additionalAccessWithAccessPackageIdWithIncompatibleAccessPackageId("{accessPackageId}", "{incompatibleAccessPackageId}").get(requestConfiguration -> {
	requestConfiguration.queryParameters.expand = new String []{"target"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let additionalAccess = await client.api('/identityGovernance/entitlementManagement/assignments/additionalAccess(accessPackageId='2506aef1-3929-4d24-a61e-7c8b83d95e6f',incompatibleAccessPackageId='d5d99728-8c0b-4ede-83d2-cf9b0e8dabfb')')
	.expand('target')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\EntitlementManagement\Assignments\AdditionalAccess(accessPackageId='{accessPackageId}',incompatibleAccessPackageId='{incompatibleAccessPackageId}')\AdditionalAccessWithAccessPackageIdWithIncompatibleAccessPackageIdRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new AdditionalAccessWithAccessPackageIdWithIncompatibleAccessPackageIdRequestBuilderGetRequestConfiguration();
$queryParameters = AdditionalAccessWithAccessPackageIdWithIncompatibleAccessPackageIdRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->expand = ["target"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identityGovernance()->entitlementManagement()->assignments()->additionalAccessWithAccessPackageIdWithIncompatibleAccessPackageId('{accessPackageId}', '{incompatibleAccessPackageId}', )->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity_governance.entitlement_management.assignments.additional_access(access_package_id='{access_package_id}',incompatible_access_package_id='{incompatible_access_package_id}').additional_access_with_access_package_id_with_incompatible_access_package_id_request_builder import AdditionalAccessWithAccessPackageIdWithIncompatibleAccessPackageIdRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = AdditionalAccessWithAccessPackageIdWithIncompatibleAccessPackageIdRequestBuilder.AdditionalAccessWithAccessPackageIdWithIncompatibleAccessPackageIdRequestBuilderGetQueryParameters(
		expand = ["target"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity_governance.entitlement_management.assignments.additional_access_with_access_package_id_with_incompatible_access_package_id("{accessPackageId}","{incompatibleAccessPackageId}").get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
        {
            "@odata.type": "#microsoft.graph.accessPackageAssignment",
            "id": "a61f7889-ae61-4e97-a4dc-e4fa525f5b33",
            "target": {
                "id": "ebaf071e-c647-42c6-b86f-fbe3625b4b63",
                "objectId": "cdbdf152-82ce-479c-b5b8-df90f561d5c7",
                "displayName": "user1"
            }
        },
        {
            "@odata.type": "#microsoft.graph.accessPackageAssignment",
            "id": "a7284263-8233-44de-8095-0ee3ff5a1716",
            "target": {
                "id": "9865b0f8-868f-42c6-a49b-3067eb4b2da1",
                "objectId": "79a8f0b6-61dc-41db-b49e-470c278e05b6",
                "displayName": "user2"
            }
        }
  ]
}
```
