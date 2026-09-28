<!-- Source: https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalconnection-put-items?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-15 -->

# Create externalItem

Namespace: microsoft.graph.externalConnectors

Create a new [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0) object.

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

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0) object. The payload is limited to 30 MB.

You can specify the following properties when creating an [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The item ID. Required. |
| properties | [microsoft.graph.externalConnectors.properties](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-properties?view=graph-rest-1.0) | The item properties. The `properties` object must contain at least one property. All `DateTime` type properties must be in ISO 8601 format. Required. |
| content | [microsoft.graph.externalConnectors.externalItemContent](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitemcontent?view=graph-rest-1.0) | The external item content. Optional. |
| acl | [microsoft.graph.externalConnectors.acl](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-acl?view=graph-rest-1.0) collection | The access control list. Required. |

Properties on an `externalItem` should use type specifiers in the payload in the following scenarios:

- For `String` type properties, if the value contains non-ASCII characters.

  ```json
  "description@odata.type": "String",
  "description": "Kandierte Äpfel"
  ```

- For all collection types.

  ```json
  "categories@odata.type": "Collection(String)"
  "categories": [
    "red",
    "blue"
  ]
  ```


  Important


  When including a property of type `Collection(DateTime)`, you must use the type specifier `Collection(DateTimeOffset)`.

## Response

If successful, this method returns `200 OK` response code.

## Examples

### Example: Create a custom item

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
Content-type: application/json

{
  "acl": [
    {
      "type": "user",
      "value": "e811976d-83df-4cbd-8b9b-5215b18aa874",
      "accessType": "grant"
    },
    {
      "type": "externalGroup",
      "value": "14m1b9c38qe647f6a",
      "accessType": "deny"
    }
  ],
  "properties": {
    "title": "Error in the payment gateway",
    "priority": 1,
    "assignee": "john@contoso.com"
  },
  "content": {
    "value": "Error in payment gateway...",
    "type": "text"
  }
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
			Type = AclType.User,
			Value = "e811976d-83df-4cbd-8b9b-5215b18aa874",
			AccessType = AccessType.Grant,
		},
		new Acl
		{
			Type = AclType.ExternalGroup,
			Value = "14m1b9c38qe647f6a",
			AccessType = AccessType.Deny,
		},
	},
	Properties = new Properties
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"title" , "Error in the payment gateway"
			},
			{
				"priority" , 1
			},
			{
				"assignee" , "john@contoso.com"
			},
		},
	},
	Content = new ExternalItemContent
	{
		Value = "Error in payment gateway...",
		Type = ExternalItemContentType.Text,
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
type := graphmodels.USER_ACLTYPE 
acl.SetType(&type) 
value := "e811976d-83df-4cbd-8b9b-5215b18aa874"
acl.SetValue(&value) 
accessType := graphmodels.GRANT_ACCESSTYPE 
acl.SetAccessType(&accessType) 
acl1 := graphmodelsexternalconnectors.NewAcl()
type := graphmodels.EXTERNALGROUP_ACLTYPE 
acl1.SetType(&type) 
value := "14m1b9c38qe647f6a"
acl1.SetValue(&value) 
accessType := graphmodels.DENY_ACCESSTYPE 
acl1.SetAccessType(&accessType) 

acl := []graphmodelsexternalconnectors.Aclable {
	acl,
	acl1,
}
requestBody.SetAcl(acl)
properties := graphmodelsexternalconnectors.NewProperties()
additionalData := map[string]interface{}{
	"title" : "Error in the payment gateway", 
	"priority" : int32(1) , 
	"assignee" : "john@contoso.com", 
}
properties.SetAdditionalData(additionalData)
requestBody.SetProperties(properties)
content := graphmodelsexternalconnectors.NewExternalItemContent()
value := "Error in payment gateway..."
content.SetValue(&value) 
type := graphmodels.TEXT_EXTERNALITEMCONTENTTYPE 
content.SetType(&type) 
requestBody.SetContent(content)

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
acl1.setType(com.microsoft.graph.models.externalconnectors.AclType.User);
acl1.setValue("e811976d-83df-4cbd-8b9b-5215b18aa874");
acl1.setAccessType(com.microsoft.graph.models.externalconnectors.AccessType.Grant);
acl.add(acl1);
com.microsoft.graph.models.externalconnectors.Acl acl2 = new com.microsoft.graph.models.externalconnectors.Acl();
acl2.setType(com.microsoft.graph.models.externalconnectors.AclType.ExternalGroup);
acl2.setValue("14m1b9c38qe647f6a");
acl2.setAccessType(com.microsoft.graph.models.externalconnectors.AccessType.Deny);
acl.add(acl2);
externalItem.setAcl(acl);
com.microsoft.graph.models.externalconnectors.Properties properties = new com.microsoft.graph.models.externalconnectors.Properties();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("title", "Error in the payment gateway");
additionalData.put("priority", 1);
additionalData.put("assignee", "john@contoso.com");
properties.setAdditionalData(additionalData);
externalItem.setProperties(properties);
com.microsoft.graph.models.externalconnectors.ExternalItemContent content = new com.microsoft.graph.models.externalconnectors.ExternalItemContent();
content.setValue("Error in payment gateway...");
content.setType(com.microsoft.graph.models.externalconnectors.ExternalItemContentType.Text);
externalItem.setContent(content);
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
      type: 'user',
      value: 'e811976d-83df-4cbd-8b9b-5215b18aa874',
      accessType: 'grant'
    },
    {
      type: 'externalGroup',
      value: '14m1b9c38qe647f6a',
      accessType: 'deny'
    }
  ],
  properties: {
    title: 'Error in the payment gateway',
    priority: 1,
    assignee: 'john@contoso.com'
  },
  content: {
    value: 'Error in payment gateway...',
    type: 'text'
  }
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
use Microsoft\Graph\Generated\Models\ExternalConnectors\Properties;
use Microsoft\Graph\Generated\Models\ExternalConnectors\ExternalItemContent;
use Microsoft\Graph\Generated\Models\ExternalConnectors\ExternalItemContentType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExternalItem();
$aclAcl1 = new Acl();
$aclAcl1->setType(new AclType('user'));
$aclAcl1->setValue('e811976d-83df-4cbd-8b9b-5215b18aa874');
$aclAcl1->setAccessType(new AccessType('grant'));
$aclArray []= $aclAcl1;
$aclAcl2 = new Acl();
$aclAcl2->setType(new AclType('externalGroup'));
$aclAcl2->setValue('14m1b9c38qe647f6a');
$aclAcl2->setAccessType(new AccessType('deny'));
$aclArray []= $aclAcl2;
$requestBody->setAcl($aclArray);

