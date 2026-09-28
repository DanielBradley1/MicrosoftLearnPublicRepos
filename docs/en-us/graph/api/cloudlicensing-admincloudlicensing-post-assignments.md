<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudlicensing-admincloudlicensing-post-assignments?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create assignment

Namespace: microsoft.graph.cloudLicensing

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new license [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) by posting to the **assignments** collection of an organization.

An assignment must always have a direct relationship to an allotment and to a user or group. If an assignment is created by posting to the central **assignments** collection located at `/admin/cloudLicensing/assignments`, both of those relationships must be established in the request body. Assignments can also be created by posting to the **assignments** collection of an allotment, the **assignments** collection of a user or the **assignments** collection of a group.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudLicensing.AssignLicenses | CloudLicensing.AssignLicenses.Organization, User-CloudLicensing.AssignLicenses, User-CloudLicensing.AssignLicenses.Organization, User.ReadWrite.All, Group-CloudLicensing.AssignLicenses, Group-CloudLicensing.AssignLicenses.Organization, Group.ReadWrite.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudLicensing.AssignLicenses.Organization | User-CloudLicensing.AssignLicenses.Organization, User.ReadWrite.All, Group-CloudLicensing.AssignLicenses.Organization, Group.ReadWrite.All, Directory.ReadWrite.All |

## HTTP request

```http
POST /admin/cloudLicensing/assignments
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) object.

You can specify the following properties when you create an **assignment**.

| Property | Type | Description |
| :--- | :--- | :--- |
| disabledServicePlanIds | GUID collection | The list of disabled service plans for this assignment. An empty list indicates that all services are enabled. Required. |

You can specify the following relationships when you create an **assignment**.

| Relationship | Type | Description |
| :--- | :--- | :--- |
| allotment | [microsoft.graph.cloudLicensing.allotment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-allotment?view=graph-rest-beta) | The allotment from which licenses are assigned. Required. |
| assignedTo | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) | The user or group to which licenses are assigned. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.cloudLicensing.assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/admin/cloudLicensing/assignments
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
  "allotment@odata.bind": "https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/rkocgef3dgjhnu3gmu2mqhbdbmwcymnf6fk3k6a7zbui5e7gfpmi",
  "assignedTo@odata.bind": "https://graph.microsoft.com/beta/users/6d645c5f-089f-40d8-b0e7-136fb5c56d5b",
  "disabledServicePlanIds": [
    "bed136c6-b799-4462-824d-fc045d3a9d25"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.CloudLicensing;

var requestBody = new Assignment
{
	OdataType = "#microsoft.graph.cloudLicensing.assignment",
	DisabledServicePlanIds = new List<Guid?>
	{
		Guid.Parse("bed136c6-b799-4462-824d-fc045d3a9d25"),
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"allotment@odata.bind" , "https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/rkocgef3dgjhnu3gmu2mqhbdbmwcymnf6fk3k6a7zbui5e7gfpmi"
		},
		{
			"assignedTo@odata.bind" , "https://graph.microsoft.com/beta/users/6d645c5f-089f-40d8-b0e7-136fb5c56d5b"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.CloudLicensing.Assignments.PostAsync(requestBody);
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
	  graphmodelscloudlicensing "github.com/microsoftgraph/msgraph-beta-sdk-go/models/cloudlicensing"
	  //other-imports
)

requestBody := graphmodelscloudlicensing.NewAssignment()
disabledServicePlanIds := []uuid.UUID {
	uuid.MustParse("bed136c6-b799-4462-824d-fc045d3a9d25"),
}
requestBody.SetDisabledServicePlanIds(disabledServicePlanIds)
additionalData := map[string]interface{}{
	"allotment@odata.bind" : "https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/rkocgef3dgjhnu3gmu2mqhbdbmwcymnf6fk3k6a7zbui5e7gfpmi", 
	"assignedTo@odata.bind" : "https://graph.microsoft.com/beta/users/6d645c5f-089f-40d8-b0e7-136fb5c56d5b", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignments, err := graphClient.Admin().CloudLicensing().Assignments().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.cloudlicensing.Assignment assignment = new com.microsoft.graph.beta.models.cloudlicensing.Assignment();
assignment.setOdataType("#microsoft.graph.cloudLicensing.assignment");
LinkedList<UUID> disabledServicePlanIds = new LinkedList<UUID>();
disabledServicePlanIds.add(UUID.fromString("bed136c6-b799-4462-824d-fc045d3a9d25"));
assignment.setDisabledServicePlanIds(disabledServicePlanIds);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("allotment@odata.bind", "https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/rkocgef3dgjhnu3gmu2mqhbdbmwcymnf6fk3k6a7zbui5e7gfpmi");
additionalData.put("assignedTo@odata.bind", "https://graph.microsoft.com/beta/users/6d645c5f-089f-40d8-b0e7-136fb5c56d5b");
assignment.setAdditionalData(additionalData);
com.microsoft.graph.models.cloudlicensing.Assignment result = graphClient.admin().cloudLicensing().assignments().post(assignment);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const assignment = {
  '@odata.type': '#microsoft.graph.cloudLicensing.assignment',
  'allotment@odata.bind': 'https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/rkocgef3dgjhnu3gmu2mqhbdbmwcymnf6fk3k6a7zbui5e7gfpmi',
  'assignedTo@odata.bind': 'https://graph.microsoft.com/beta/users/6d645c5f-089f-40d8-b0e7-136fb5c56d5b',
  disabledServicePlanIds: [
    'bed136c6-b799-4462-824d-fc045d3a9d25'
  ]
};

await client.api('/admin/cloudLicensing/assignments')
	.version('beta')
	.post(assignment);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\CloudLicensing\Assignment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Assignment();
$requestBody->setOdataType('#microsoft.graph.cloudLicensing.assignment');
$requestBody->setDisabledServicePlanIds(['bed136c6-b799-4462-824d-fc045d3a9d25', 	]);
$additionalData = [
	'allotment@odata.bind' => 'https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/rkocgef3dgjhnu3gmu2mqhbdbmwcymnf6fk3k6a7zbui5e7gfpmi',
	'assignedTo@odata.bind' => 'https://graph.microsoft.com/beta/users/6d645c5f-089f-40d8-b0e7-136fb5c56d5b',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->admin()->cloudLicensing()->assignments()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.cloud_licensing.assignment import Assignment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Assignment(
	odata_type = "#microsoft.graph.cloudLicensing.assignment",
	disabled_service_plan_ids = [
		UUID("bed136c6-b799-4462-824d-fc045d3a9d25"),
	],
	additional_data = {
			"allotment@odata_bind" : "https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/rkocgef3dgjhnu3gmu2mqhbdbmwcymnf6fk3k6a7zbui5e7gfpmi",
			"assigned_to@odata_bind" : "https://graph.microsoft.com/beta/users/6d645c5f-089f-40d8-b0e7-136fb5c56d5b",
	}
)

result = await graph_client.admin.cloud_licensing.assignments.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
  "id": "405ee855-dd74-f695-8d7e-be35a6788fe8",
  "disabledServicePlanIds": [
    "bed136c6-b799-4462-824d-fc045d3a9d25"
  ]
}
```
