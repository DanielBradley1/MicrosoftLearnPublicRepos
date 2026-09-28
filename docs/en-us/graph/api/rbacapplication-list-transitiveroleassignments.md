<!-- Source: https://learn.microsoft.com/en-us/graph/api/rbacapplication-list-transitiveroleassignments?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# List transitiveRoleAssignment

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the list of direct and transitive [unifiedRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-beta) objects for a specific principal. For example, if a user is assigned a Microsoft Entra role through group membership, the role assignment is transitive, and this request will list the group's ID as the **principalId**. Results can also be filtered by the **roleDefinitionId** and **directoryScopeId**. Supported only for directory \(Microsoft Entra ID\) provider.

For more information, see [Use Microsoft Entra groups to manage role assignments](https://learn.microsoft.com/en-us/azure/active-directory/roles/groups-concept).

Note

This request might have replication delays for role assignments that were recently created, updated, or deleted. Learn more in [Designing for eventual consistency for Microsoft Entra](https://devblogs.microsoft.com/identity/designing-for-eventual-consistency-for-microsoft-entra/).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | RoleManagement.Read.Directory | Directory.Read.All, Directory.ReadWrite.All, RoleManagement.ReadWrite.Directory |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | RoleManagement.Read.Directory | Directory.Read.All, Directory.ReadWrite.All, RoleManagement.ReadWrite.Directory |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Directory Readers
- Global Reader
- Privileged Role Administrator

## HTTP request

To list transitive role assignments for a directory provider:

```http
GET /roleManagement/directory/transitiveRoleAssignments?$filter=principalId eq '{principalId}'
```

## Query parameters

This method requires the `$filter` \(`eq`\) OData query parameter to scope the transitive role assignments to a principal. You can narrow the scope of the request by expanding the filter to other supported properties. This method also supports the `$count` and `$select` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| ConsistencyLevel | eventual. This header, `$count`, and `$filter` are required. For more information about the use of **ConsistencyLevel**, `$count`, and `$filter`, see [Advanced query capabilities on directory objects](https://learn.microsoft.com/en-us/graph/aad-advanced-queries). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [unifiedRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-beta) objects in the response body.

If your request doesn't include the **ConsistencyLevel** header set to `eventual`, this method returns `404 Not Found` response code.

## Examples

For the examples in this section, consider the following role assignment scenario. A user named Alice has both direct and transitive role assignments as follows:

| User | Group | Role | Scope | Role assignment ID |
| :---: | :---: | :---: | :---: | :---: |
| Alice  <br>`2c7936bc-3517-40f3-8eda-4806637b6516` |  | User Administrator  <br>`fe930be7-5e62-47db-91af-98c3a49a38b1` | Tenant | RA1  <br>`857708a7-b5e0-44f9-bfd7-53531d72a739` |
|  | G1  <br>`ae2fc327-4c71-48ed-b6ca-f48632186510`  <br>\(Alice is a member\) | User Administrator  <br>`fe930be7-5e62-47db-91af-98c3a49a38b1` | Tenant | RA2  <br>`8a021d5f-7351-4713-aab4-b088504d476e` |
|  | G2  <br>`6ffb34b8-5e6d-4727-a7f9-93245e7f6ea8`  <br>\(Alice is a member\) | Helpdesk Administrator  <br>`729827e3-9c14-49f7-bb1b-9608f156bbb8` | Administrative unit \(AU1\)  <br>`26e79164-0c5c-4281-8c5b-be7bc7809fb2` | RA3  <br>`6cc86637-13c8-473f-afdc-e0e65c9734d2` |

- Alice is assigned the User Administrator role directly at tenant scope with role assignment RA1.
- Alice is member of a group G1 and G1 is assigned the User Administrator role at tenant scope with role assignment RA2.
- Alice is also a member of group G2 and G2 is assigned the Helpdesk Administrator role at an administrative unit AU1 scope with role assignment RA3.

### Example 1 : Get direct and transitive role assignments of a principal

#### Request

The following example shows a request. This request requires the **ConsistencyLevel** header set to `eventual` and the `$count=true` and `$filter` query parameters. For more information about the use of **ConsistencyLevel**, `$count`, and `$filter`, see [Advanced query capabilities on directory objects](https://learn.microsoft.com/en-us/graph/aad-advanced-queries).

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/beta/roleManagement/directory/transitiveRoleAssignments?$count=true&$filter=principalId eq '2c7936bc-3517-40f3-8eda-4806637b6516'
ConsistencyLevel: eventual
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.RoleManagement.Directory.TransitiveRoleAssignments.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Count = true;
	requestConfiguration.QueryParameters.Filter = "principalId eq '2c7936bc-3517-40f3-8eda-4806637b6516'";
	requestConfiguration.Headers.Add("ConsistencyLevel", "eventual");
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
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphrolemanagement "github.com/microsoftgraph/msgraph-beta-sdk-go/rolemanagement"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("ConsistencyLevel", "eventual")


requestCount := true
requestFilter := "principalId eq '2c7936bc-3517-40f3-8eda-4806637b6516'"

requestParameters := &graphrolemanagement.DirectoryTransitiveRoleAssignmentsRequestBuilderGetQueryParameters{
	Count: &requestCount,
	Filter: &requestFilter,
}
configuration := &graphrolemanagement.DirectoryTransitiveRoleAssignmentsRequestBuilderGetRequestConfiguration{
	Headers: headers,
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
transitiveRoleAssignments, err := graphClient.RoleManagement().Directory().TransitiveRoleAssignments().Get(context.Background(), configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleAssignmentCollectionResponse result = graphClient.roleManagement().directory().transitiveRoleAssignments().get(requestConfiguration -> {
	requestConfiguration.queryParameters.count = true;
	requestConfiguration.queryParameters.filter = "principalId eq '2c7936bc-3517-40f3-8eda-4806637b6516'";
	requestConfiguration.headers.add("ConsistencyLevel", "eventual");
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

let transitiveRoleAssignments = await client.api('/roleManagement/directory/transitiveRoleAssignments')
	.version('beta')
	.header('ConsistencyLevel','eventual')
	.filter('principalId eq \'2c7936bc-3517-40f3-8eda-4806637b6516\'')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\RoleManagement\Directory\TransitiveRoleAssignments\TransitiveRoleAssignmentsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new TransitiveRoleAssignmentsRequestBuilderGetRequestConfiguration();
$headers = [
		'ConsistencyLevel' => 'eventual',
	];
$requestConfiguration->headers = $headers;

$queryParameters = TransitiveRoleAssignmentsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->count = true;
$queryParameters->filter = "principalId eq '2c7936bc-3517-40f3-8eda-4806637b6516'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->roleManagement()->directory()->transitiveRoleAssignments()->get($requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

Get-MgBetaRoleManagementDirectoryTransitiveRoleAssignment -CountVariable CountVar -Filter "principalId eq '2c7936bc-3517-40f3-8eda-4806637b6516'"  -ConsistencyLevel eventual 
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.role_management.directory.transitive_role_assignments.transitive_role_assignments_request_builder import TransitiveRoleAssignmentsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = TransitiveRoleAssignmentsRequestBuilder.TransitiveRoleAssignmentsRequestBuilderGetQueryParameters(
		count = True,
		filter = "principalId eq '2c7936bc-3517-40f3-8eda-4806637b6516'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)
request_configuration.headers.add("ConsistencyLevel", "eventual")


result = await graph_client.role_management.directory.transitive_role_assignments.get(request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability. All the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#roleManagement/directory/transitiveRoleAssignments",
    "value": [
        {
            "id": "857708a7-b5e0-44f9-bfd7-53531d72a739",
            "principalId": "2c7936bc-3517-40f3-8eda-4806637b6516",
            "directoryScopeId": "/",
            "roleDefinitionId": "fe930be7-5e62-47db-91af-98c3a49a38b1"
        },
        {
            "id": "8a021d5f-7351-4713-aab4-b088504d476e",
            "principalId": "ae2fc327-4c71-48ed-b6ca-f48632186510",
            "directoryScopeId": "/",
            "roleDefinitionId": "fe930be7-5e62-47db-91af-98c3a49a38b1"
        },
        {
            "id": "6cc86637-13c8-473f-afdc-e0e65c9734d2",
            "principalId": "6ffb34b8-5e6d-4727-a7f9-93245e7f6ea8",
            "directoryScopeId": "/administrativeUnits/26e79164-0c5c-4281-8c5b-be7bc7809fb2",
            "roleDefinitionId": "729827e3-9c14-49f7-bb1b-9608f156bbb8"
        }
    ]
}
```

### Example 2: Get direct and transitive assignments of a principal, but only specific role definitions

#### Request

The following example shows a request. This request requires the **ConsistencyLevel** header set to `eventual` and the `$count=true` and `$filter` query parameters. For more information about the use of **ConsistencyLevel**, `$count`, and `$filter`, see [Advanced query capabilities on directory objects](https://learn.microsoft.com/en-us/graph/aad-advanced-queries).

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
GET https://graph.microsoft.com/beta/roleManagement/directory/transitiveRoleAssignments?$count=true&$filter=principalId eq '2c7936bc-3517-40f3-8eda-4806637b6516' and roleDefinitionId eq 'fe930be7-5e62-47db-91af-98c3a49a38b1'
ConsistencyLevel: eventual
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.RoleManagement.Directory.TransitiveRoleAssignments.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Count = true;
	requestConfiguration.QueryParameters.Filter = "principalId eq '2c7936bc-3517-40f3-8eda-4806637b6516' and roleDefinitionId eq 'fe930be7-5e62-47db-91af-98c3a49a38b1'";
	requestConfiguration.Headers.Add("ConsistencyLevel", "eventual");
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
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphrolemanagement "github.com/microsoftgraph/msgraph-beta-sdk-go/rolemanagement"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("ConsistencyLevel", "eventual")


requestCount := true
requestFilter := "principalId eq '2c7936bc-3517-40f3-8eda-4806637b6516' and roleDefinitionId eq 'fe930be7-5e62-47db-91af-98c3a49a38b1'"

requestParameters := &graphrolemanagement.DirectoryTransitiveRoleAssignmentsRequestBuilderGetQueryParameters{
	Count: &requestCount,
	Filter: &requestFilter,
}
configuration := &graphrolemanagement.DirectoryTransitiveRoleAssignmentsRequestBuilderGetRequestConfiguration{
	Headers: headers,
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
transitiveRoleAssignments, err := graphClient.RoleManagement().Directory().TransitiveRoleAssignments().Get(context.Background(), configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleAssignmentCollectionResponse result = graphClient.roleManagement().directory().transitiveRoleAssignments().get(requestConfiguration -> {
	requestConfiguration.queryParameters.count = true;
	requestConfiguration.queryParameters.filter = "principalId eq '2c7936bc-3517-40f3-8eda-4806637b6516' and roleDefinitionId eq 'fe930be7-5e62-47db-91af-98c3a49a38b1'";
	requestConfiguration.headers.add("ConsistencyLevel", "eventual");
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

let transitiveRoleAssignments = await client.api('/roleManagement/directory/transitiveRoleAssignments')
	.version('beta')
	.header('ConsistencyLevel','eventual')
	.filter('principalId eq \'2c7936bc-3517-40f3-8eda-4806637b6516\' and roleDefinitionId eq \'fe930be7-5e62-47db-91af-98c3a49a38b1\'')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\RoleManagement\Directory\TransitiveRoleAssignments\TransitiveRoleAssignmentsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new TransitiveRoleAssignmentsRequestBuilderGetRequestConfiguration();
$headers = [
		'ConsistencyLevel' => 'eventual',
	];
$requestConfiguration->headers = $headers;

$queryParameters = TransitiveRoleAssignmentsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->count = true;
$queryParameters->filter = "principalId eq '2c7936bc-3517-40f3-8eda-4806637b6516' and roleDefinitionId eq 'fe930be7-5e62-47db-91af-98c3a49a38b1'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->roleManagement()->directory()->transitiveRoleAssignments()->get($requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

Get-MgBetaRoleManagementDirectoryTransitiveRoleAssignment -CountVariable CountVar -Filter "principalId eq '2c7936bc-3517-40f3-8eda-4806637b6516' and roleDefinitionId eq 'fe930be7-5e62-47db-91af-98c3a49a38b1'"  -ConsistencyLevel eventual 
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.role_management.directory.transitive_role_assignments.transitive_role_assignments_request_builder import TransitiveRoleAssignmentsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = TransitiveRoleAssignmentsRequestBuilder.TransitiveRoleAssignmentsRequestBuilderGetQueryParameters(
		count = True,
		filter = "principalId eq '2c7936bc-3517-40f3-8eda-4806637b6516' and roleDefinitionId eq 'fe930be7-5e62-47db-91af-98c3a49a38b1'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)
request_configuration.headers.add("ConsistencyLevel", "eventual")


result = await graph_client.role_management.directory.transitive_role_assignments.get(request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability. All the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#roleManagement/directory/transitiveRoleAssignments",
    "value": [
        {
            "id": "857708a7-b5e0-44f9-bfd7-53531d72a739",
            "principalId": "2c7936bc-3517-40f3-8eda-4806637b6516",
            "directoryScopeId": "/",
            "roleDefinitionId": "fe930be7-5e62-47db-91af-98c3a49a38b1"
        },
        {
            "id": "8a021d5f-7351-4713-aab4-b088504d476e",
            "principalId": "6ffb34b8-5e6d-4727-a7f9-93245e7f6ea8",
            "directoryScopeId": "/",
            "roleDefinitionId": "fe930be7-5e62-47db-91af-98c3a49a38b1"
        }
    ]
}
```

### Example 3: Get direct and transitive role assignments of a principal, but only administrative unit scoped

#### Request

The following example shows a request. This request requires the **ConsistencyLevel** header set to `eventual` and the `$count=true` and `$filter` query parameters. For more information about the use of **ConsistencyLevel**, `$count`, and `$filter`, see [Advanced query capabilities on directory objects](https://learn.microsoft.com/en-us/graph/aad-advanced-queries).

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
GET https://graph.microsoft.com/beta/roleManagement/directory/transitiveRoleAssignments?$count=true&$filter=principalId eq '2c7936bc-3517-40f3-8eda-4806637b6516' and directoryScopeId eq '/administrativeUnits/26e79164-0c5c-4281-8c5b-be7bc7809fb2'
ConsistencyLevel: eventual
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.RoleManagement.Directory.TransitiveRoleAssignments.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Count = true;
	requestConfiguration.QueryParameters.Filter = "principalId eq '2c7936bc-3517-40f3-8eda-4806637b6516' and directoryScopeId eq '/administrativeUnits/26e79164-0c5c-4281-8c5b-be7bc7809fb2'";
	requestConfiguration.Headers.Add("ConsistencyLevel", "eventual");
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
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphrolemanagement "github.com/microsoftgraph/msgraph-beta-sdk-go/rolemanagement"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("ConsistencyLevel", "eventual")


requestCount := true
requestFilter := "principalId eq '2c7936bc-3517-40f3-8eda-4806637b6516' and directoryScopeId eq '/administrativeUnits/26e79164-0c5c-4281-8c5b-be7bc7809fb2'"

requestParameters := &graphrolemanagement.DirectoryTransitiveRoleAssignmentsRequestBuilderGetQueryParameters{
	Count: &requestCount,
	Filter: &requestFilter,
}
configuration := &graphrolemanagement.DirectoryTransitiveRoleAssignmentsRequestBuilderGetRequestConfiguration{
	Headers: headers,
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
transitiveRoleAssignments, err := graphClient.RoleManagement().Directory().TransitiveRoleAssignments().Get(context.Background(), configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleAssignmentCollectionResponse result = graphClient.roleManagement().directory().transitiveRoleAssignments().get(requestConfiguration -> {
	requestConfiguration.queryParameters.count = true;
	requestConfiguration.queryParameters.filter = "principalId eq '2c7936bc-3517-40f3-8eda-4806637b6516' and directoryScopeId eq '/administrativeUnits/26e79164-0c5c-4281-8c5b-be7bc7809fb2'";
	requestConfiguration.headers.add("ConsistencyLevel", "eventual");
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

let transitiveRoleAssignments = await client.api('/roleManagement/directory/transitiveRoleAssignments')
	.version('beta')
	.header('ConsistencyLevel','eventual')
	.filter('principalId eq \'2c7936bc-3517-40f3-8eda-4806637b6516\' and directoryScopeId eq \'/administrativeUnits/26e79164-0c5c-4281-8c5b-be7bc7809fb2\'')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\RoleManagement\Directory\TransitiveRoleAssignments\TransitiveRoleAssignmentsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new TransitiveRoleAssignmentsRequestBuilderGetRequestConfiguration();
$headers = [
		'ConsistencyLevel' => 'eventual',
	];
$requestConfiguration->headers = $headers;

$queryParameters = TransitiveRoleAssignmentsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->count = true;
$queryParameters->filter = "principalId eq '2c7936bc-3517-40f3-8eda-4806637b6516' and directoryScopeId eq '/administrativeUnits/26e79164-0c5c-4281-8c5b-be7bc7809fb2'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->roleManagement()->directory()->transitiveRoleAssignments()->get($requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

Get-MgBetaRoleManagementDirectoryTransitiveRoleAssignment -CountVariable CountVar -Filter "principalId eq '2c7936bc-3517-40f3-8eda-4806637b6516' and directoryScopeId eq '/administrativeUnits/26e79164-0c5c-4281-8c5b-be7bc7809fb2'"  -ConsistencyLevel eventual 
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.role_management.directory.transitive_role_assignments.transitive_role_assignments_request_builder import TransitiveRoleAssignmentsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = TransitiveRoleAssignmentsRequestBuilder.TransitiveRoleAssignmentsRequestBuilderGetQueryParameters(
		count = True,
		filter = "principalId eq '2c7936bc-3517-40f3-8eda-4806637b6516' and directoryScopeId eq '/administrativeUnits/26e79164-0c5c-4281-8c5b-be7bc7809fb2'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)
request_configuration.headers.add("ConsistencyLevel", "eventual")


result = await graph_client.role_management.directory.transitive_role_assignments.get(request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability. All the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#roleManagement/directory/transitiveRoleAssignments",
    "value": [
        {
            "id": "6cc86637-13c8-473f-afdc-e0e65c9734d2",
            "principalId": "6ffb34b8-5e6d-4727-a7f9-93245e7f6ea8",
            "directoryScopeId": "/administrativeUnits/26e79164-0c5c-4281-8c5b-be7bc7809fb2",
            "roleDefinitionId": "729827e3-9c14-49f7-bb1b-9608f156bbb8"
        }
    ]
}
```
