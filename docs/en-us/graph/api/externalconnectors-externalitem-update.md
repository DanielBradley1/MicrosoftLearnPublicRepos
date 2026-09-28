<!-- Source: https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalitem-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-14 -->

# Update externalItem

Namespace: microsoft.graph.externalConnectors

Update the properties of an [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ExternalItem.ReadWrite.OwnedBy | ExternalItem.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ExternalItem.ReadWrite.OwnedBy | ExternalItem.ReadWrite.All |

## HTTP request

```http
PUT /external/connections/{connection-id}/items/{item-id}
```

## Path parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |
| connection-id | string | The `id` property of the containing [externalConnection](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection?view=graph-rest-1.0) |
| item-id | string | The developer-provided `id` property of the [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0). |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties \(excluding properties inside the `properties` object\) that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance, don't include existing values that haven't changed. The following properties can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| acl | [microsoft.graph.externalConnectors.acl](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-acl?view=graph-rest-1.0) collection | An array of access control entries. Each entry specifies the access granted to a user or group. |
| content | [microsoft.graph.externalConnectors.externalItemContent](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitemcontent?view=graph-rest-1.0) | A plain-text representation of the contents of the item. The text in this property is full-text indexed. |
| properties | Object | A property bag with the properties of the item. The properties MUST conform to the [schema](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-schema?view=graph-rest-1.0) defined for the [externalConnection](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection?view=graph-rest-1.0). |

### Updating the acl collection

If the `acl` property is included in an update request, the existing ACL collection is overwritten with the collection included in the request.

### Updating the properties object

If the `properties` property is included in an update request, the existing property bag is overwritten with the value included in the request.

## Response

If successful, this method returns a `200 OK` response code and an updated [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0) object in the response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PUT https://graph.microsoft.com/v1.0/external/connections/contosohr/items/TSP228082938
Content-Type: application/json

{
  "acl": [
    {
      "type": "everyone",
      "value": "67a141d8-cf4e-4528-ba07-bed21bfacd2d",
      "accessType": "grant"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.ExternalConnectors;

var requestBody = new ExternalItem
{
	Acl = new List<Acl>
	{
		new Acl
		{
			Type = AclType.Everyone,
			Value = "67a141d8-cf4e-4528-ba07-bed21bfacd2d",
			AccessType = AccessType.Grant,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.Connections["{externalConnection-id}"].Items["{externalItem-id}"].PutAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelsexternalconnectors "github.com/microsoftgraph/msgraph-sdk-go/models/externalconnectors"
	  //other-imports
)

requestBody := graphmodelsexternalconnectors.NewExternalItem()


acl := graphmodelsexternalconnectors.NewAcl()
type := graphmodels.EVERYONE_ACLTYPE 
acl.SetType(&type) 
value := "67a141d8-cf4e-4528-ba07-bed21bfacd2d"
acl.SetValue(&value) 
accessType := graphmodels.GRANT_ACCESSTYPE 
acl.SetAccessType(&accessType) 

acl := []graphmodelsexternalconnectors.Aclable {
	acl,
}
requestBody.SetAcl(acl)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
items, err := graphClient.External().Connections().ByExternalConnectionId("externalConnection-id").Items().ByExternalItemId("externalItem-id").Put(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.externalconnectors.ExternalItem externalItem = new com.microsoft.graph.models.externalconnectors.ExternalItem();
LinkedList<com.microsoft.graph.models.externalconnectors.Acl> acl = new LinkedList<com.microsoft.graph.models.externalconnectors.Acl>();
com.microsoft.graph.models.externalconnectors.Acl acl1 = new com.microsoft.graph.models.externalconnectors.Acl();
acl1.setType(com.microsoft.graph.models.externalconnectors.AclType.Everyone);
acl1.setValue("67a141d8-cf4e-4528-ba07-bed21bfacd2d");
acl1.setAccessType(com.microsoft.graph.models.externalconnectors.AccessType.Grant);
acl.add(acl1);
externalItem.setAcl(acl);
com.microsoft.graph.models.externalconnectors.ExternalItem result = graphClient.external().connections().byExternalConnectionId("{externalConnection-id}").items().byExternalItemId("{externalItem-id}").put(externalItem);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const externalItem = {
  acl: [
    {
      type: 'everyone',
      value: '67a141d8-cf4e-4528-ba07-bed21bfacd2d',
      accessType: 'grant'
    }
  ]
};

await client.api('/external/connections/contosohr/items/TSP228082938')
	.put(externalItem);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ExternalConnectors\ExternalItem;
use Microsoft\Graph\Generated\Models\ExternalConnectors\Acl;
use Microsoft\Graph\Generated\Models\ExternalConnectors\AclType;
use Microsoft\Graph\Generated\Models\ExternalConnectors\AccessType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExternalItem();
$aclAcl1 = new Acl();
$aclAcl1->setType(new AclType('everyone'));
$aclAcl1->setValue('67a141d8-cf4e-4528-ba07-bed21bfacd2d');
$aclAcl1->setAccessType(new AccessType('grant'));
$aclArray []= $aclAcl1;
$requestBody->setAcl($aclArray);


$result = $graphServiceClient->external()->connections()->byExternalConnectionId('externalConnection-id')->items()->byExternalItemId('externalItem-id')->put($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Search

$params = @{
	acl = @(
		@{
			type = "everyone"
			value = "67a141d8-cf4e-4528-ba07-bed21bfacd2d"
			accessType = "grant"
		}
	)
}

Set-MgExternalConnectionItem -ExternalConnectionId $externalConnectionId -ExternalItemId $externalItemId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.external_connectors.external_item import ExternalItem
from msgraph.generated.models.external_connectors.acl import Acl
from msgraph.generated.models.acl_type import AclType
from msgraph.generated.models.access_type import AccessType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExternalItem(
	acl = [
		Acl(
			type = AclType.Everyone,
			value = "67a141d8-cf4e-4528-ba07-bed21bfacd2d",
			access_type = AccessType.Grant,
		),
	],
)

result = await graph_client.external.connections.by_external_connection_id('externalConnection-id').items.by_external_item_id('externalItem-id').put(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "id": "TSP228082938",
  "acl": [
    {
      "type": "everyone",
      "value": "67a141d8-cf4e-4528-ba07-bed21bfacd2d",
      "accessType": "grant"
    }
  ],
  "properties": {
    "title": "Error in the payment gateway",
    "priority": 1,
    "assignee": "john@contoso.com"
  },
  "content": {
    "@odata.type": "microsoft.graph.externalConnectors.externalItemContent",
    "value": "<h1>Error in payment gateway</h1><p>Error details...</p>",
    "type": "html"
  }
}
```
