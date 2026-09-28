<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamsadministration-telephonenumbermanagementroot-list-numberassignments?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# List numberAssignments

Namespace: microsoft.graph.teamsAdministration

Read the properties and relationships of [microsoft.graph.teamsAdministration.numberAssignment](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-numberassignment?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamsTelephoneNumber.Read.All | TeamsTelephoneNumber.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamsTelephoneNumber.Read.All | TeamsTelephoneNumber.ReadWrite.All |

## HTTP request

```http
GET /admin/teams/telephoneNumberManagement/numberAssignments
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters). The following optional parameters are supported:

- `$filter`: Use the `$filter` query parameter to retrieve just a subset of a collection. For example, you can use the `$filter` parameter to retrieve those telephone numbers with numberType equals `DirectRouting`. Filter can be applied by appending the following expression to the query `$filter=numberType eq ‘DirectRouting’`. All fields from the number assignments can be filtered except `id` and `city`.
- `$Top`: Use the `$Top` parameter to return first “X” number of results. Default number of results is 500 entries and maximum 1,000 entries allowed per query.
- `$Skip`: Use the `$Skip` query parameter to skip first “X” number of results. Default value is 0

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [numberAssignment](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-numberassignment?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1

#### Request

The following example shows a request to get a list of all telephone numbers, including assignment details.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/admin/teams/telephoneNumberManagement/numberAssignments
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Teams.TelephoneNumberManagement.NumberAssignments.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
numberAssignments, err := graphClient.Admin().Teams().TelephoneNumberManagement().NumberAssignments().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.teamsadministration.NumberAssignmentCollectionResponse result = graphClient.admin().teams().telephoneNumberManagement().numberAssignments().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let numberAssignments = await client.api('/admin/teams/telephoneNumberManagement/numberAssignments')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->admin()->teams()->telephoneNumberManagement()->numberAssignments()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.admin.teams.telephone_number_management.number_assignments.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.teamsAdministration.numberAssignment",
    "id": "YmMyNjMyZTMtNzUwYy00N2Q3LWFlYWUtOWZlZTAzNWJjMGM3fCsxMjAyMzQ1Njc4OA",
    "telephoneNumber": "+112345",
    "operatorId": "7a205197-8e59-487d-b9fa-3fc1b108f1e5",
    "numberType": "directRouting",
    "activationState": "activated",
    "capabilities": [
      "conferenceAssignment",
        "voiceApplicationAssignment",
        "userAssignment"
    ],
    "locationId": null,
    "civicAddressId": null,
    "networkSiteId": null,
    "assignmentTargetId": "22ed44ab-7759-4649-818e-6af3242dbc5d",
    "assignmentCategory": "primary",
    "portInStatus": null,
    "assignmentStatus": "userAssigned",
    "isoCountryCode": null,
    "city": null,
    "numberSource": "online",
    "supportedCustomerActions": [
      "locationUpdate"
    ],
    "reverseNumberLookupOptions": []
  },
    "value": {
    "@odata.type": "#microsoft.graph.teamsAdministration.numberAssignment",
    "id": "YmMyNjMyZTMtNzUwYy00N2Q3LWFlYWUtOWZlZTAzNWJjMGM3fCsxMjAyMzQ1Njc4OQ",
    "telephoneNumber": "+12052582895",
    "operatorId": "0019adbc-b82a-47b4-a799-4e993a9982f1",
    "numberType": "callingPlan",
    "activationState": "activated",
    "capabilities": [
      "conferenceAssignment"
    ],
    "locationId": null,
    "civicAddressId": null,
    "networkSiteId": null,
    "assignmentTargetId": "207a6836-d031-4764-a9d8-c1193f455f21",
    "assignmentCategory": "primary",
    "portInStatus": null,
    "assignmentStatus": "conferenceAssigned",
    "isoCountryCode": "US",
    "city": "Clanton",
    "numberSource": "online",
    "supportedCustomerActions": [
      "locationUpdate",
       "release"
    ],
    "reverseNumberLookupOptions": []
  }
  
}
```

### Example 2

#### Request

The following example shows a request to get a list of telephone numbers based on a filter.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [Python](#tabpanel_2_python)

```msgraph
GET https://graph.microsoft.com/v1.0/admin/teams/telephoneNumberManagement/numberAssignments?$filter=assignmentStatus eq 'unassigned' and capabilities/any(c:c eq 'userAssignment')
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Teams.TelephoneNumberManagement.NumberAssignments.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "assignmentStatus eq 'unassigned' and capabilities/any(c:c eq 'userAssignment')";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphadmin "github.com/microsoftgraph/msgraph-sdk-go/admin"
	  //other-imports
)


requestFilter := "assignmentStatus eq 'unassigned' and capabilities/any(c:c eq 'userAssignment')"

requestParameters := &graphadmin.TeamsTelephoneNumberManagementNumberAssignmentsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphadmin.TeamsTelephoneNumberManagementNumberAssignmentsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
numberAssignments, err := graphClient.Admin().Teams().TelephoneNumberManagement().NumberAssignments().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.teamsadministration.NumberAssignmentCollectionResponse result = graphClient.admin().teams().telephoneNumberManagement().numberAssignments().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "assignmentStatus eq 'unassigned' and capabilities/any(c:c eq 'userAssignment')";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let numberAssignments = await client.api('/admin/teams/telephoneNumberManagement/numberAssignments')
	.filter('assignmentStatus eq \'unassigned\' and capabilities/any(c:c eq \'userAssignment\')')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Admin\Teams\TelephoneNumberManagement\NumberAssignments\NumberAssignmentsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new NumberAssignmentsRequestBuilderGetRequestConfiguration();
$queryParameters = NumberAssignmentsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "assignmentStatus eq 'unassigned' and capabilities/any(c:c eq 'userAssignment')";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->admin()->teams()->telephoneNumberManagement()->numberAssignments()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.admin.teams.telephone_number_management.number_assignments.number_assignments_request_builder import NumberAssignmentsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = NumberAssignmentsRequestBuilder.NumberAssignmentsRequestBuilderGetQueryParameters(
		filter = "assignmentStatus eq 'unassigned' and capabilities/any(c:c eq 'userAssignment')",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.admin.teams.telephone_number_management.number_assignments.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.teamsAdministration.numberAssignment",
    "id": "YmMyNjMyZTMtNzUwYy00N2Q3LWFlYWUtOWZlZTAzNWJjMGM3fCsxMjAzNDU2Nzgy",
    "telephoneNumber": "+1123457",
    "operatorId": "7a205197-8e59-487d-b9fa-3fc1b108f1e5",
    "numberType": "directRouting",
    "activationState": "activated",
    "capabilities": [
      "conferenceAssignment",
        "voiceApplicationAssignment",
        "userAssignment"
    ],
    "locationId": null,
    "civicAddressId": null,
    "networkSiteId": null,
    "assignmentTargetId": null,
    "assignmentCategory": null,
    "portInStatus": null,
    "assignmentStatus": "unassigned",
    "isoCountryCode": null,
    "city": null,
    "numberSource": "online",
    "supportedCustomerActions": [
      "locationUpdate"
    ],
    "reverseNumberLookupOptions": []
  }
}
```

### Example 3

#### Request

The following example shows a request to get a list of telephone numbers using `$top` and `$skip` for pagination.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [Python](#tabpanel_3_python)

```msgraph
GET https://graph.microsoft.com/v1.0/admin/teams/telephoneNumberManagement/numberAssignments?$top=100&$skip=200
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Teams.TelephoneNumberManagement.NumberAssignments.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Top = 100;
	requestConfiguration.QueryParameters.Skip = 200;
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphadmin "github.com/microsoftgraph/msgraph-sdk-go/admin"
	  //other-imports
)


requestTop := int32(100)
requestSkip := int32(200)

requestParameters := &graphadmin.TeamsTelephoneNumberManagementNumberAssignmentsRequestBuilderGetQueryParameters{
	Top: &requestTop,
	Skip: &requestSkip,
}
configuration := &graphadmin.TeamsTelephoneNumberManagementNumberAssignmentsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
numberAssignments, err := graphClient.Admin().Teams().TelephoneNumberManagement().NumberAssignments().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.teamsadministration.NumberAssignmentCollectionResponse result = graphClient.admin().teams().telephoneNumberManagement().numberAssignments().get(requestConfiguration -> {
	requestConfiguration.queryParameters.top = 100;
	requestConfiguration.queryParameters.skip = 200;
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let numberAssignments = await client.api('/admin/teams/telephoneNumberManagement/numberAssignments')
	.skip(200)
	.top(100)
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Admin\Teams\TelephoneNumberManagement\NumberAssignments\NumberAssignmentsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new NumberAssignmentsRequestBuilderGetRequestConfiguration();
$queryParameters = NumberAssignmentsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->top = 100;
$queryParameters->skip = 200;
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->admin()->teams()->telephoneNumberManagement()->numberAssignments()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.admin.teams.telephone_number_management.number_assignments.number_assignments_request_builder import NumberAssignmentsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = NumberAssignmentsRequestBuilder.NumberAssignmentsRequestBuilderGetQueryParameters(
		top = 100,
		skip = 200,
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.admin.teams.telephone_number_management.number_assignments.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.teamsAdministration.numberAssignment",
    "id": "YmMyNjMyZTMtNzUwYy00N2Q3LWFlYWUtOWZlZTAzNWJjMGM3fCsxMjAyMzQ1Njc4OA",
    "telephoneNumber": "+112345",
    "operatorId": "7a205197-8e59-487d-b9fa-3fc1b108f1e5",
    "numberType": "directRouting",
    "activationState": "activated",
    "capabilities": [
      "conferenceAssignment",
        "voiceApplicationAssignment",
        "userAssignment"
    ],
    "locationId": null,
    "civicAddressId": null,
    "networkSiteId": null,
    "assignmentTargetId": "22ed44ab-7759-4649-818e-6af3242dbc5d",
    "assignmentCategory": "primary",
    "portInStatus": null,
    "assignmentStatus": "userAssigned",
    "isoCountryCode": null,
    "city": null,
    "numberSource": "online",
    "supportedCustomerActions": [
      "locationUpdate"
    ],
    "reverseNumberLookupOptions": []
  },
    "value": {
    "@odata.type": "#microsoft.graph.teamsAdministration.numberAssignment",
    "id": "YmMyNjMyZTMtNzUwYy00N2Q3LWFlYWUtOWZlZTAzNWJjMGM3fCsxMjAyMzQ1Njc4OQ",
    "telephoneNumber": "+12052582895",
    "operatorId": "0019adbc-b82a-47b4-a799-4e993a9982f1",
    "numberType": "callingPlan",
    "activationState": "activated",
    "capabilities": [
      "conferenceAssignment"
    ],
    "locationId": null,
    "civicAddressId": null,
    "networkSiteId": null,
    "assignmentTargetId": "207a6836-d031-4764-a9d8-c1193f455f21",
    "assignmentCategory": "primary",
    "portInStatus": null,
    "assignmentStatus": "conferenceAssigned",
    "isoCountryCode": "US",
    "city": "Clanton",
    "numberSource": "online",
    "supportedCustomerActions": [
      "locationUpdate",
       "release"
    ],
    "reverseNumberLookupOptions": []
  }
  
}
```

### Example 4

#### Request

The following example shows a request to get assignment details for a single telephone number using a filter.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [Python](#tabpanel_4_python)

```msgraph
GET https://graph.microsoft.com/v1.0/admin/teams/telephoneNumberManagement/numberAssignments?$filter=telephoneNumber eq '+12052582895'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Teams.TelephoneNumberManagement.NumberAssignments.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "telephoneNumber eq ' 12052582895'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphadmin "github.com/microsoftgraph/msgraph-sdk-go/admin"
	  //other-imports
)


requestFilter := "telephoneNumber eq ' 12052582895'"

requestParameters := &graphadmin.TeamsTelephoneNumberManagementNumberAssignmentsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphadmin.TeamsTelephoneNumberManagementNumberAssignmentsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
numberAssignments, err := graphClient.Admin().Teams().TelephoneNumberManagement().NumberAssignments().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.teamsadministration.NumberAssignmentCollectionResponse result = graphClient.admin().teams().telephoneNumberManagement().numberAssignments().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "telephoneNumber eq ' 12052582895'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let numberAssignments = await client.api('/admin/teams/telephoneNumberManagement/numberAssignments')
	.filter('telephoneNumber eq \' 12052582895\'')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Admin\Teams\TelephoneNumberManagement\NumberAssignments\NumberAssignmentsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new NumberAssignmentsRequestBuilderGetRequestConfiguration();
$queryParameters = NumberAssignmentsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "telephoneNumber eq ' 12052582895'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->admin()->teams()->telephoneNumberManagement()->numberAssignments()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.admin.teams.telephone_number_management.number_assignments.number_assignments_request_builder import NumberAssignmentsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = NumberAssignmentsRequestBuilder.NumberAssignmentsRequestBuilderGetQueryParameters(
		filter = "telephoneNumber eq ' 12052582895'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.admin.teams.telephone_number_management.number_assignments.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.teamsAdministration.numberAssignment",
    "id": "YmMyNjMyZTMtNzUwYy00N2Q3LWFlYWUtOWZlZTAzNWJjMGM3fCsxMjAzNDU2Nzcy",
    "telephoneNumber": "+12052582895",
    "operatorId": "7a205197-8e59-487d-b9fa-3fc1b108f1e5",
    "numberType": "directRouting",
    "activationState": "activated",
    "capabilities": [
        "voiceApplicationAssignment",
        "userAssignment"
    ],
    "locationId": null,
    "civicAddressId": null,
    "networkSiteId": null,
    "assignmentTargetId": null,
    "assignmentCategory": null,
    "portInStatus": null,
    "assignmentStatus": "unassigned",
    "isoCountryCode": null,
    "city": null,
    "numberSource": "online",
    "supportedCustomerActions": [
      "locationUpdate"
    ],
    "reverseNumberLookupOptions": []
  }
}
```
