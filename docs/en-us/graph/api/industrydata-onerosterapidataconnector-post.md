<!-- Source: https://learn.microsoft.com/en-us/graph/api/industrydata-onerosterapidataconnector-post?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-18 -->

# Create oneRosterApiDataConnector

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [oneRosterApiDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-onerosterapidataconnector?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | IndustryData-DataConnector.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | IndustryData-DataConnector.ReadWrite.All | Not available. |

## HTTP request

```http
POST /external/industryData/dataConnectors
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [oneRosterApiDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-onerosterapidataconnector?view=graph-rest-beta) object.

The following table lists the required and optional properties for creating an **oneRosterApiDataConnector** object.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the data connector. Inherited from [industryDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataconnector?view=graph-rest-beta). Required. |
| apiFormat | microsoft.graph.industryData.apiFormat | The API format of the external system being connected to. Inherited from [apiDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-apidataconnector?view=graph-rest-beta). The possible values are: `oneRoster`, `unknownFutureValue`. Required. |
| baseUrl | String | The base URI, including the scheme, host, and path, with or without a trailing '/'. For example, "https://example.com/ims/oneRoster/v1p1". Inherited from [apiDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-apidataconnector?view=graph-rest-beta). Required. |
| credential | [microsoft.graph.industryData.credential](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-credential?view=graph-rest-beta) | The base type for all supported credentials. Inherited from [apiDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-apidataconnector?view=graph-rest-beta). Required. |
| apiVersion | String | The API version of the OneRoster source. Required. |
| isDemographicsEnabled | Boolean | Indicates whether the user specified to import optional demographics data. Required. |
| isFlagsEnabled | Boolean | Indicates whether the user specified to import optional flags data. Required. |
| isContactsEnabled | Boolean | Indicates whether the user specified to import optional contacts data. Required. |

## Response

If successful, this method returns a `201 Created` response code and an updated [microsoft.graph.industryData.oneRosterApiDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-onerosterapidataconnector?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/external/industryData/dataConnectors
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.industryData.oneRosterApiDataConnector",
  "displayName": "Generic OAuth2 Connector",
  "sourceSystem@odata.bind": "https://graph.microsoft.com/beta/external/industryData/sourceSystems('c93a6e02-aeb7-437f-cc52-08dc3fc158af')",
  "apiFormat": "oneRoster",
  "baseUrl": "https://fakeProvider.net/ims/oneroster/v1p1",
  "apiVersion": "1.1",
  "credential": {
    "@odata.type": "#microsoft.graph.industryData.oAuth2ClientCredential",
    "displayName": "One Roster API Credentials",
    "clientId": "530be723-6af3-4952-8658-668fb2598ad7",
    "clientSecret": "thisIsASecret",
    "tokenUrl": "https://login.microsoftonline.com/c27f982b-f7ee-4b8b-bb0e-3c55bd1dc02c/oauth2/token",
    "scope": null
  },
  "isDemographicsEnabled": false,
  "isFlagsEnabled": false,
  "isContactsEnabled": false
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.IndustryData;

var requestBody = new OneRosterApiDataConnector
{
	OdataType = "#microsoft.graph.industryData.oneRosterApiDataConnector",
	DisplayName = "Generic OAuth2 Connector",
	ApiFormat = ApiFormat.OneRoster,
	BaseUrl = "https://fakeProvider.net/ims/oneroster/v1p1",
	ApiVersion = "1.1",
	Credential = new OAuth2ClientCredential
	{
		OdataType = "#microsoft.graph.industryData.oAuth2ClientCredential",
		DisplayName = "One Roster API Credentials",
		ClientId = "530be723-6af3-4952-8658-668fb2598ad7",
		ClientSecret = "thisIsASecret",
		TokenUrl = "https://login.microsoftonline.com/c27f982b-f7ee-4b8b-bb0e-3c55bd1dc02c/oauth2/token",
		Scope = null,
	},
	IsDemographicsEnabled = false,
	IsFlagsEnabled = false,
	IsContactsEnabled = false,
	AdditionalData = new Dictionary<string, object>
	{
		{
			"sourceSystem@odata.bind" , "https://graph.microsoft.com/beta/external/industryData/sourceSystems('c93a6e02-aeb7-437f-cc52-08dc3fc158af')"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.IndustryData.DataConnectors.PostAsync(requestBody);
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
	  graphmodelsindustrydata "github.com/microsoftgraph/msgraph-beta-sdk-go/models/industrydata"
	  //other-imports
)

requestBody := graphmodelsindustrydata.NewIndustryDataConnector()
displayName := "Generic OAuth2 Connector"
requestBody.SetDisplayName(&displayName) 
apiFormat := graphmodels.ONEROSTER_APIFORMAT 
requestBody.SetApiFormat(&apiFormat) 
baseUrl := "https://fakeProvider.net/ims/oneroster/v1p1"
requestBody.SetBaseUrl(&baseUrl) 
apiVersion := "1.1"
requestBody.SetApiVersion(&apiVersion) 
credential := graphmodelsindustrydata.NewOAuth2ClientCredential()
displayName := "One Roster API Credentials"
credential.SetDisplayName(&displayName) 
clientId := "530be723-6af3-4952-8658-668fb2598ad7"
credential.SetClientId(&clientId) 
clientSecret := "thisIsASecret"
credential.SetClientSecret(&clientSecret) 
tokenUrl := "https://login.microsoftonline.com/c27f982b-f7ee-4b8b-bb0e-3c55bd1dc02c/oauth2/token"
credential.SetTokenUrl(&tokenUrl) 
scope := null
credential.SetScope(&scope) 
requestBody.SetCredential(credential)
isDemographicsEnabled := false
requestBody.SetIsDemographicsEnabled(&isDemographicsEnabled) 
isFlagsEnabled := false
requestBody.SetIsFlagsEnabled(&isFlagsEnabled) 
isContactsEnabled := false
requestBody.SetIsContactsEnabled(&isContactsEnabled) 
additionalData := map[string]interface{}{
	"sourceSystem@odata.bind" : "https://graph.microsoft.com/beta/external/industryData/sourceSystems('c93a6e02-aeb7-437f-cc52-08dc3fc158af')", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
dataConnectors, err := graphClient.External().IndustryData().DataConnectors().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.industrydata.OneRosterApiDataConnector industryDataConnector = new com.microsoft.graph.beta.models.industrydata.OneRosterApiDataConnector();
industryDataConnector.setOdataType("#microsoft.graph.industryData.oneRosterApiDataConnector");
industryDataConnector.setDisplayName("Generic OAuth2 Connector");
industryDataConnector.setApiFormat(com.microsoft.graph.beta.models.industrydata.ApiFormat.OneRoster);
industryDataConnector.setBaseUrl("https://fakeProvider.net/ims/oneroster/v1p1");
industryDataConnector.setApiVersion("1.1");
com.microsoft.graph.beta.models.industrydata.OAuth2ClientCredential credential = new com.microsoft.graph.beta.models.industrydata.OAuth2ClientCredential();
credential.setOdataType("#microsoft.graph.industryData.oAuth2ClientCredential");
credential.setDisplayName("One Roster API Credentials");
credential.setClientId("530be723-6af3-4952-8658-668fb2598ad7");
credential.setClientSecret("thisIsASecret");
credential.setTokenUrl("https://login.microsoftonline.com/c27f982b-f7ee-4b8b-bb0e-3c55bd1dc02c/oauth2/token");
credential.setScope(null);
industryDataConnector.setCredential(credential);
industryDataConnector.setIsDemographicsEnabled(false);
industryDataConnector.setIsFlagsEnabled(false);
industryDataConnector.setIsContactsEnabled(false);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("sourceSystem@odata.bind", "https://graph.microsoft.com/beta/external/industryData/sourceSystems('c93a6e02-aeb7-437f-cc52-08dc3fc158af')");
industryDataConnector.setAdditionalData(additionalData);
com.microsoft.graph.models.industrydata.IndustryDataConnector result = graphClient.external().industryData().dataConnectors().post(industryDataConnector);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const industryDataConnector = {
  '@odata.type': '#microsoft.graph.industryData.oneRosterApiDataConnector',
  displayName: 'Generic OAuth2 Connector',
  'sourceSystem@odata.bind': 'https://graph.microsoft.com/beta/external/industryData/sourceSystems(\'c93a6e02-aeb7-437f-cc52-08dc3fc158af\')',
  apiFormat: 'oneRoster',
  baseUrl: 'https://fakeProvider.net/ims/oneroster/v1p1',
  apiVersion: '1.1',
  credential: {
    '@odata.type': '#microsoft.graph.industryData.oAuth2ClientCredential',
    displayName: 'One Roster API Credentials',
    clientId: '530be723-6af3-4952-8658-668fb2598ad7',
    clientSecret: 'thisIsASecret',
    tokenUrl: 'https://login.microsoftonline.com/c27f982b-f7ee-4b8b-bb0e-3c55bd1dc02c/oauth2/token',
    scope: null
  },
  isDemographicsEnabled: false,
  isFlagsEnabled: false,
  isContactsEnabled: false
};

await client.api('/external/industryData/dataConnectors')
	.version('beta')
	.post(industryDataConnector);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\OneRosterApiDataConnector;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\ApiFormat;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\OAuth2ClientCredential;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OneRosterApiDataConnector();
$requestBody->setOdataType('#microsoft.graph.industryData.oneRosterApiDataConnector');
$requestBody->setDisplayName('Generic OAuth2 Connector');
$requestBody->setApiFormat(new ApiFormat('oneRoster'));
$requestBody->setBaseUrl('https://fakeProvider.net/ims/oneroster/v1p1');
$requestBody->setApiVersion('1.1');
$credential = new OAuth2ClientCredential();
$credential->setOdataType('#microsoft.graph.industryData.oAuth2ClientCredential');
$credential->setDisplayName('One Roster API Credentials');
$credential->setClientId('530be723-6af3-4952-8658-668fb2598ad7');
$credential->setClientSecret('thisIsASecret');
$credential->setTokenUrl('https://login.microsoftonline.com/c27f982b-f7ee-4b8b-bb0e-3c55bd1dc02c/oauth2/token');
$credential->setScope(null);
$requestBody->setCredential($credential);
$requestBody->setIsDemographicsEnabled(false);
$requestBody->setIsFlagsEnabled(false);
$requestBody->setIsContactsEnabled(false);
$additionalData = [
	'sourceSystem@odata.bind' => 'https://graph.microsoft.com/beta/external/industryData/sourceSystems(\'c93a6e02-aeb7-437f-cc52-08dc3fc158af\')',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->external()->industryData()->dataConnectors()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Search

$params = @{
	"@odata.type" = "#microsoft.graph.industryData.oneRosterApiDataConnector"
	displayName = "Generic OAuth2 Connector"
	"sourceSystem@odata.bind" = "https://graph.microsoft.com/beta/external/industryData/sourceSystems('c93a6e02-aeb7-437f-cc52-08dc3fc158af')"
	apiFormat = "oneRoster"
	baseUrl = "https://fakeProvider.net/ims/oneroster/v1p1"
	apiVersion = "1.1"
	credential = @{
		"@odata.type" = "#microsoft.graph.industryData.oAuth2ClientCredential"
		displayName = "One Roster API Credentials"
		clientId = "530be723-6af3-4952-8658-668fb2598ad7"
		clientSecret = "thisIsASecret"
		tokenUrl = "https://login.microsoftonline.com/c27f982b-f7ee-4b8b-bb0e-3c55bd1dc02c/oauth2/token"
		scope = $null
	}
	isDemographicsEnabled = $false
	isFlagsEnabled = $false
	isContactsEnabled = $false
}

New-MgBetaExternalIndustryDataConnector -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.industry_data.one_roster_api_data_connector import OneRosterApiDataConnector
from msgraph_beta.generated.models.api_format import ApiFormat
from msgraph_beta.generated.models.industry_data.o_auth2_client_credential import OAuth2ClientCredential
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OneRosterApiDataConnector(
	odata_type = "#microsoft.graph.industryData.oneRosterApiDataConnector",
	display_name = "Generic OAuth2 Connector",
	api_format = ApiFormat.OneRoster,
	base_url = "https://fakeProvider.net/ims/oneroster/v1p1",
	api_version = "1.1",
	credential = OAuth2ClientCredential(
		odata_type = "#microsoft.graph.industryData.oAuth2ClientCredential",
		display_name = "One Roster API Credentials",
		client_id = "530be723-6af3-4952-8658-668fb2598ad7",
		client_secret = "thisIsASecret",
		token_url = "https://login.microsoftonline.com/c27f982b-f7ee-4b8b-bb0e-3c55bd1dc02c/oauth2/token",
		scope = None,
	),
	is_demographics_enabled = False,
	is_flags_enabled = False,
	is_contacts_enabled = False,
	additional_data = {
			"source_system@odata_bind" : "https://graph.microsoft.com/beta/external/industryData/sourceSystems('c93a6e02-aeb7-437f-cc52-08dc3fc158af')",
	}
)

result = await graph_client.external.industry_data.data_connectors.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.industryData.oneRosterApiDataConnector",
  "id": "f72b2c92-4b8b-461d-3725-08dc3fc158ff",
  "displayName": "Generic OAuth2 Connector",
  "apiFormat": "oneRoster",
  "baseUrl": "https://fakeProvider.net/ims/oneroster/v1p1",
  "apiVersion": "1.1",
  "isDemographicsEnabled": false,
  "isFlagsEnabled": false,
  "isContactsEnabled": false,
  "credential": {
    "@odata.type": "#microsoft.graph.industryData.oAuth2ClientCredential",
    "displayName": "One Roster API Credentials",
    "isValid": true,
    "lastValidDateTime": null,
    "clientId": "530be723-6af3-4952-8658-668fb2598ad7",
    "tokenUrl": "https://login.microsoftonline.com/c27f982b-f7ee-4b8b-bb0e-3c55bd1dc02c/oauth2/token",
    "scope": null
  }
}
```
