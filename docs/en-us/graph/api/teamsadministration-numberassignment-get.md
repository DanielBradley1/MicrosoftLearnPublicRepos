<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamsadministration-numberassignment-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# Get numberAssignment

Namespace: microsoft.graph.teamsAdministration

Read the properties and relationships of [microsoft.graph.teamsAdministration.numberAssignment](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-numberassignment?view=graph-rest-1.0) object. This action retrieves all Microsoft Teams telephone numbers currently available within your tenant.

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
GET /admin/teams/telephoneNumberManagement/numberAssignments/{numberAssignmentId}
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.teamsAdministration.numberAssignment](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-numberassignment?view=graph-rest-1.0) object in the response body. The response body contains similar attributes found in Get-CsPhoneNumberAssignment Teams PowerShell cmdlet.

## Examples

### Request

The following request shows how to get assignment details for a single telephone number using the ID.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/admin/teams/telephoneNumberManagement/numberAssignments/YmMyNjMyZTMtNzUwYy00N2Q3LWFlYWUtOWZlZTAzNWJjMGM3fCsxMjAyMzQ1Njc4OQ
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Teams.TelephoneNumberManagement.NumberAssignments["{numberAssignment-id}"].GetAsync();
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
numberAssignments, err := graphClient.Admin().Teams().TelephoneNumberManagement().NumberAssignments().ByNumberAssignmentId("numberAssignment-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.teamsadministration.NumberAssignment result = graphClient.admin().teams().telephoneNumberManagement().numberAssignments().byNumberAssignmentId("{numberAssignment-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let numberAssignment = await client.api('/admin/teams/telephoneNumberManagement/numberAssignments/YmMyNjMyZTMtNzUwYy00N2Q3LWFlYWUtOWZlZTAzNWJjMGM3fCsxMjAyMzQ1Njc4OQ')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->admin()->teams()->telephoneNumberManagement()->numberAssignments()->byNumberAssignmentId('numberAssignment-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.admin.teams.telephone_number_management.number_assignments.by_number_assignment_id('numberAssignment-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.teamsAdministration.numberAssignment",
    "id": "YmMyNjMyZTMtNzUwYy00N2Q3LWFlYWUtOWZlZTAzNWJjMGM3fCsxMjAyMzQ1Njc4OQ",
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
  }  
}
```
