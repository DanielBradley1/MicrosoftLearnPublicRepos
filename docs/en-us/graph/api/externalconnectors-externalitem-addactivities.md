<!-- Source: https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalitem-addactivities?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-31 -->

# externalItem: addActivities

Namespace: microsoft.graph.externalConnectors

Append additional instances of [externalActivity](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalactivity?view=graph-rest-1.0) objects on an [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ExternalItem.ReadWrite.OwnedBy | ExternalItem.ReadWrite.All |

## HTTP request

```http
POST external/connections/{connectionsId}/items/{externalItemId}/addActivities
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| activities | [microsoft.graph.externalConnectors.externalActivity](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalactivity?view=graph-rest-1.0) collection | Collection of activities that involve an **externalItem**. |

## Response

If successful, this action returns a `200 OK` response code and a collection of [microsoft.graph.externalConnectors.externalActivityResult](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalactivityresult?view=graph-rest-1.0) objects in the response body.

A `207 Multi-Status` response code indicates that only some of the added **externalActivity** instances were successfully processed. The caller should inspect the response payload, looking at the error field for each **externalActivityResult** to determine why the **externalActivity** instance was not processed and what action can be taken. A `null` **error** property indicates a successful **externalActivityResult**.

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
POST https://graph.microsoft.com/v1.0/external/connections/contosohr/items/TSP228082938/addActivities
Content-Type: application/json
Content-length: 190

{
  "activities": [
    {
      "@odata.type": "#microsoft.graph.externalConnectors.externalActivity",
      "type": "created",
      "startDateTime": "2021-04-06T18:04:31.033Z",
      "performedBy": {
        "type": "user",
        "id": "1f0c997e-99f7-43f1-8cca-086f8d42be8d"
      }
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.External.Connections.Item.Items.Item.MicrosoftGraphExternalConnectorsAddActivities;
using Microsoft.Graph.Models.ExternalConnectors;

var requestBody = new AddActivitiesPostRequestBody
{
	Activities = new List<ExternalActivity>
	{
		new ExternalActivity
		{
			OdataType = "#microsoft.graph.externalConnectors.externalActivity",
			Type = ExternalActivityType.Created,
			StartDateTime = DateTimeOffset.Parse("2021-04-06T18:04:31.033Z"),
			PerformedBy = new Identity
			{
				Type = IdentityType.User,
				Id = "1f0c997e-99f7-43f1-8cca-086f8d42be8d",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.Connections["{externalConnection-id}"].Items["{externalItem-id}"].MicrosoftGraphExternalConnectorsAddActivities.PostAsAddActivitiesPostResponseAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphexternal "github.com/microsoftgraph/msgraph-sdk-go/external"
	  graphmodelsexternalconnectors "github.com/microsoftgraph/msgraph-sdk-go/models/externalconnectors"
	  //other-imports
)

requestBody := graphexternal.NewAddActivitiesPostRequestBody()


externalActivity := graphmodelsexternalconnectors.NewExternalActivity()
type := graphmodels.CREATED_EXTERNALACTIVITYTYPE 
externalActivity.SetType(&type) 
startDateTime , err := time.Parse(time.RFC3339, "2021-04-06T18:04:31.033Z")
externalActivity.SetStartDateTime(&startDateTime) 
performedBy := graphmodelsexternalconnectors.NewIdentity()
type := graphmodels.USER_IDENTITYTYPE 
performedBy.SetType(&type) 
id := "1f0c997e-99f7-43f1-8cca-086f8d42be8d"
performedBy.SetId(&id) 
externalActivity.SetPerformedBy(performedBy)

activities := []graphmodelsexternalconnectors.ExternalActivityable {
	externalActivity,
}
requestBody.SetActivities(activities)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
microsoftGraphExternalConnectorsAddActivities, err := graphClient.External().Connections().ByExternalConnectionId("externalConnection-id").Items().ByExternalItemId("externalItem-id").MicrosoftGraphExternalConnectorsAddActivities().PostAsAddActivitiesPostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.external.connections.item.items.item.microsoftgraphexternalconnectorsaddactivities.AddActivitiesPostRequestBody addActivitiesPostRequestBody = new com.microsoft.graph.external.connections.item.items.item.microsoftgraphexternalconnectorsaddactivities.AddActivitiesPostRequestBody();
LinkedList<com.microsoft.graph.models.externalconnectors.ExternalActivity> activities = new LinkedList<com.microsoft.graph.models.externalconnectors.ExternalActivity>();
com.microsoft.graph.models.externalconnectors.ExternalActivity externalActivity = new com.microsoft.graph.models.externalconnectors.ExternalActivity();
externalActivity.setOdataType("#microsoft.graph.externalConnectors.externalActivity");
externalActivity.setType(com.microsoft.graph.models.externalconnectors.ExternalActivityType.Created);
OffsetDateTime startDateTime = OffsetDateTime.parse("2021-04-06T18:04:31.033Z");
externalActivity.setStartDateTime(startDateTime);
com.microsoft.graph.models.externalconnectors.Identity performedBy = new com.microsoft.graph.models.externalconnectors.Identity();
performedBy.setType(com.microsoft.graph.models.externalconnectors.IdentityType.User);
performedBy.setId("1f0c997e-99f7-43f1-8cca-086f8d42be8d");
externalActivity.setPerformedBy(performedBy);
activities.add(externalActivity);
addActivitiesPostRequestBody.setActivities(activities);
var result = graphClient.external().connections().byExternalConnectionId("{externalConnection-id}").items().byExternalItemId("{externalItem-id}").microsoftGraphExternalConnectorsAddActivities().post(addActivitiesPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const externalActivityResult = {
  activities: [
    {
      '@odata.type': '#microsoft.graph.externalConnectors.externalActivity',
      type: 'created',
      startDateTime: '2021-04-06T18:04:31.033Z',
      performedBy: {
        type: 'user',
        id: '1f0c997e-99f7-43f1-8cca-086f8d42be8d'
      }
    }
  ]
};

await client.api('/external/connections/contosohr/items/TSP228082938/addActivities')
	.post(externalActivityResult);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\External\Connections\Item\Items\Item\MicrosoftGraphExternalConnectorsAddActivities\AddActivitiesPostRequestBody;
use Microsoft\Graph\Generated\Models\ExternalConnectors\ExternalActivity;
use Microsoft\Graph\Generated\Models\ExternalConnectors\ExternalActivityType;
use Microsoft\Graph\Generated\Models\ExternalConnectors\Identity;
use Microsoft\Graph\Generated\Models\ExternalConnectors\IdentityType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AddActivitiesPostRequestBody();
$activitiesExternalActivity1 = new ExternalActivity();
$activitiesExternalActivity1->setOdataType('#microsoft.graph.externalConnectors.externalActivity');
$activitiesExternalActivity1->setType(new ExternalActivityType('created'));
$activitiesExternalActivity1->setStartDateTime(new \DateTime('2021-04-06T18:04:31.033Z'));
$activitiesExternalActivity1PerformedBy = new Identity();
$activitiesExternalActivity1PerformedBy->setType(new IdentityType('user'));
$activitiesExternalActivity1PerformedBy->setId('1f0c997e-99f7-43f1-8cca-086f8d42be8d');
$activitiesExternalActivity1->setPerformedBy($activitiesExternalActivity1PerformedBy);
$activitiesArray []= $activitiesExternalActivity1;
$requestBody->setActivities($activitiesArray);


$result = $graphServiceClient->external()->connections()->byExternalConnectionId('externalConnection-id')->items()->byExternalItemId('externalItem-id')->microsoftGraphExternalConnectorsAddActivities()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Search

$params = @{
	activities = @(
		@{
			"@odata.type" = "#microsoft.graph.externalConnectors.externalActivity"
			type = "created"
			startDateTime = [System.DateTime]::Parse("2021-04-06T18:04:31.033Z")
			performedBy = @{
				type = "user"
				id = "1f0c997e-99f7-43f1-8cca-086f8d42be8d"
			}
		}
	)
}

Add-MgExternalConnectionItemActivity -ExternalConnectionId $externalConnectionId -ExternalItemId $externalItemId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.external.connections.item.items.item.microsoft_graph_external_connectors_add_activities.add_activities_post_request_body import AddActivitiesPostRequestBody
from msgraph.generated.models.external_connectors.external_activity import ExternalActivity
from msgraph.generated.models.external_activity_type import ExternalActivityType
from msgraph.generated.models.external_connectors.identity import Identity
from msgraph.generated.models.identity_type import IdentityType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AddActivitiesPostRequestBody(
	activities = [
		ExternalActivity(
			odata_type = "#microsoft.graph.externalConnectors.externalActivity",
			type = ExternalActivityType.Created,
			start_date_time = "2021-04-06T18:04:31.033Z",
			performed_by = Identity(
				type = IdentityType.User,
				id = "1f0c997e-99f7-43f1-8cca-086f8d42be8d",
			),
		),
	],
)

result = await graph_client.external.connections.by_external_connection_id('externalConnection-id').items.by_external_item_id('externalItem-id').microsoft_graph_external_connectors_add_activities.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.externalConnectors.externalActivityResult",
      "type": "created",
      "startDateTime": "2021-04-06T18:04:31.033Z",
      "error": null
    }
  ]
}
```
