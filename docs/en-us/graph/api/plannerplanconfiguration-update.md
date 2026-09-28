<!-- Source: https://learn.microsoft.com/en-us/graph/api/plannerplanconfiguration-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# Update plannerPlanConfiguration

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [plannerPlanConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfiguration?view=graph-rest-beta) object and its [plannerPlanConfigurationLocalization](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfigurationlocalization?view=graph-rest-beta) collection for a [businessScenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BusinessScenarioConfig.ReadWrite.OwnedBy | BusinessScenarioConfig.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BusinessScenarioConfig.ReadWrite.OwnedBy | Not available. |

## HTTP request

For the plan configuration based on a business scenario ID:

```http
PATCH /solutions/businessScenarios/{businessScenarioId}/planner/planConfiguration
```

For the plan configuration based on the unique name of a business scenario:

```http
PATCH /solutions/businessScenarios(uniqueName='{uniqueName}')/planner/planConfiguration
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultLanguage | String | The language that should be used for creating plans when no language has been specified. |
| buckets | [plannerPlanConfigurationBucketDefinition](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfigurationbucketdefinition?view=graph-rest-beta) collection | Buckets available in the plan. |
| localizations | [plannerPlanConfigurationLocalization](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfigurationlocalization?view=graph-rest-beta) collection | Localized names for the plan configuration. |

## Response

If successful, this method returns a `200 OK` response code and an updated [plannerPlanConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfiguration?view=graph-rest-beta) object in the response body.

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
PATCH https://graph.microsoft.com/beta/solutions/businessScenarios/c5d514e6c6864911ac46c720affb6e4d/planner/planConfiguration
Content-Type: application/json

{
  "defaultLanguage": "en-us",
  "buckets": [
    {
      "externalBucketId": "deliveryBucket"
    },
    {
      "externalBucketId": "storePickupBucket"
    },
    {
      "externalBucketId": "specialOrdersBucket"
    },
    {
      "externalBucketId": "returnProcessingBucket"
    }
  ],
  "localizations": [
    {
      "id": "en-us",
      "languageTag": "en-us",
      "planTitle": "Order Tracking",
      "buckets": [
        {
          "externalBucketId": "deliveryBucket",
          "name": "Deliveries"
        },
        {
          "externalBucketId": "storePickupBucket",
          "name": "Pickup"
        },
        {
          "externalBucketId": "specialOrdersBucket",
          "name": "Special Orders"
        },
        {
          "externalBucketId": "returnProcessingBucket",
          "name": "Customer Returns"
        }
      ]
    },
    {
      "id": "es-es",
      "languageTag": "es-es",
      "planTitle": "Seguimiento de pedidos",
      "buckets": [
        {
          "externalBucketId": "deliveryBucket",
          "name": "Entregas"
        },
        {
          "externalBucketId": "storePickupBucket",
          "name": "Recogida"
        },
        {
          "externalBucketId": "specialOrdersBucket",
          "name": "Pedidos especiales"
        },
        {
          "externalBucketId": "specialOrdersBucket",
          "name": "Devoluciones de clientes"
        }
      ]
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new PlannerPlanConfiguration
{
	DefaultLanguage = "en-us",
	Buckets = new List<PlannerPlanConfigurationBucketDefinition>
	{
		new PlannerPlanConfigurationBucketDefinition
		{
			ExternalBucketId = "deliveryBucket",
		},
		new PlannerPlanConfigurationBucketDefinition
		{
			ExternalBucketId = "storePickupBucket",
		},
		new PlannerPlanConfigurationBucketDefinition
		{
			ExternalBucketId = "specialOrdersBucket",
		},
		new PlannerPlanConfigurationBucketDefinition
		{
			ExternalBucketId = "returnProcessingBucket",
		},
	},
	Localizations = new List<PlannerPlanConfigurationLocalization>
	{
		new PlannerPlanConfigurationLocalization
		{
			Id = "en-us",
			LanguageTag = "en-us",
			PlanTitle = "Order Tracking",
			Buckets = new List<PlannerPlanConfigurationBucketLocalization>
			{
				new PlannerPlanConfigurationBucketLocalization
				{
					ExternalBucketId = "deliveryBucket",
					Name = "Deliveries",
				},
				new PlannerPlanConfigurationBucketLocalization
				{
					ExternalBucketId = "storePickupBucket",
					Name = "Pickup",
				},
				new PlannerPlanConfigurationBucketLocalization
				{
					ExternalBucketId = "specialOrdersBucket",
					Name = "Special Orders",
				},
				new PlannerPlanConfigurationBucketLocalization
				{
					ExternalBucketId = "returnProcessingBucket",
					Name = "Customer Returns",
				},
			},
		},
		new PlannerPlanConfigurationLocalization
		{
			Id = "es-es",
			LanguageTag = "es-es",
			PlanTitle = "Seguimiento de pedidos",
			Buckets = new List<PlannerPlanConfigurationBucketLocalization>
			{
				new PlannerPlanConfigurationBucketLocalization
				{
					ExternalBucketId = "deliveryBucket",
					Name = "Entregas",
				},
				new PlannerPlanConfigurationBucketLocalization
				{
					ExternalBucketId = "storePickupBucket",
					Name = "Recogida",
				},
				new PlannerPlanConfigurationBucketLocalization
				{
					ExternalBucketId = "specialOrdersBucket",
					Name = "Pedidos especiales",
				},
				new PlannerPlanConfigurationBucketLocalization
				{
					ExternalBucketId = "specialOrdersBucket",
					Name = "Devoluciones de clientes",
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BusinessScenarios["{businessScenario-id}"].Planner.PlanConfiguration.PatchAsync(requestBody);
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewPlannerPlanConfiguration()
defaultLanguage := "en-us"
requestBody.SetDefaultLanguage(&defaultLanguage) 


plannerPlanConfigurationBucketDefinition := graphmodels.NewPlannerPlanConfigurationBucketDefinition()
externalBucketId := "deliveryBucket"
plannerPlanConfigurationBucketDefinition.SetExternalBucketId(&externalBucketId) 
plannerPlanConfigurationBucketDefinition1 := graphmodels.NewPlannerPlanConfigurationBucketDefinition()
externalBucketId := "storePickupBucket"
plannerPlanConfigurationBucketDefinition1.SetExternalBucketId(&externalBucketId) 
plannerPlanConfigurationBucketDefinition2 := graphmodels.NewPlannerPlanConfigurationBucketDefinition()
externalBucketId := "specialOrdersBucket"
plannerPlanConfigurationBucketDefinition2.SetExternalBucketId(&externalBucketId) 
plannerPlanConfigurationBucketDefinition3 := graphmodels.NewPlannerPlanConfigurationBucketDefinition()
externalBucketId := "returnProcessingBucket"
plannerPlanConfigurationBucketDefinition3.SetExternalBucketId(&externalBucketId) 

buckets := []graphmodels.PlannerPlanConfigurationBucketDefinitionable {
	plannerPlanConfigurationBucketDefinition,
	plannerPlanConfigurationBucketDefinition1,
	plannerPlanConfigurationBucketDefinition2,
	plannerPlanConfigurationBucketDefinition3,
}
requestBody.SetBuckets(buckets)


plannerPlanConfigurationLocalization := graphmodels.NewPlannerPlanConfigurationLocalization()
id := "en-us"
plannerPlanConfigurationLocalization.SetId(&id) 
languageTag := "en-us"
plannerPlanConfigurationLocalization.SetLanguageTag(&languageTag) 
planTitle := "Order Tracking"
plannerPlanConfigurationLocalization.SetPlanTitle(&planTitle) 


plannerPlanConfigurationBucketLocalization := graphmodels.NewPlannerPlanConfigurationBucketLocalization()
externalBucketId := "deliveryBucket"
plannerPlanConfigurationBucketLocalization.SetExternalBucketId(&externalBucketId) 
name := "Deliveries"
plannerPlanConfigurationBucketLocalization.SetName(&name) 
plannerPlanConfigurationBucketLocalization1 := graphmodels.NewPlannerPlanConfigurationBucketLocalization()
externalBucketId := "storePickupBucket"
plannerPlanConfigurationBucketLocalization1.SetExternalBucketId(&externalBucketId) 
name := "Pickup"
plannerPlanConfigurationBucketLocalization1.SetName(&name) 
plannerPlanConfigurationBucketLocalization2 := graphmodels.NewPlannerPlanConfigurationBucketLocalization()
externalBucketId := "specialOrdersBucket"
plannerPlanConfigurationBucketLocalization2.SetExternalBucketId(&externalBucketId) 
name := "Special Orders"
plannerPlanConfigurationBucketLocalization2.SetName(&name) 
plannerPlanConfigurationBucketLocalization3 := graphmodels.NewPlannerPlanConfigurationBucketLocalization()
externalBucketId := "returnProcessingBucket"
plannerPlanConfigurationBucketLocalization3.SetExternalBucketId(&externalBucketId) 
name := "Customer Returns"
plannerPlanConfigurationBucketLocalization3.SetName(&name) 

buckets := []graphmodels.PlannerPlanConfigurationBucketLocalizationable {
	plannerPlanConfigurationBucketLocalization,
	plannerPlanConfigurationBucketLocalization1,
	plannerPlanConfigurationBucketLocalization2,
	plannerPlanConfigurationBucketLocalization3,
}
plannerPlanConfigurationLocalization.SetBuckets(buckets)
plannerPlanConfigurationLocalization1 := graphmodels.NewPlannerPlanConfigurationLocalization()
id := "es-es"
plannerPlanConfigurationLocalization1.SetId(&id) 
languageTag := "es-es"
plannerPlanConfigurationLocalization1.SetLanguageTag(&languageTag) 
planTitle := "Seguimiento de pedidos"
plannerPlanConfigurationLocalization1.SetPlanTitle(&planTitle) 


plannerPlanConfigurationBucketLocalization := graphmodels.NewPlannerPlanConfigurationBucketLocalization()
externalBucketId := "deliveryBucket"
plannerPlanConfigurationBucketLocalization.SetExternalBucketId(&externalBucketId) 
name := "Entregas"
plannerPlanConfigurationBucketLocalization.SetName(&name) 
plannerPlanConfigurationBucketLocalization1 := graphmodels.NewPlannerPlanConfigurationBucketLocalization()
externalBucketId := "storePickupBucket"
plannerPlanConfigurationBucketLocalization1.SetExternalBucketId(&externalBucketId) 
name := "Recogida"
plannerPlanConfigurationBucketLocalization1.SetName(&name) 
plannerPlanConfigurationBucketLocalization2 := graphmodels.NewPlannerPlanConfigurationBucketLocalization()
externalBucketId := "specialOrdersBucket"
plannerPlanConfigurationBucketLocalization2.SetExternalBucketId(&externalBucketId) 
name := "Pedidos especiales"
plannerPlanConfigurationBucketLocalization2.SetName(&name) 
plannerPlanConfigurationBucketLocalization3 := graphmodels.NewPlannerPlanConfigurationBucketLocalization()
externalBucketId := "specialOrdersBucket"
plannerPlanConfigurationBucketLocalization3.SetExternalBucketId(&externalBucketId) 
name := "Devoluciones de clientes"
plannerPlanConfigurationBucketLocalization3.SetName(&name) 

buckets := []graphmodels.PlannerPlanConfigurationBucketLocalizationable {
	plannerPlanConfigurationBucketLocalization,
	plannerPlanConfigurationBucketLocalization1,
	plannerPlanConfigurationBucketLocalization2,
	plannerPlanConfigurationBucketLocalization3,
}
plannerPlanConfigurationLocalization1.SetBuckets(buckets)

localizations := []graphmodels.PlannerPlanConfigurationLocalizationable {
	plannerPlanConfigurationLocalization,
	plannerPlanConfigurationLocalization1,
}
requestBody.SetLocalizations(localizations)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
planConfiguration, err := graphClient.Solutions().BusinessScenarios().ByBusinessScenarioId("businessScenario-id").Planner().PlanConfiguration().Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PlannerPlanConfiguration plannerPlanConfiguration = new PlannerPlanConfiguration();
plannerPlanConfiguration.setDefaultLanguage("en-us");
LinkedList<PlannerPlanConfigurationBucketDefinition> buckets = new LinkedList<PlannerPlanConfigurationBucketDefinition>();
PlannerPlanConfigurationBucketDefinition plannerPlanConfigurationBucketDefinition = new PlannerPlanConfigurationBucketDefinition();
plannerPlanConfigurationBucketDefinition.setExternalBucketId("deliveryBucket");
buckets.add(plannerPlanConfigurationBucketDefinition);
PlannerPlanConfigurationBucketDefinition plannerPlanConfigurationBucketDefinition1 = new PlannerPlanConfigurationBucketDefinition();
plannerPlanConfigurationBucketDefinition1.setExternalBucketId("storePickupBucket");
buckets.add(plannerPlanConfigurationBucketDefinition1);
PlannerPlanConfigurationBucketDefinition plannerPlanConfigurationBucketDefinition2 = new PlannerPlanConfigurationBucketDefinition();
plannerPlanConfigurationBucketDefinition2.setExternalBucketId("specialOrdersBucket");
buckets.add(plannerPlanConfigurationBucketDefinition2);
PlannerPlanConfigurationBucketDefinition plannerPlanConfigurationBucketDefinition3 = new PlannerPlanConfigurationBucketDefinition();
plannerPlanConfigurationBucketDefinition3.setExternalBucketId("returnProcessingBucket");
buckets.add(plannerPlanConfigurationBucketDefinition3);
plannerPlanConfiguration.setBuckets(buckets);
LinkedList<PlannerPlanConfigurationLocalization> localizations = new LinkedList<PlannerPlanConfigurationLocalization>();
PlannerPlanConfigurationLocalization plannerPlanConfigurationLocalization = new PlannerPlanConfigurationLocalization();
plannerPlanConfigurationLocalization.setId("en-us");
plannerPlanConfigurationLocalization.setLanguageTag("en-us");
plannerPlanConfigurationLocalization.setPlanTitle("Order Tracking");
LinkedList<PlannerPlanConfigurationBucketLocalization> buckets1 = new LinkedList<PlannerPlanConfigurationBucketLocalization>();
PlannerPlanConfigurationBucketLocalization plannerPlanConfigurationBucketLocalization = new PlannerPlanConfigurationBucketLocalization();
plannerPlanConfigurationBucketLocalization.setExternalBucketId("deliveryBucket");
plannerPlanConfigurationBucketLocalization.setName("Deliveries");
buckets1.add(plannerPlanConfigurationBucketLocalization);
PlannerPlanConfigurationBucketLocalization plannerPlanConfigurationBucketLocalization1 = new PlannerPlanConfigurationBucketLocalization();
plannerPlanConfigurationBucketLocalization1.setExternalBucketId("storePickupBucket");
plannerPlanConfigurationBucketLocalization1.setName("Pickup");
buckets1.add(plannerPlanConfigurationBucketLocalization1);
PlannerPlanConfigurationBucketLocalization plannerPlanConfigurationBucketLocalization2 = new PlannerPlanConfigurationBucketLocalization();
plannerPlanConfigurationBucketLocalization2.setExternalBucketId("specialOrdersBucket");
plannerPlanConfigurationBucketLocalization2.setName("Special Orders");
buckets1.add(plannerPlanConfigurationBucketLocalization2);
PlannerPlanConfigurationBucketLocalization plannerPlanConfigurationBucketLocalization3 = new PlannerPlanConfigurationBucketLocalization();
plannerPlanConfigurationBucketLocalization3.setExternalBucketId("returnProcessingBucket");
plannerPlanConfigurationBucketLocalization3.setName("Customer Returns");
buckets1.add(plannerPlanConfigurationBucketLocalization3);
plannerPlanConfigurationLocalization.setBuckets(buckets1);
localizations.add(plannerPlanConfigurationLocalization);
PlannerPlanConfigurationLocalization plannerPlanConfigurationLocalization1 = new PlannerPlanConfigurationLocalization();
plannerPlanConfigurationLocalization1.setId("es-es");
plannerPlanConfigurationLocalization1.setLanguageTag("es-es");
plannerPlanConfigurationLocalization1.setPlanTitle("Seguimiento de pedidos");
LinkedList<PlannerPlanConfigurationBucketLocalization> buckets2 = new LinkedList<PlannerPlanConfigurationBucketLocalization>();
PlannerPlanConfigurationBucketLocalization plannerPlanConfigurationBucketLocalization4 = new PlannerPlanConfigurationBucketLocalization();
plannerPlanConfigurationBucketLocalization4.setExternalBucketId("deliveryBucket");
plannerPlanConfigurationBucketLocalization4.setName("Entregas");
buckets2.add(plannerPlanConfigurationBucketLocalization4);
PlannerPlanConfigurationBucketLocalization plannerPlanConfigurationBucketLocalization5 = new PlannerPlanConfigurationBucketLocalization();
plannerPlanConfigurationBucketLocalization5.setExternalBucketId("storePickupBucket");
plannerPlanConfigurationBucketLocalization5.setName("Recogida");
buckets2.add(plannerPlanConfigurationBucketLocalization5);
PlannerPlanConfigurationBucketLocalization plannerPlanConfigurationBucketLocalization6 = new PlannerPlanConfigurationBucketLocalization();
plannerPlanConfigurationBucketLocalization6.setExternalBucketId("specialOrdersBucket");
plannerPlanConfigurationBucketLocalization6.setName("Pedidos especiales");
buckets2.add(plannerPlanConfigurationBucketLocalization6);
PlannerPlanConfigurationBucketLocalization plannerPlanConfigurationBucketLocalization7 = new PlannerPlanConfigurationBucketLocalization();
plannerPlanConfigurationBucketLocalization7.setExternalBucketId("specialOrdersBucket");
plannerPlanConfigurationBucketLocalization7.setName("Devoluciones de clientes");
buckets2.add(plannerPlanConfigurationBucketLocalization7);
plannerPlanConfigurationLocalization1.setBuckets(buckets2);
localizations.add(plannerPlanConfigurationLocalization1);
plannerPlanConfiguration.setLocalizations(localizations);
PlannerPlanConfiguration result = graphClient.solutions().businessScenarios().byBusinessScenarioId("{businessScenario-id}").planner().planConfiguration().patch(plannerPlanConfiguration);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const plannerPlanConfiguration = {
  defaultLanguage: 'en-us',
  buckets: [
    {
      externalBucketId: 'deliveryBucket'
    },
    {
      externalBucketId: 'storePickupBucket'
    },
    {
      externalBucketId: 'specialOrdersBucket'
    },
    {
      externalBucketId: 'returnProcessingBucket'
    }
  ],
  localizations: [
    {
      id: 'en-us',
      languageTag: 'en-us',
      planTitle: 'Order Tracking',
      buckets: [
        {
          externalBucketId: 'deliveryBucket',
          name: 'Deliveries'
        },
        {
          externalBucketId: 'storePickupBucket',
          name: 'Pickup'
        },
        {
          externalBucketId: 'specialOrdersBucket',
          name: 'Special Orders'
        },
        {
          externalBucketId: 'returnProcessingBucket',
          name: 'Customer Returns'
        }
      ]
    },
    {
      id: 'es-es',
      languageTag: 'es-es',
      planTitle: 'Seguimiento de pedidos',
      buckets: [
        {
          externalBucketId: 'deliveryBucket',
          name: 'Entregas'
        },
        {
          externalBucketId: 'storePickupBucket',
          name: 'Recogida'
        },
        {
          externalBucketId: 'specialOrdersBucket',
          name: 'Pedidos especiales'
        },
        {
          externalBucketId: 'specialOrdersBucket',
          name: 'Devoluciones de clientes'
        }
      ]
    }
  ]
};

await client.api('/solutions/businessScenarios/c5d514e6c6864911ac46c720affb6e4d/planner/planConfiguration')
	.version('beta')
	.update(plannerPlanConfiguration);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\PlannerPlanConfiguration;
use Microsoft\Graph\Beta\Generated\Models\PlannerPlanConfigurationBucketDefinition;
use Microsoft\Graph\Beta\Generated\Models\PlannerPlanConfigurationLocalization;
use Microsoft\Graph\Beta\Generated\Models\PlannerPlanConfigurationBucketLocalization;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PlannerPlanConfiguration();
$requestBody->setDefaultLanguage('en-us');
$bucketsPlannerPlanConfigurationBucketDefinition1 = new PlannerPlanConfigurationBucketDefinition();
$bucketsPlannerPlanConfigurationBucketDefinition1->setExternalBucketId('deliveryBucket');
$bucketsArray []= $bucketsPlannerPlanConfigurationBucketDefinition1;
$bucketsPlannerPlanConfigurationBucketDefinition2 = new PlannerPlanConfigurationBucketDefinition();
$bucketsPlannerPlanConfigurationBucketDefinition2->setExternalBucketId('storePickupBucket');
$bucketsArray []= $bucketsPlannerPlanConfigurationBucketDefinition2;
$bucketsPlannerPlanConfigurationBucketDefinition3 = new PlannerPlanConfigurationBucketDefinition();
$bucketsPlannerPlanConfigurationBucketDefinition3->setExternalBucketId('specialOrdersBucket');
$bucketsArray []= $bucketsPlannerPlanConfigurationBucketDefinition3;
$bucketsPlannerPlanConfigurationBucketDefinition4 = new PlannerPlanConfigurationBucketDefinition();
$bucketsPlannerPlanConfigurationBucketDefinition4->setExternalBucketId('returnProcessingBucket');
$bucketsArray []= $bucketsPlannerPlanConfigurationBucketDefinition4;
$requestBody->setBuckets($bucketsArray);

$localizationsPlannerPlanConfigurationLocalization1 = new PlannerPlanConfigurationLocalization();
$localizationsPlannerPlanConfigurationLocalization1->setId('en-us');
$localizationsPlannerPlanConfigurationLocalization1->setLanguageTag('en-us');
$localizationsPlannerPlanConfigurationLocalization1->setPlanTitle('Order Tracking');
$bucketsPlannerPlanConfigurationBucketLocalization1 = new PlannerPlanConfigurationBucketLocalization();
$bucketsPlannerPlanConfigurationBucketLocalization1->setExternalBucketId('deliveryBucket');
$bucketsPlannerPlanConfigurationBucketLocalization1->setName('Deliveries');
$bucketsArray []= $bucketsPlannerPlanConfigurationBucketLocalization1;
$bucketsPlannerPlanConfigurationBucketLocalization2 = new PlannerPlanConfigurationBucketLocalization();
$bucketsPlannerPlanConfigurationBucketLocalization2->setExternalBucketId('storePickupBucket');
$bucketsPlannerPlanConfigurationBucketLocalization2->setName('Pickup');
$bucketsArray []= $bucketsPlannerPlanConfigurationBucketLocalization2;
$bucketsPlannerPlanConfigurationBucketLocalization3 = new PlannerPlanConfigurationBucketLocalization();
$bucketsPlannerPlanConfigurationBucketLocalization3->setExternalBucketId('specialOrdersBucket');
$bucketsPlannerPlanConfigurationBucketLocalization3->setName('Special Orders');
$bucketsArray []= $bucketsPlannerPlanConfigurationBucketLocalization3;
$bucketsPlannerPlanConfigurationBucketLocalization4 = new PlannerPlanConfigurationBucketLocalization();
$bucketsPlannerPlanConfigurationBucketLocalization4->setExternalBucketId('returnProcessingBucket');
$bucketsPlannerPlanConfigurationBucketLocalization4->setName('Customer Returns');
$bucketsArray []= $bucketsPlannerPlanConfigurationBucketLocalization4;
$localizationsPlannerPlanConfigurationLocalization1->setBuckets($bucketsArray);

$localizationsArray []= $localizationsPlannerPlanConfigurationLocalization1;
$localizationsPlannerPlanConfigurationLocalization2 = new PlannerPlanConfigurationLocalization();
$localizationsPlannerPlanConfigurationLocalization2->setId('es-es');
$localizationsPlannerPlanConfigurationLocalization2->setLanguageTag('es-es');
$localizationsPlannerPlanConfigurationLocalization2->setPlanTitle('Seguimiento de pedidos');
$bucketsPlannerPlanConfigurationBucketLocalization1 = new PlannerPlanConfigurationBucketLocalization();
$bucketsPlannerPlanConfigurationBucketLocalization1->setExternalBucketId('deliveryBucket');
$bucketsPlannerPlanConfigurationBucketLocalization1->setName('Entregas');
$bucketsArray []= $bucketsPlannerPlanConfigurationBucketLocalization1;
$bucketsPlannerPlanConfigurationBucketLocalization2 = new PlannerPlanConfigurationBucketLocalization();
$bucketsPlannerPlanConfigurationBucketLocalization2->setExternalBucketId('storePickupBucket');
$bucketsPlannerPlanConfigurationBucketLocalization2->setName('Recogida');
$bucketsArray []= $bucketsPlannerPlanConfigurationBucketLocalization2;
$bucketsPlannerPlanConfigurationBucketLocalization3 = new PlannerPlanConfigurationBucketLocalization();
$bucketsPlannerPlanConfigurationBucketLocalization3->setExternalBucketId('specialOrdersBucket');
$bucketsPlannerPlanConfigurationBucketLocalization3->setName('Pedidos especiales');
$bucketsArray []= $bucketsPlannerPlanConfigurationBucketLocalization3;
$bucketsPlannerPlanConfigurationBucketLocalization4 = new PlannerPlanConfigurationBucketLocalization();
$bucketsPlannerPlanConfigurationBucketLocalization4->setExternalBucketId('specialOrdersBucket');
$bucketsPlannerPlanConfigurationBucketLocalization4->setName('Devoluciones de clientes');
$bucketsArray []= $bucketsPlannerPlanConfigurationBucketLocalization4;
$localizationsPlannerPlanConfigurationLocalization2->setBuckets($bucketsArray);

$localizationsArray []= $localizationsPlannerPlanConfigurationLocalization2;
$requestBody->setLocalizations($localizationsArray);


$result = $graphServiceClient->solutions()->businessScenarios()->byBusinessScenarioId('businessScenario-id')->planner()->planConfiguration()->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.BusinessScenario

$params = @{
	defaultLanguage = "en-us"
	buckets = @(
		@{
			externalBucketId = "deliveryBucket"
		}
		@{
			externalBucketId = "storePickupBucket"
		}
		@{
			externalBucketId = "specialOrdersBucket"
		}
		@{
			externalBucketId = "returnProcessingBucket"
		}
	)
	localizations = @(
		@{
			id = "en-us"
			languageTag = "en-us"
			planTitle = "Order Tracking"
			buckets = @(
				@{
					externalBucketId = "deliveryBucket"
					name = "Deliveries"
				}
				@{
					externalBucketId = "storePickupBucket"
					name = "Pickup"
				}
				@{
					externalBucketId = "specialOrdersBucket"
					name = "Special Orders"
				}
				@{
					externalBucketId = "returnProcessingBucket"
					name = "Customer Returns"
				}
			)
		}
		@{
			id = "es-es"
			languageTag = "es-es"
			planTitle = "Seguimiento de pedidos"
			buckets = @(
				@{
					externalBucketId = "deliveryBucket"
					name = "Entregas"
				}
				@{
					externalBucketId = "storePickupBucket"
					name = "Recogida"
				}
				@{
					externalBucketId = "specialOrdersBucket"
					name = "Pedidos especiales"
				}
				@{
					externalBucketId = "specialOrdersBucket"
					name = "Devoluciones de clientes"
				}
			)
		}
	)
}

Update-MgBetaSolutionBusinessScenarioPlannerPlanConfiguration -BusinessScenarioId $businessScenarioId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.planner_plan_configuration import PlannerPlanConfiguration
from msgraph_beta.generated.models.planner_plan_configuration_bucket_definition import PlannerPlanConfigurationBucketDefinition
from msgraph_beta.generated.models.planner_plan_configuration_localization import PlannerPlanConfigurationLocalization
from msgraph_beta.generated.models.planner_plan_configuration_bucket_localization import PlannerPlanConfigurationBucketLocalization
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PlannerPlanConfiguration(
	default_language = "en-us",
	buckets = [
		PlannerPlanConfigurationBucketDefinition(
			external_bucket_id = "deliveryBucket",
		),
		PlannerPlanConfigurationBucketDefinition(
			external_bucket_id = "storePickupBucket",
		),
		PlannerPlanConfigurationBucketDefinition(
			external_bucket_id = "specialOrdersBucket",
		),
		PlannerPlanConfigurationBucketDefinition(
			external_bucket_id = "returnProcessingBucket",
		),
	],
	localizations = [
		PlannerPlanConfigurationLocalization(
			id = "en-us",
			language_tag = "en-us",
			plan_title = "Order Tracking",
			buckets = [
				PlannerPlanConfigurationBucketLocalization(
					external_bucket_id = "deliveryBucket",
					name = "Deliveries",
				),
				PlannerPlanConfigurationBucketLocalization(
					external_bucket_id = "storePickupBucket",
					name = "Pickup",
				),
				PlannerPlanConfigurationBucketLocalization(
					external_bucket_id = "specialOrdersBucket",
					name = "Special Orders",
				),
				PlannerPlanConfigurationBucketLocalization(
					external_bucket_id = "returnProcessingBucket",
					name = "Customer Returns",
				),
			],
		),
		PlannerPlanConfigurationLocalization(
			id = "es-es",
			language_tag = "es-es",
			plan_title = "Seguimiento de pedidos",
			buckets = [
				PlannerPlanConfigurationBucketLocalization(
					external_bucket_id = "deliveryBucket",
					name = "Entregas",
				),
				PlannerPlanConfigurationBucketLocalization(
					external_bucket_id = "storePickupBucket",
					name = "Recogida",
				),
				PlannerPlanConfigurationBucketLocalization(
					external_bucket_id = "specialOrdersBucket",
					name = "Pedidos especiales",
				),
				PlannerPlanConfigurationBucketLocalization(
					external_bucket_id = "specialOrdersBucket",
					name = "Devoluciones de clientes",
				),
			],
		),
	],
)

result = await graph_client.solutions.business_scenarios.by_business_scenario_id('businessScenario-id').planner.plan_configuration.patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.plannerPlanConfiguration",
  "id": "afdd911ee3db44b69cc28373a6192e94",
  "defaultLanguage": "en-us",
  "buckets": [
    {
      "externalBucketId": "deliveryBucket"
    },
    {
      "externalBucketId": "storePickupBucket"
    },
    {
      "externalBucketId": "specialOrdersBucket"
    },
    {
      "externalBucketId": "returnProcessingBucket"
    }
  ],
  "localizations": [
    {
      "id": "en-us",
      "languageTag": "en-us",
      "planTitle": "Order Tracking",
      "buckets": [
        {
          "externalBucketId": "deliveryBucket",
          "name": "Deliveries"
        },
        {
          "externalBucketId": "storePickupBucket",
          "name": "Pickup"
        },
        {
          "externalBucketId": "specialOrdersBucket",
          "name": "Special Orders"
        },
        {
          "externalBucketId": "returnProcessingBucket",
          "name": "Customer Returns"
        }
      ]
    },
    {
      "id": "es-es",
      "languageTag": "es-es",
      "planTitle": "Seguimiento de pedidos",
      "buckets": [
        {
          "externalBucketId": "deliveryBucket",
          "name": "Entregas"
        },
        {
          "externalBucketId": "storePickupBucket",
          "name": "Recogida"
        },
        {
          "externalBucketId": "specialOrdersBucket",
          "name": "Pedidos especiales"
        },
        {
          "externalBucketId": "specialOrdersBucket",
          "name": "Devoluciones de clientes"
        }
      ]
    }
  ]
}
```
