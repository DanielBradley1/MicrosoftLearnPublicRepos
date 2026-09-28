<!-- Source: https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalconnection-patch-schema?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create or update schema

Namespace: microsoft.graph.externalConnectors

Create a new or update an existing [schema](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-schema?view=graph-rest-1.0) for a Microsoft Search [connection](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ExternalConnection.ReadWrite.OwnedBy | ExternalConnection.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ExternalConnection.ReadWrite.OwnedBy | ExternalConnection.ReadWrite.All |

## HTTP request

```http
PATCH /external/connections/{id}/schema
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a [schema](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-schema?view=graph-rest-1.0) object.

When you register a custom item schema, the **schema** object **must** have the **baseType** property set to `microsoft.graph.externalItem` and **must** contain the **properties** property. The **properties** object **must** contain at least one property, up to a maximum of 128.

## Response

If successful, this method returns a `202 Accepted` response code and a URL in the `Location` response header that can be used to [get the operation status](https://learn.microsoft.com/en-us/graph/api/externalconnectors-connectionoperation-get?view=graph-rest-1.0).

> **Note:** It can take between 5 and 15 minutes for the schema to be created. We recommend that you use the URL in the `Location` response header to get the operation status.

## Examples

### Request

The following example shows a request to register a new or update an existing custom schema asynchronously.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/external/connections/contosohr/schema
Content-type: application/json

{
  "baseType": "microsoft.graph.externalItem",
  "properties": [
    {
      "name": "ticketTitle",
      "type": "String",
      "isSearchable": "true",
      "isRetrievable": "true",
      "labels": [
        "title"
      ]
    },
    {
      "name": "priority",
      "type": "String",
      "isQueryable": "true",
      "isRetrievable": "true",
      "isSearchable": "false"
    },
    {
      "name": "assignee",
      "type": "String",
      "isRetrievable": "true"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.ExternalConnectors;

var requestBody = new Schema
{
	BaseType = "microsoft.graph.externalItem",
	Properties = new List<Property>
	{
		new Property
		{
			Name = "ticketTitle",
			Type = PropertyType.String,
			IsSearchable = true,
			IsRetrievable = true,
			Labels = new List<Label?>
			{
				Label.Title,
			},
		},
		new Property
		{
			Name = "priority",
			Type = PropertyType.String,
			IsQueryable = true,
			IsRetrievable = true,
			IsSearchable = false,
		},
		new Property
		{
			Name = "assignee",
			Type = PropertyType.String,
			IsRetrievable = true,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.Connections["{externalConnection-id}"].Schema.PatchAsync(requestBody);
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

requestBody := graphmodelsexternalconnectors.NewSchema()
baseType := "microsoft.graph.externalItem"
requestBody.SetBaseType(&baseType) 


property := graphmodelsexternalconnectors.NewProperty()
name := "ticketTitle"
property.SetName(&name) 
type := graphmodels.STRING_PROPERTYTYPE 
property.SetType(&type) 
isSearchable := true
property.SetIsSearchable(&isSearchable) 
isRetrievable := true
property.SetIsRetrievable(&isRetrievable) 
labels := []graphmodelsexternalconnectors.Labelable {
	label := graphmodels.TITLE_LABEL 
	property.SetLabel(&label)
}
property.SetLabels(labels)
property1 := graphmodelsexternalconnectors.NewProperty()
name := "priority"
property1.SetName(&name) 
type := graphmodels.STRING_PROPERTYTYPE 
property1.SetType(&type) 
isQueryable := true
property1.SetIsQueryable(&isQueryable) 
isRetrievable := true
property1.SetIsRetrievable(&isRetrievable) 
isSearchable := false
property1.SetIsSearchable(&isSearchable) 
property2 := graphmodelsexternalconnectors.NewProperty()
name := "assignee"
property2.SetName(&name) 
type := graphmodels.STRING_PROPERTYTYPE 
property2.SetType(&type) 
isRetrievable := true
property2.SetIsRetrievable(&isRetrievable) 

properties := []graphmodelsexternalconnectors.Propertyable {
	property,
	property1,
	property2,
}
requestBody.SetProperties(properties)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
schema, err := graphClient.External().Connections().ByExternalConnectionId("externalConnection-id").Schema().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.externalconnectors.Schema schema = new com.microsoft.graph.models.externalconnectors.Schema();
schema.setBaseType("microsoft.graph.externalItem");
LinkedList<com.microsoft.graph.models.externalconnectors.Property> properties = new LinkedList<com.microsoft.graph.models.externalconnectors.Property>();
com.microsoft.graph.models.externalconnectors.Property property = new com.microsoft.graph.models.externalconnectors.Property();
property.setName("ticketTitle");
property.setType(com.microsoft.graph.models.externalconnectors.PropertyType.String);
property.setIsSearchable(true);
property.setIsRetrievable(true);
LinkedList<com.microsoft.graph.models.externalconnectors.com.microsoft.graph.models.externalconnectors.Label> labels = new LinkedList<com.microsoft.graph.models.externalconnectors.com.microsoft.graph.models.externalconnectors.Label>();
labels.add(com.microsoft.graph.models.externalconnectors.Label.Title);
property.setLabels(labels);
properties.add(property);
com.microsoft.graph.models.externalconnectors.Property property1 = new com.microsoft.graph.models.externalconnectors.Property();
property1.setName("priority");
property1.setType(com.microsoft.graph.models.externalconnectors.PropertyType.String);
property1.setIsQueryable(true);
property1.setIsRetrievable(true);
property1.setIsSearchable(false);
properties.add(property1);
com.microsoft.graph.models.externalconnectors.Property property2 = new com.microsoft.graph.models.externalconnectors.Property();
property2.setName("assignee");
property2.setType(com.microsoft.graph.models.externalconnectors.PropertyType.String);
property2.setIsRetrievable(true);
properties.add(property2);
schema.setProperties(properties);
com.microsoft.graph.models.externalconnectors.Schema result = graphClient.external().connections().byExternalConnectionId("{externalConnection-id}").schema().patch(schema);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const schema = {
  baseType: 'microsoft.graph.externalItem',
  properties: [
    {
      name: 'ticketTitle',
      type: 'String',
      isSearchable: 'true',
      isRetrievable: 'true',
      labels: [
        'title'
      ]
    },
    {
      name: 'priority',
      type: 'String',
      isQueryable: 'true',
      isRetrievable: 'true',
      isSearchable: 'false'
    },
    {
      name: 'assignee',
      type: 'String',
      isRetrievable: 'true'
    }
  ]
};

await client.api('/external/connections/contosohr/schema')
	.update(schema);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ExternalConnectors\Schema;
use Microsoft\Graph\Generated\Models\ExternalConnectors\Property;
use Microsoft\Graph\Generated\Models\ExternalConnectors\PropertyType;
use Microsoft\Graph\Generated\Models\ExternalConnectors\Label;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Schema();
$requestBody->setBaseType('microsoft.graph.externalItem');
$propertiesProperty1 = new Property();
$propertiesProperty1->setName('ticketTitle');
$propertiesProperty1->setType(new PropertyType('string'));
$propertiesProperty1->setIsSearchable(true);
$propertiesProperty1->setIsRetrievable(true);
$propertiesProperty1->setLabels([new Label('title'),	]);
$propertiesArray []= $propertiesProperty1;
$propertiesProperty2 = new Property();
$propertiesProperty2->setName('priority');
$propertiesProperty2->setType(new PropertyType('string'));
$propertiesProperty2->setIsQueryable(true);
$propertiesProperty2->setIsRetrievable(true);
$propertiesProperty2->setIsSearchable(false);
$propertiesArray []= $propertiesProperty2;
$propertiesProperty3 = new Property();
$propertiesProperty3->setName('assignee');
$propertiesProperty3->setType(new PropertyType('string'));
$propertiesProperty3->setIsRetrievable(true);
$propertiesArray []= $propertiesProperty3;
$requestBody->setProperties($propertiesArray);


$result = $graphServiceClient->external()->connections()->byExternalConnectionId('externalConnection-id')->schema()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Search

$params = @{
	baseType = "microsoft.graph.externalItem"
	properties = @(
		@{
			name = "ticketTitle"
			type = "String"
			isSearchable = "true"
			isRetrievable = "true"
			labels = @(
			"title"
		)
	}
	@{
		name = "priority"
		type = "String"
		isQueryable = "true"
		isRetrievable = "true"
		isSearchable = "false"
	}
	@{
		name = "assignee"
		type = "String"
		isRetrievable = "true"
	}
)
}

Update-MgExternalConnectionSchema -ExternalConnectionId $externalConnectionId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.external_connectors.schema import Schema
from msgraph.generated.models.external_connectors.property import Property
from msgraph.generated.models.property_type import PropertyType
from msgraph.generated.models.external_connectors.label import Label
from msgraph.generated.models.label import Label
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Schema(
	base_type = "microsoft.graph.externalItem",
	properties = [
		Property_(
			name = "ticketTitle",
			type = PropertyType.String,
			is_searchable = True,
			is_retrievable = True,
			labels = [
				Label.Title,
			],
		),
		Property_(
			name = "priority",
			type = PropertyType.String,
			is_queryable = True,
			is_retrievable = True,
			is_searchable = False,
		),
		Property_(
			name = "assignee",
			type = PropertyType.String,
			is_retrievable = True,
		),
	],
)

result = await graph_client.external.connections.by_external_connection_id('externalConnection-id').schema.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
Location: https://graph.microsoft.com/v1.0/external/connections/contosohr/operations/616bfeed-666f-4ce0-8cd9-058939010bfc
```
