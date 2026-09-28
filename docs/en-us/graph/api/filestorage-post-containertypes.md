<!-- Source: https://learn.microsoft.com/en-us/graph/api/filestorage-post-containertypes?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create fileStorageContainerType

Namespace: microsoft.graph

Create a new [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0) in the owning tenant. The number of container types in a tenant is [limited](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/development/limits-calling).

Important

- The tenant must own the application that is assigned as the owner of the **fileStorageContainerType** \(**owningAppId**\).
- The registration of a container type in a newly created tenant can fail if the tenant isn't yet fully ready. You might need to wait at least an hour before you can register a container type in a new tenant.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | FileStorageContainerType.Manage.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

> **Note:** Either the SharePoint Embedded admin role or the Global admin role is required to call this API.

## HTTP request

```http
POST /storage/fileStorage/containerTypes
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0) object.

You can specify the following properties when you create a **fileStorageContainerType**.

| Property | Type | Description |
| :--- | :--- | :--- |
| billingClassification | fileStorageContainerBillingClassification | The billing type. The possible values are: `standard`, `trial`, `directToCustomer`, `unknownFutureValue`. The default value is `standard`. Optional. |
| name | String | The name of the **fileStorageContainerType**. Required. |
| owningAppId | Guid | ID of the application that owns the **fileStorageContainerType**. Required. |
| settings | [fileStorageContainerTypeSettings](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertypesettings?view=graph-rest-1.0) | The settings of the **fileStorageContainerType**. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows how to create a trial [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0).

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/storage/fileStorage/containerTypes
Content-Type: application/json

{
  "name": "Test Trial Container",
  "owningAppId": "11335700-9a00-4c00-84dd-0c210f203f00",
  "billingClassification": "trial",
  "settings": {
    "isItemVersioningEnabled": true,
    "isSharingRestricted": false,
    "consumingTenantOverridables": "isSearchEnabled,itemMajorVersionLimit",
    "agent": {
      "chatEmbedAllowedHosts": ["https://localhost:3000"]
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new FileStorageContainerType
{
	Name = "Test Trial Container",
	OwningAppId = Guid.Parse("11335700-9a00-4c00-84dd-0c210f203f00"),
	BillingClassification = FileStorageContainerBillingClassification.Trial,
	Settings = new FileStorageContainerTypeSettings
	{
		IsItemVersioningEnabled = true,
		IsSharingRestricted = false,
		ConsumingTenantOverridables = FileStorageContainerTypeSettingsOverride.IsSearchEnabled | FileStorageContainerTypeSettingsOverride.ItemMajorVersionLimit,
		AdditionalData = new Dictionary<string, object>
		{
			{
				"agent" , new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"chatEmbedAllowedHosts", new UntypedArray(new List<UntypedNode>
						{
							new UntypedString("https://localhost:3000"),
						})
					},
				})
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Storage.FileStorage.ContainerTypes.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "github.com/google/uuid"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewFileStorageContainerType()
name := "Test Trial Container"
requestBody.SetName(&name) 
owningAppId := uuid.MustParse("11335700-9a00-4c00-84dd-0c210f203f00")
requestBody.SetOwningAppId(&owningAppId) 
billingClassification := graphmodels.TRIAL_FILESTORAGECONTAINERBILLINGCLASSIFICATION 
requestBody.SetBillingClassification(&billingClassification) 
settings := graphmodels.NewFileStorageContainerTypeSettings()
isItemVersioningEnabled := true
settings.SetIsItemVersioningEnabled(&isItemVersioningEnabled) 
isSharingRestricted := false
settings.SetIsSharingRestricted(&isSharingRestricted) 
consumingTenantOverridables := graphmodels.ISSEARCHENABLED,ITEMMAJORVERSIONLIMIT_FILESTORAGECONTAINERTYPESETTINGSOVERRIDE 
settings.SetConsumingTenantOverridables(&consumingTenantOverridables) 
additionalData := map[string]interface{}{
agent := graph.New()
	chatEmbedAllowedHosts := []string {
		"https://localhost:3000",
	}
	agent.SetChatEmbedAllowedHosts(chatEmbedAllowedHosts)
	settings.SetAgent(agent)
}
settings.SetAdditionalData(additionalData)
requestBody.SetSettings(settings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
containerTypes, err := graphClient.Storage().FileStorage().ContainerTypes().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

FileStorageContainerType fileStorageContainerType = new FileStorageContainerType();
fileStorageContainerType.setName("Test Trial Container");
fileStorageContainerType.setOwningAppId(UUID.fromString("11335700-9a00-4c00-84dd-0c210f203f00"));
fileStorageContainerType.setBillingClassification(FileStorageContainerBillingClassification.Trial);
FileStorageContainerTypeSettings settings = new FileStorageContainerTypeSettings();
settings.setIsItemVersioningEnabled(true);
settings.setIsSharingRestricted(false);
settings.setConsumingTenantOverridables(EnumSet.of(FileStorageContainerTypeSettingsOverride.IsSearchEnabled, FileStorageContainerTypeSettingsOverride.ItemMajorVersionLimit));
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 agent = new ();
LinkedList<String> chatEmbedAllowedHosts = new LinkedList<String>();
chatEmbedAllowedHosts.add("https://localhost:3000");
agent.setChatEmbedAllowedHosts(chatEmbedAllowedHosts);
additionalData.put("agent", agent);
settings.setAdditionalData(additionalData);
fileStorageContainerType.setSettings(settings);
FileStorageContainerType result = graphClient.storage().fileStorage().containerTypes().post(fileStorageContainerType);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const fileStorageContainerType = {
  name: 'Test Trial Container',
  owningAppId: '11335700-9a00-4c00-84dd-0c210f203f00',
  billingClassification: 'trial',
  settings: {
    isItemVersioningEnabled: true,
    isSharingRestricted: false,
    consumingTenantOverridables: 'isSearchEnabled,itemMajorVersionLimit',
    agent: {
      chatEmbedAllowedHosts: ['https://localhost:3000']
    }
  }
};

await client.api('/storage/fileStorage/containerTypes')
	.post(fileStorageContainerType);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\FileStorageContainerType;
use Microsoft\Graph\Generated\Models\FileStorageContainerBillingClassification;
use Microsoft\Graph\Generated\Models\FileStorageContainerTypeSettings;
use Microsoft\Graph\Generated\Models\FileStorageContainerTypeSettingsOverride;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new FileStorageContainerType();
$requestBody->setName('Test Trial Container');
$requestBody->setOwningAppId('11335700-9a00-4c00-84dd-0c210f203f00');
$requestBody->setBillingClassification(new FileStorageContainerBillingClassification('trial'));
$settings = new FileStorageContainerTypeSettings();
$settings->setIsItemVersioningEnabled(true);
$settings->setIsSharingRestricted(false);
$settings->setConsumingTenantOverridables(new FileStorageContainerTypeSettingsOverride('isSearchEnabled,itemMajorVersionLimit'));
$additionalData = [
	'agent' => [
		'chatEmbedAllowedHosts' => [
'https://localhost:3000', ],
	],
];
$settings->setAdditionalData($additionalData);
$requestBody->setSettings($settings);

$result = $graphServiceClient->storage()->fileStorage()->containerTypes()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.file_storage_container_type import FileStorageContainerType
from msgraph.generated.models.file_storage_container_billing_classification import FileStorageContainerBillingClassification
from msgraph.generated.models.file_storage_container_type_settings import FileStorageContainerTypeSettings
from msgraph.generated.models.file_storage_container_type_settings_override import FileStorageContainerTypeSettingsOverride
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = FileStorageContainerType(
	name = "Test Trial Container",
	owning_app_id = UUID("11335700-9a00-4c00-84dd-0c210f203f00"),
	billing_classification = FileStorageContainerBillingClassification.Trial,
	settings = FileStorageContainerTypeSettings(
		is_item_versioning_enabled = True,
		is_sharing_restricted = False,
		consuming_tenant_overridables = FileStorageContainerTypeSettingsOverride.IsSearchEnabled | FileStorageContainerTypeSettingsOverride.ItemMajorVersionLimit,
		additional_data = {
				"agent" : {
						"chat_embed_allowed_hosts" : [
							"https://localhost:3000",
						],
				},
		}
	),
)

result = await graph_client.storage.file_storage.container_types.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.fileStorageContainerType",
  "id": "de988700-d700-020e-0a00-0831f3042f00",
  "name": "Test Trial Container",
  "owningAppId": "11335700-9a00-4c00-84dd-0c210f203f00",
  "billingClassification": "trial",
  "billingStatus": "valid",
  "createdDateTime": "01/20/2025",
  "expirationDateTime": "02/20/2025",
  "etag": "RVRhZw==",
  "settings": {
    "urlTemplate": "",
    "isDiscoverabilityEnabled": true,
    "isSearchEnabled": true,
    "isItemVersioningEnabled": true,
    "itemMajorVersionLimit": 50,
    "maxStoragePerContainerInBytes": 104857600,
    "isSharingRestricted": false,
    "consumingTenantOverridables": "isSearchEnabled,itemMajorVersionLimit",
    "agent": {
      "chatEmbedAllowedHosts": ["https://localhost:3000"]
    }
  }
}
```
