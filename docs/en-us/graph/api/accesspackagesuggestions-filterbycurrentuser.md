<!-- Source: https://learn.microsoft.com/en-us/graph/api/accesspackagesuggestions-filterbycurrentuser?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-08 -->

# accessPackageSuggestions: filterByCurrentUser

Namespace: microsoft.graph

Retrieve suggested [accessPackageSuggestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesuggestion?view=graph-rest-1.0) objects for the current end user. This operation returns access packages that are suggested based on various criteria such as related people insights and the user's assignment history.

The suggestions help end users discover relevant access packages they may need for their role or work context.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EntitlementMgmt-SubjectAccess.ReadWrite | EntitlementManagement.Read.All, EntitlementManagement.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EntitlementManagement.Read.All | EntitlementManagement.ReadWrite.All |

## HTTP request

```http
GET /identityGovernance/entitlementManagement/accessPackageSuggestions/filterByCurrentUser(on='{on}')
```

## Function parameters

In the request URL, provide the following query parameters with values.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| on | accessPackageSuggestionFilterByCurrentUserOptions | Filter to determine which suggestions to return. This is a flags enum that allows multiple values to be specified. The possible values are: `none`, `relatedPeopleAssignments`, `assignmentHistory`, `unknownFutureValue`. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [accessPackageSuggestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesuggestion?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1: Get all access package suggestions with default insight types

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/accessPackageSuggestions/filterByCurrentUser(on='relatedPeopleAssignments,assignmentHistory')?$expand=accessPackage
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageSuggestions["{accessPackageSuggestion-id}"].GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Expand = new string []{ "accessPackage" };
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

requestParameters := &graphidentitygovernance.EntitlementManagementAccessPackageSuggestionsItemRequestBuilderGetQueryParameters{
	Expand: [] string {"accessPackage"},
}
configuration := &graphidentitygovernance.EntitlementManagementAccessPackageSuggestionsItemRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageSuggestions, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageSuggestions().ByAccessPackageSuggestionId("accessPackageSuggestion-id").Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageSuggestion result = graphClient.identityGovernance().entitlementManagement().accessPackageSuggestions().byAccessPackageSuggestionId("{accessPackageSuggestion-id}").get(requestConfiguration -> {
	requestConfiguration.queryParameters.expand = new String []{"accessPackage"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let filterByCurrentUser = await client.api('/identityGovernance/entitlementManagement/accessPackageSuggestions/filterByCurrentUser(on='relatedPeopleAssignments,assignmentHistory')')
	.expand('accessPackage')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\EntitlementManagement\AccessPackageSuggestions\Item\AccessPackageSuggestionItemRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new AccessPackageSuggestionItemRequestBuilderGetRequestConfiguration();
$queryParameters = AccessPackageSuggestionItemRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->expand = ["accessPackage"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageSuggestions()->byAccessPackageSuggestionId('accessPackageSuggestion-id')->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgEntitlementManagementAccessPackageSuggestion -AccessPackageSuggestionId $accessPackageSuggestionId -ExpandProperty "accessPackage"  -On $onId -AssignmentHistory') $assignmentHistory')Id 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity_governance.entitlement_management.access_package_suggestions.item.access_package_suggestion_item_request_builder import AccessPackageSuggestionItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = AccessPackageSuggestionItemRequestBuilder.AccessPackageSuggestionItemRequestBuilderGetQueryParameters(
		expand = ["accessPackage"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity_governance.entitlement_management.access_package_suggestions.by_access_package_suggestion_id('accessPackageSuggestion-id').get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/accessPackageSuggestions/filterByCurrentUser(on='relatedPeopleAssignments,assignmentHistory')",
  "value": [
    {
      "id": "51b4bd29-cb2d-ef11-8b5f-20c19bd3bce6",
      "reasons": [
        {
          "@odata.type": "#microsoft.graph.accessPackageSuggestionRelatedPeopleBased",
          "relatedPeopleAssignmentCount": 2
        },
        {
          "@odata.type": "#microsoft.graph.accessPackageSuggestionSelfAssignmentHistoryBased",
          "pastAssignmentCount": 2,
          "lastAssignmentDateTime": "2024-08-08T19:13:50.023Z"
        }
      ],
      "accessPackage": {
        "id": "51b4bd29-cb2d-ef11-8b5f-20c19bd3bce6",
        "displayName": "Marketing Team Access",
        "description": "Access package providing marketing team resources and permissions"
      }
    },
    {
      "id": "fa6338d0-d12d-ef11-8b5f-20c19bd3bce6",
      "reasons": [
        {
          "@odata.type": "#microsoft.graph.accessPackageSuggestionRelatedPeopleBased",
          "relatedPeopleAssignmentCount": 3
        }
      ],
      "accessPackage": {
        "id": "fa6338d0-d12d-ef11-8b5f-20c19bd3bce6",
        "displayName": "Engineering Team Access",
        "description": "Access package for engineering resources"
      }
    }
  ]
}
```

### Example 2: Get access package suggestions based on assignment history

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
GET https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/accessPackageSuggestions/filterByCurrentUser(on='assignmentHistory')?$expand=accessPackage
```

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let filterByCurrentUser = await client.api('/identityGovernance/entitlementManagement/accessPackageSuggestions/filterByCurrentUser(on='assignmentHistory')')
	.expand('accessPackage')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Invoke-MgFilterEntitlementManagementAccessPackageSuggestionByCurrentUser -ExpandProperty "accessPackage"  -On $onId 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/accessPackageSuggestions/filterByCurrentUser(on='assignmentHistory')",
  "value": [
    {
      "id": "97ce41d0-fc5c-4e10-a979-1ad18e8242d7",
      "reasons": [
        {
          "@odata.type": "#microsoft.graph.accessPackageSuggestionSelfAssignmentHistoryBased",
          "pastAssignmentCount": 3,
          "lastAssignmentDateTime": "2024-11-28T01:28:15.313Z"
        }
      ],
      "accessPackage": {
        "id": "97ce41d0-fc5c-4e10-a979-1ad18e8242d7",
        "displayName": "Sales Team Access",
        "description": "Access package for sales team"
      }
    }
  ]
}
```
