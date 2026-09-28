<!-- Source: https://learn.microsoft.com/en-us/graph/api/externalconnectors-schema-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# Update schema

Namespace: microsoft.graph.externalConnectors

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [schema](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-schema?view=graph-rest-beta) for an [externalConnection](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection?view=graph-rest-beta).

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
PATCH /external/connections/{connectionId}/schema
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| Prefer: respond-async | Use this to cause the request to execute asynchronously. Optional. |

## Request body

In the request body, supply a JSON representation of a [schema](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-schema?view=graph-rest-beta) object.

When you register a custom item schema, the **schema** object **must** have the **baseType** property set to `microsoft.graph.externalItem` and **must** contain the **properties** property. The **properties** object **must** contain at least one property, up to a maximum of 128.

## Response

If successful, this method returns a `202 Accepted` response code and a URL in the `Location` response header that can be used to [get the operation status](https://learn.microsoft.com/en-us/graph/api/externalconnectors-connectionoperation-get?view=graph-rest-beta).

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
PATCH https://graph.microsoft.com/beta/external/connections/contosohr/schema
Content-type: application/json

{
  "baseType": "microsoft.graph.externalItem",
  "properties": [
    {
      "name": "ticketTitle",
      "type": "string",
      "isSearchable": "true",
      "isRetrievable": "true",
      "labels": [
        "title"
      ]
    },
    {
      "name": "priority",
      "type": "string",
      "isQueryable": "true",
      "isRetrievable": "true",
      "isSearchable": "false"
    },
    {
      "name": "assignee",
      "type": "string",
      "isRetrievable": "true"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.ExternalConnectors;

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

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodelsexternalconnectors "github.com/microsoftgraph/msgraph-beta-sdk-go/models/externalconnectors"
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

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.externalconnectors.Schema schema = new com.microsoft.graph.beta.models.externalconnectors.Schema();
schema.setBaseType("microsoft.graph.externalItem");
LinkedList<com.microsoft.graph.beta.models.externalconnectors.Property> properties = new LinkedList<com.microsoft.graph.beta.models.externalconnectors.Property>();
com.microsoft.graph.beta.models.externalconnectors.Property property = new com.microsoft.graph.beta.models.externalconnectors.Property();
property.setName("ticketTitle");
property.setType(com.microsoft.graph.beta.models.externalconnectors.PropertyType.String);
property.setIsSearchable(true);
property.setIsRetrievable(true);
LinkedList<com.microsoft.graph.beta.models.externalconnectors.com.microsoft.graph.beta.models.externalconnectors.Label> labels = new LinkedList<com.microsoft.graph.beta.models.externalconnectors.com.microsoft.graph.beta.models.externalconnectors.Label>();
labels.add(com.microsoft.graph.beta.models.externalconnectors.Label.Title);
property.setLabels(labels);
properties.add(property);
com.microsoft.graph.beta.models.externalconnectors.Property property1 = new com.microsoft.graph.beta.models.externalconnectors.Property();
property1.setName("priority");
property1.setType(com.microsoft.graph.beta.models.externalconnectors.PropertyType.String);
property1.setIsQueryable(true);
property1.setIsRetrievable(true);
property1.setIsSearchable(false);
properties.add(property1);
com.microsoft.graph.beta.models.externalconnectors.Property property2 = new com.microsoft.graph.beta.models.externalconnectors.Property();
property2.setName("assignee");
property2.setType(com.microsoft.graph.beta.models.externalconnectors.PropertyType.String);
property2.setIsRetrievable(true);
properties.add(property2);
schema.setProperties(properties);
com.microsoft.graph.models.externalconnectors.Schema result = graphClient.external().connections().byExternalConnectionId("{externalConnection-id}").schema().patch(schema);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

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
      type: 'string',
      isSearchable: 'true',
      isRetrievable: 'true',
      labels: [
        'title'
      ]
    },
    {
      name: 'priority',
      type: 'string',
      isQueryable: 'true',
      isRetrievable: 'true',
      isSearchable: 'false'
    },
    {
      name: 'assignee',
      type: 'string',
      isRetrievable: 'true'
    }
  ]
};

await client.api('/external/connections/contosohr/schema')
	.version('beta')
	.update(schema);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\ExternalConnectors\Schema;
use Microsoft\Graph\Beta\Generated\Models\ExternalConnectors\Property;
use Microsoft\Graph\Beta\Generated\Models\ExternalConnectors\PropertyType;
use Microsoft\Graph\Beta\Generated\Models\ExternalConnectors\Label;


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

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Search

$params = @{
	baseType = "microsoft.graph.externalItem"
	properties = @(
		@{
			name = "ticketTitle"
			type = "string"
			isSearchable = "true"
			isRetrievable = "true"
			labels = @(
			"title"
		)
	}
	@{
		name = "priority"
		type = "string"
		isQueryable = "true"
		isRetrievable = "true"
		isSearchable = "false"
	}
	@{
		name = "assignee"
		type = "string"
		isRetrievable = "true"
	}
)
}

Update-MgBetaExternalConnectionSchema -ExternalConnectionId $externalConnectionId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.external_connectors.schema import Schema
from msgraph_beta.generated.models.external_connectors.property import Property
from msgraph_beta.generated.models.property_type import PropertyType
from msgraph_beta.generated.models.external_connectors.label import Label
from msgraph_beta.generated.models.label import Label
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

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
Location: https://graph.microsoft.com/beta/external/connections/contosohr/operations/616bfeed-666f-4ce0-8cd9-058939010bfc
```