$properties = new Properties();
$additionalData = [
'title' => 'Error in the payment gateway',
'priority' => 1,
'assignee' => 'john@contoso.com',
];
$properties->setAdditionalData($additionalData);
$requestBody->setProperties($properties);
$content = new ExternalItemContent();
$content->setValue('Error in payment gateway...');
$content->setType(new ExternalItemContentType('text'));
$requestBody->setContent($content);

$result = $graphServiceClient->external()->connections()->byExternalConnectionId('externalConnection-id')->items()->byExternalItemId('externalItem-id')->put($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Search

$params = @{
	acl = @(
		@{
			type = "user"
			value = "e811976d-83df-4cbd-8b9b-5215b18aa874"
			accessType = "grant"
		}
		@{
			type = "externalGroup"
			value = "14m1b9c38qe647f6a"
			accessType = "deny"
		}
	)
	properties = @{
		title = "Error in the payment gateway"
		priority = 
		assignee = "john@contoso.com"
	}
	content = @{
		value = "Error in payment gateway..."
		type = "text"
	}
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
from msgraph.generated.models.external_connectors.properties import Properties
from msgraph.generated.models.external_connectors.external_item_content import ExternalItemContent
from msgraph.generated.models.external_item_content_type import ExternalItemContentType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExternalItem(
	acl = [
		Acl(
			type = AclType.User,
			value = "e811976d-83df-4cbd-8b9b-5215b18aa874",
			access_type = AccessType.Grant,
		),
		Acl(
			type = AclType.ExternalGroup,
			value = "14m1b9c38qe647f6a",
			access_type = AccessType.Deny,
		),
	],
	properties = Properties(
		additional_data = {
				"title" : "Error in the payment gateway",
				"priority" : 1,
				"assignee" : "john@contoso.com",
		}
	),
	content = ExternalItemContent(
		value = "Error in payment gateway...",
		type = ExternalItemContentType.Text,
	),
)

result = await graph_client.external.connections.by_external_connection_id('externalConnection-id').items.by_external_item_id('externalItem-id').put(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
```
