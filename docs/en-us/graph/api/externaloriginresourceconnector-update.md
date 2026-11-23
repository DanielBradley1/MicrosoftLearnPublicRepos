<!-- Source: https://learn.microsoft.com/en-us/graph/api/externaloriginresourceconnector-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-05 -->

# Update externalOriginResourceConnector

Namespace: microsoft.graph

Update the properties of an [externalOriginResourceConnector](https://learn.microsoft.com/en-us/graph/api/resources/externaloriginresourceconnector?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EntitlementManagement.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EntitlementManagement.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /identityGovernance/entitlementManagement/externalOriginResourceConnectors/{externalOriginResourceConnectorId}
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
| connectionInfo | [connectionInfo](https://learn.microsoft.com/en-us/graph/api/resources/connectioninfo?view=graph-rest-1.0) | The connection information used to communicate with the external resource system. |
| connectorType | connectorType | The type of connector. The possible values are: `sapIag`, `unknownFutureValue`. |
| description | String | A description of the connector. |
| displayName | String | The display name of the connector. |

## Response

If successful, this method returns a `200 OK` response code and an updated [externalOriginResourceConnector](https://learn.microsoft.com/en-us/graph/api/resources/externaloriginresourceconnector?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/externalOriginResourceConnectors/e363ebb8-6faa-4980-ac5b-eefc196e1cd4
Content-Type: application/json

{
  "connectorType": "sapIag",
  "displayName": "SAP IAG Connector 2.0",
  "description": "SAP IAG Connector 2.0 description",
  "connectionInfo": {
    "@odata.type": "microsoft.graph.externalTokenBasedSapIagConnectionInfo",
    "url": "https://contoso.example.com",
    "keyVaultName": "Keyvault",
    "subscriptionId": "5ee98b73-d9df-43a7-8a92-36855054bdee",
    "resourceGroup": "SAP IAG Group",
    "accessTokenUrl": "https://contoso.example.com/oauth/token",
    "clientId": "e9ad8b1d-959c-4e86-8ba2-2cbf4d14bc29",
    "secretName": "clientSecret"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ExternalOriginResourceConnector
{
	ConnectorType = ConnectorType.SapIag,
	DisplayName = "SAP IAG Connector 2.0",
	Description = "SAP IAG Connector 2.0 description",
	ConnectionInfo = new ExternalTokenBasedSapIagConnectionInfo
	{
		OdataType = "microsoft.graph.externalTokenBasedSapIagConnectionInfo",
		Url = "https://contoso.example.com",
		KeyVaultName = "Keyvault",
		SubscriptionId = "5ee98b73-d9df-43a7-8a92-36855054bdee",
		ResourceGroup = "SAP IAG Group",
		AccessTokenUrl = "https://contoso.example.com/oauth/token",
		ClientId = "e9ad8b1d-959c-4e86-8ba2-2cbf4d14bc29",
		SecretName = "clientSecret",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.ExternalOriginResourceConnectors["{externalOriginResourceConnector-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewExternalOriginResourceConnector()
connectorType := graphmodels.SAPIAG_CONNECTORTYPE 
requestBody.SetConnectorType(&connectorType) 
displayName := "SAP IAG Connector 2.0"
requestBody.SetDisplayName(&displayName) 
description := "SAP IAG Connector 2.0 description"
requestBody.SetDescription(&description) 
connectionInfo := graphmodels.NewExternalTokenBasedSapIagConnectionInfo()
url := "https://contoso.example.com"
connectionInfo.SetUrl(&url) 
keyVaultName := "Keyvault"
connectionInfo.SetKeyVaultName(&keyVaultName) 
subscriptionId := "5ee98b73-d9df-43a7-8a92-36855054bdee"
connectionInfo.SetSubscriptionId(&subscriptionId) 
resourceGroup := "SAP IAG Group"
connectionInfo.SetResourceGroup(&resourceGroup) 
accessTokenUrl := "https://contoso.example.com/oauth/token"
connectionInfo.SetAccessTokenUrl(&accessTokenUrl) 
clientId := "e9ad8b1d-959c-4e86-8ba2-2cbf4d14bc29"
connectionInfo.SetClientId(&clientId) 
secretName := "clientSecret"
connectionInfo.SetSecretName(&secretName) 
requestBody.SetConnectionInfo(connectionInfo)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
externalOriginResourceConnectors, err := graphClient.IdentityGovernance().EntitlementManagement().ExternalOriginResourceConnectors().ByExternalOriginResourceConnectorId("externalOriginResourceConnector-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ExternalOriginResourceConnector externalOriginResourceConnector = new ExternalOriginResourceConnector();
externalOriginResourceConnector.setConnectorType(ConnectorType.SapIag);
externalOriginResourceConnector.setDisplayName("SAP IAG Connector 2.0");
externalOriginResourceConnector.setDescription("SAP IAG Connector 2.0 description");
ExternalTokenBasedSapIagConnectionInfo connectionInfo = new ExternalTokenBasedSapIagConnectionInfo();
connectionInfo.setOdataType("microsoft.graph.externalTokenBasedSapIagConnectionInfo");
connectionInfo.setUrl("https://contoso.example.com");
connectionInfo.setKeyVaultName("Keyvault");
connectionInfo.setSubscriptionId("5ee98b73-d9df-43a7-8a92-36855054bdee");
connectionInfo.setResourceGroup("SAP IAG Group");
connectionInfo.setAccessTokenUrl("https://contoso.example.com/oauth/token");
connectionInfo.setClientId("e9ad8b1d-959c-4e86-8ba2-2cbf4d14bc29");
connectionInfo.setSecretName("clientSecret");
externalOriginResourceConnector.setConnectionInfo(connectionInfo);
ExternalOriginResourceConnector result = graphClient.identityGovernance().entitlementManagement().externalOriginResourceConnectors().byExternalOriginResourceConnectorId("{externalOriginResourceConnector-id}").patch(externalOriginResourceConnector);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const externalOriginResourceConnector = {
  connectorType: 'sapIag',
  displayName: 'SAP IAG Connector 2.0',
  description: 'SAP IAG Connector 2.0 description',
  connectionInfo: {
    '@odata.type': 'microsoft.graph.externalTokenBasedSapIagConnectionInfo',
    url: 'https://contoso.example.com',
    keyVaultName: 'Keyvault',
    subscriptionId: '5ee98b73-d9df-43a7-8a92-36855054bdee',
    resourceGroup: 'SAP IAG Group',
    accessTokenUrl: 'https://contoso.example.com/oauth/token',
    clientId: 'e9ad8b1d-959c-4e86-8ba2-2cbf4d14bc29',
    secretName: 'clientSecret'
  }
};

await client.api('/identityGovernance/entitlementManagement/externalOriginResourceConnectors/e363ebb8-6faa-4980-ac5b-eefc196e1cd4')
	.update(externalOriginResourceConnector);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ExternalOriginResourceConnector;
use Microsoft\Graph\Generated\Models\ConnectorType;
use Microsoft\Graph\Generated\Models\ExternalTokenBasedSapIagConnectionInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExternalOriginResourceConnector();
$requestBody->setConnectorType(new ConnectorType('sapIag'));
$requestBody->setDisplayName('SAP IAG Connector 2.0');
$requestBody->setDescription('SAP IAG Connector 2.0 description');
$connectionInfo = new ExternalTokenBasedSapIagConnectionInfo();
$connectionInfo->setOdataType('microsoft.graph.externalTokenBasedSapIagConnectionInfo');
$connectionInfo->setUrl('https://contoso.example.com');
$connectionInfo->setKeyVaultName('Keyvault');
$connectionInfo->setSubscriptionId('5ee98b73-d9df-43a7-8a92-36855054bdee');
$connectionInfo->setResourceGroup('SAP IAG Group');
$connectionInfo->setAccessTokenUrl('https://contoso.example.com/oauth/token');
$connectionInfo->setClientId('e9ad8b1d-959c-4e86-8ba2-2cbf4d14bc29');
$connectionInfo->setSecretName('clientSecret');
$requestBody->setConnectionInfo($connectionInfo);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->externalOriginResourceConnectors()->byExternalOriginResourceConnectorId('externalOriginResourceConnector-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.external_origin_resource_connector import ExternalOriginResourceConnector
from msgraph.generated.models.connector_type import ConnectorType
from msgraph.generated.models.external_token_based_sap_iag_connection_info import ExternalTokenBasedSapIagConnectionInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExternalOriginResourceConnector(
	connector_type = ConnectorType.SapIag,
	display_name = "SAP IAG Connector 2.0",
	description = "SAP IAG Connector 2.0 description",
	connection_info = ExternalTokenBasedSapIagConnectionInfo(
		odata_type = "microsoft.graph.externalTokenBasedSapIagConnectionInfo",
		url = "https://contoso.example.com",
		key_vault_name = "Keyvault",
		subscription_id = "5ee98b73-d9df-43a7-8a92-36855054bdee",
		resource_group = "SAP IAG Group",
		access_token_url = "https://contoso.example.com/oauth/token",
		client_id = "e9ad8b1d-959c-4e86-8ba2-2cbf4d14bc29",
		secret_name = "clientSecret",
	),
)

result = await graph_client.identity_governance.entitlement_management.external_origin_resource_connectors.by_external_origin_resource_connector_id('externalOriginResourceConnector-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.externalOriginResourceConnector",
  "id": "e363ebb8-6faa-4980-ac5b-eefc196e1cd4",
  "displayName": "SAP IAG Connector 2.0",
  "description": "SAP IAG Connector 2.0 description",
  "connectorType": "sapIag",
  "connectionInfo": {
    "@odata.type": "microsoft.graph.externalTokenBasedSapIagConnectionInfo",
    "url": "https://contoso.example.com",
    "accessTokenUrl": "https://contoso.example.com/oauth/token",
    "clientId": "e9ad8b1d-959c-4e86-8ba2-2cbf4d14bc29",
    "keyVaultName": "Keyvault",
    "secretName": "clientSecret",
    "subscriptionId": "5ee98b73-d9df-43a7-8a92-36855054bdee",
    "resourceGroup": "SAP IAG Group"
  },
  "createdBy": "admin@contoso.com",
  "createdDateTime": "2026-02-23T10:15:30Z",
  "modifiedBy": "admin@contoso.com",
  "modifiedDateTime": "2026-02-24T11:20:10Z"
}
```
