<!-- Source: https://learn.microsoft.com/en-us/graph/api/plannerroster-assignsensitivitylabel?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-11 -->

# plannerRoster: assignSensitivityLabel

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Assign a sensitivity label to a [plannerRoster](https://learn.microsoft.com/en-us/graph/api/resources/plannerroster?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Tasks.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Tasks.ReadWrite.All | Not available. |

## HTTP request

```http
POST /planner/rosters/{rosterId}/assignSensitivityLabel
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| If-Match | If-match: {etag}. Last known ETag value for the **plannerRoster** to be updated. Required. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| assignmentMethod | [sensitivityLabelAssignmentMethod](https://learn.microsoft.com/en-us/graph/api/resources/sensitivitylabelassignment?view=graph-rest-beta#sensitivitylabelassignmentmethod-values) | The method that is used to apply the sensitivity label to the roster. The possible values are: `standard`, `privileged`, `auto`, `unknownFutureValue`. |
| sensitivityLabelId | String | The ID of the label that's applied to the roster. |

## Response

If successful, this method returns a `200 OK` response code and a [plannerRoster](https://learn.microsoft.com/en-us/graph/api/resources/plannerroster?view=graph-rest-beta) object in the response body.

This method fails in the following situations, each with a respective response code. The **code** property in the error response indicates the specific error.

| Response code | Description | Code property value |
| :--- | :--- | :--- |
| `400 Bad Request` | If the label has sublabels, it can't be applied to the roster. Only labels without sublabels can be applied. The request fails. | `sensitivityLabelHasSublabels` |
| `403 Forbidden` | If labels are mandatory for the user and the user tries to remove the sensitivity label, the request fails. | `sensitivityLabelsAreMandatory` |
| `403 Forbidden` | If a previously existing label assignment was applied with `sensitivityLabelAssignmentMethod.privileged` and an app attempts to overwrite the label with `sensitivityLabelAssignmentMethod.standard`, the request fails. | `existingSensitivityLabelWasAppliedWithPrivilegedMethod` |
| `404 Not Found` | If a label can't be found or the label isn't in scope for the user, the request fails. | `sensitivityLabelNotFound` |

For more information, see [Microsoft Graph error responses and resource types](https://learn.microsoft.com/en-us/graph/errors).

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
POST https://graph.microsoft.com/beta/planner/rosters/3e34de02-b01d-423b-b2ae-ca0ccd1fab05/assignSensitivityLabel
Content-type: application/json
If-Match: "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc=\""

{
    "assignmentMethod" : "standard",
    "sensitivityLabelId": "7a4d7cc1-f72b-46a3-9831-02680eaf56f9"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Planner.Rosters.Item.AssignSensitivityLabel;
using Microsoft.Graph.Beta.Models;

var requestBody = new AssignSensitivityLabelPostRequestBody
{
	AssignmentMethod = SensitivityLabelAssignmentMethod.Standard,
	SensitivityLabelId = "7a4d7cc1-f72b-46a3-9831-02680eaf56f9",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Planner.Rosters["{plannerRoster-id}"].AssignSensitivityLabel.PostAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("If-Match", "\"W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc=\"\"");
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
	  graphplanner "github.com/microsoftgraph/msgraph-beta-sdk-go/planner"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("If-Match", "\"W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc=\"\"")

configuration := &graphplanner.RostersItemAssignSensitivityLabelRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphplanner.NewAssignSensitivityLabelPostRequestBody()
assignmentMethod := graphmodels.STANDARD_SENSITIVITYLABELASSIGNMENTMETHOD 
requestBody.SetAssignmentMethod(&assignmentMethod) 
sensitivityLabelId := "7a4d7cc1-f72b-46a3-9831-02680eaf56f9"
requestBody.SetSensitivityLabelId(&sensitivityLabelId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignSensitivityLabel, err := graphClient.Planner().Rosters().ByPlannerRosterId("plannerRoster-id").AssignSensitivityLabel().Post(context.Background(), requestBody, configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.planner.rosters.item.assignsensitivitylabel.AssignSensitivityLabelPostRequestBody assignSensitivityLabelPostRequestBody = new com.microsoft.graph.beta.planner.rosters.item.assignsensitivitylabel.AssignSensitivityLabelPostRequestBody();
assignSensitivityLabelPostRequestBody.setAssignmentMethod(SensitivityLabelAssignmentMethod.Standard);
assignSensitivityLabelPostRequestBody.setSensitivityLabelId("7a4d7cc1-f72b-46a3-9831-02680eaf56f9");
var result = graphClient.planner().rosters().byPlannerRosterId("{plannerRoster-id}").assignSensitivityLabel().post(assignSensitivityLabelPostRequestBody, requestConfiguration -> {
	requestConfiguration.headers.add("If-Match", "\"W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc=\"\"");
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

const plannerRoster = {
    assignmentMethod: 'standard',
    sensitivityLabelId: '7a4d7cc1-f72b-46a3-9831-02680eaf56f9'
};

await client.api('/planner/rosters/3e34de02-b01d-423b-b2ae-ca0ccd1fab05/assignSensitivityLabel')
	.version('beta')
	.post(plannerRoster);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Planner\Rosters\Item\AssignSensitivityLabel\AssignSensitivityLabelRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Beta\Generated\Planner\Rosters\Item\AssignSensitivityLabel\AssignSensitivityLabelPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\SensitivityLabelAssignmentMethod;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AssignSensitivityLabelPostRequestBody();
$requestBody->setAssignmentMethod(new SensitivityLabelAssignmentMethod('standard'));
$requestBody->setSensitivityLabelId('7a4d7cc1-f72b-46a3-9831-02680eaf56f9');
$requestConfiguration = new AssignSensitivityLabelRequestBuilderPostRequestConfiguration();
$headers = [
		'If-Match' => '"W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc=\""',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->planner()->rosters()->byPlannerRosterId('plannerRoster-id')->assignSensitivityLabel()->post($requestBody, $requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Planner

$params = @{
	assignmentMethod = "standard"
	sensitivityLabelId = "7a4d7cc1-f72b-46a3-9831-02680eaf56f9"
}

Set-MgBetaPlannerRosterSensitivityLabel -PlannerRosterId $plannerRosterId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.planner.rosters.item.assign_sensitivity_label.assign_sensitivity_label_request_builder import AssignSensitivityLabelRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph_beta.generated.planner.rosters.item.assign_sensitivity_label.assign_sensitivity_label_post_request_body import AssignSensitivityLabelPostRequestBody
from msgraph_beta.generated.models.sensitivity_label_assignment_method import SensitivityLabelAssignmentMethod
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AssignSensitivityLabelPostRequestBody(
	assignment_method = SensitivityLabelAssignmentMethod.Standard,
	sensitivity_label_id = "7a4d7cc1-f72b-46a3-9831-02680eaf56f9",
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("If-Match", "\"W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc=\"\"")


result = await graph_client.planner.rosters.by_planner_roster_id('plannerRoster-id').assign_sensitivity_label.post(request_body, request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response to the updated roster.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.plannerRoster",
  "id": "6519868f-868f-6519-8f86-19658f861965",
  "assignedSensitivityLabel": {
      "assignmentMethod" : "standard",
      "sensitivityLabelId": "720b42d7-d945-46cd-81f8-8dd825d01960",
      "tenantId": "88397d78-d160-4545-a01f-cceda28d3fe3"
  }
}
```
