<!-- Source: https://learn.microsoft.com/en-us/graph/api/onpremisesdirectorysynchronization-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-31 -->

# Update onPremisesDirectorySynchronization

Namespace: microsoft.graph

Update the properties of an [onPremisesDirectorySynchronization](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesdirectorysynchronization?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | OnPremDirectorySynchronization.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

In delegated scenarios with work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role with a supported role permission. *Global Administrator* is the only role supported for this operation.

## HTTP request

```http
PATCH /directory/onPremisesSynchronization/{id}
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
| configuration | [onPremisesDirectorySynchronizationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesdirectorysynchronizationconfiguration?view=graph-rest-1.0) | Consists of configurations that can be fine-tuned and impact the on-premises directory synchronization process for a tenant. |
| features | [onPremisesDirectorySynchronizationFeature](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesdirectorysynchronizationfeature?view=graph-rest-1.0) | Consists of directory synchronization features that can be enabled or disabled. |

## Response

If successful, this method returns a `204 No Content` response code.

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
PATCH https://graph.microsoft.com/v1.0/directory/onPremisesSynchronization/{id}
Content-Type: application/json
Content-length: 293

{
  "configuration": {
    "accidentalDeletionPrevention": {
      "synchronizationPreventionType": "enabledForCount",
      "alertThreshold": 500
    }
  },
  "features": {
    "groupWriteBackEnabled": true
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OnPremisesDirectorySynchronization
{
	Configuration = new OnPremisesDirectorySynchronizationConfiguration
	{
		AccidentalDeletionPrevention = new OnPremisesAccidentalDeletionPrevention
		{
			SynchronizationPreventionType = OnPremisesDirectorySynchronizationDeletionPreventionType.EnabledForCount,
			AlertThreshold = 500,
		},
	},
	Features = new OnPremisesDirectorySynchronizationFeature
	{
		GroupWriteBackEnabled = true,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.OnPremisesSynchronization["{onPremisesDirectorySynchronization-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewOnPremisesDirectorySynchronization()
configuration := graphmodels.NewOnPremisesDirectorySynchronizationConfiguration()
accidentalDeletionPrevention := graphmodels.NewOnPremisesAccidentalDeletionPrevention()
synchronizationPreventionType := graphmodels.ENABLEDFORCOUNT_ONPREMISESDIRECTORYSYNCHRONIZATIONDELETIONPREVENTIONTYPE 
accidentalDeletionPrevention.SetSynchronizationPreventionType(&synchronizationPreventionType) 
alertThreshold := int32(500)
accidentalDeletionPrevention.SetAlertThreshold(&alertThreshold) 
configuration.SetAccidentalDeletionPrevention(accidentalDeletionPrevention)
requestBody.SetConfiguration(configuration)
features := graphmodels.NewOnPremisesDirectorySynchronizationFeature()
groupWriteBackEnabled := true
features.SetGroupWriteBackEnabled(&groupWriteBackEnabled) 
requestBody.SetFeatures(features)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
onPremisesSynchronization, err := graphClient.Directory().OnPremisesSynchronization().ByOnPremisesDirectorySynchronizationId("onPremisesDirectorySynchronization-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OnPremisesDirectorySynchronization onPremisesDirectorySynchronization = new OnPremisesDirectorySynchronization();
OnPremisesDirectorySynchronizationConfiguration configuration = new OnPremisesDirectorySynchronizationConfiguration();
OnPremisesAccidentalDeletionPrevention accidentalDeletionPrevention = new OnPremisesAccidentalDeletionPrevention();
accidentalDeletionPrevention.setSynchronizationPreventionType(OnPremisesDirectorySynchronizationDeletionPreventionType.EnabledForCount);
accidentalDeletionPrevention.setAlertThreshold(500);
configuration.setAccidentalDeletionPrevention(accidentalDeletionPrevention);
onPremisesDirectorySynchronization.setConfiguration(configuration);
OnPremisesDirectorySynchronizationFeature features = new OnPremisesDirectorySynchronizationFeature();
features.setGroupWriteBackEnabled(true);
onPremisesDirectorySynchronization.setFeatures(features);
OnPremisesDirectorySynchronization result = graphClient.directory().onPremisesSynchronization().byOnPremisesDirectorySynchronizationId("{onPremisesDirectorySynchronization-id}").patch(onPremisesDirectorySynchronization);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const onPremisesDirectorySynchronization = {
  configuration: {
    accidentalDeletionPrevention: {
      synchronizationPreventionType: 'enabledForCount',
      alertThreshold: 500
    }
  },
  features: {
    groupWriteBackEnabled: true
  }
};

await client.api('/directory/onPremisesSynchronization/{id}')
	.update(onPremisesDirectorySynchronization);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OnPremisesDirectorySynchronization;
use Microsoft\Graph\Generated\Models\OnPremisesDirectorySynchronizationConfiguration;
use Microsoft\Graph\Generated\Models\OnPremisesAccidentalDeletionPrevention;
use Microsoft\Graph\Generated\Models\OnPremisesDirectorySynchronizationDeletionPreventionType;
use Microsoft\Graph\Generated\Models\OnPremisesDirectorySynchronizationFeature;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OnPremisesDirectorySynchronization();
$configuration = new OnPremisesDirectorySynchronizationConfiguration();
$configurationAccidentalDeletionPrevention = new OnPremisesAccidentalDeletionPrevention();
$configurationAccidentalDeletionPrevention->setSynchronizationPreventionType(new OnPremisesDirectorySynchronizationDeletionPreventionType('enabledForCount'));
$configurationAccidentalDeletionPrevention->setAlertThreshold(500);
$configuration->setAccidentalDeletionPrevention($configurationAccidentalDeletionPrevention);
$requestBody->setConfiguration($configuration);
$features = new OnPremisesDirectorySynchronizationFeature();
$features->setGroupWriteBackEnabled(true);
$requestBody->setFeatures($features);

$result = $graphServiceClient->directory()->onPremisesSynchronization()->byOnPremisesDirectorySynchronizationId('onPremisesDirectorySynchronization-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

$params = @{
	configuration = @{
		accidentalDeletionPrevention = @{
			synchronizationPreventionType = "enabledForCount"
			alertThreshold = 500
		}
	}
	features = @{
		groupWriteBackEnabled = $true
	}
}

Update-MgDirectoryOnPremiseSynchronization -OnPremisesDirectorySynchronizationId $onPremisesDirectorySynchronizationId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.on_premises_directory_synchronization import OnPremisesDirectorySynchronization
from msgraph.generated.models.on_premises_directory_synchronization_configuration import OnPremisesDirectorySynchronizationConfiguration
from msgraph.generated.models.on_premises_accidental_deletion_prevention import OnPremisesAccidentalDeletionPrevention
from msgraph.generated.models.on_premises_directory_synchronization_deletion_prevention_type import OnPremisesDirectorySynchronizationDeletionPreventionType
from msgraph.generated.models.on_premises_directory_synchronization_feature import OnPremisesDirectorySynchronizationFeature
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OnPremisesDirectorySynchronization(
	configuration = OnPremisesDirectorySynchronizationConfiguration(
		accidental_deletion_prevention = OnPremisesAccidentalDeletionPrevention(
			synchronization_prevention_type = OnPremisesDirectorySynchronizationDeletionPreventionType.EnabledForCount,
			alert_threshold = 500,
		),
	),
	features = OnPremisesDirectorySynchronizationFeature(
		group_write_back_enabled = True,
	),
)

result = await graph_client.directory.on_premises_synchronization.by_on_premises_directory_synchronization_id('onPremisesDirectorySynchronization-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
