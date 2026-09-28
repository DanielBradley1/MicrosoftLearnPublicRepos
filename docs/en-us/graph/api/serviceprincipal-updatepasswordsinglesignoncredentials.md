<!-- Source: https://learn.microsoft.com/en-us/graph/api/serviceprincipal-updatepasswordsinglesignoncredentials?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# servicePrincipal: updatePasswordSingleSignOnCredentials

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update single sign-on credentials using a password for a user or group.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Application.ReadWrite.All and Directory.Read.All | Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Application.ReadWrite.All and Directory.Read.All | Directory.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Users can create and manage credentials for themselves
- Application Administrator
- Cloud Application Administrator

## HTTP request

You can address the service principal using either its **id** or **appId**. **id** and **appId** are referred to as the **Object ID** and **Application \(Client\) ID**, respectively, in app registrations in the Microsoft Entra admin center.

```http
POST /servicePrincipals/{id}/updatePasswordSingleSignOnCredentials
POST /servicePrincipals(appId='{appId}')/updatePasswordSingleSignOnCredentials
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID of the user or group this credential set belongs to. |
| credentials | [credential](https://learn.microsoft.com/en-us/graph/api/resources/credential?view=graph-rest-beta) collection | A list of credential objects that define the complete sign in flow. |

## Response

If successful, this method returns a `204 No Content` response code. It doesn't return anything in the response body.

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
POST https://graph.microsoft.com/beta/servicePrincipals/{id}/updatePasswordSingleSignOnCredentials
Content-type: application/json

{
  "id": "5793aa3b-cca9-4794-679a240f8b58",
  "credentials": [
    {
      "fieldId": "param_username",
      "value": "myusername",
      "type": "username"
    },
    {
      "fieldId": "param_password",
      "value": "pa$$w0rd",
      "type": "password"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.ServicePrincipals.Item.UpdatePasswordSingleSignOnCredentials;
using Microsoft.Graph.Beta.Models;

var requestBody = new UpdatePasswordSingleSignOnCredentialsPostRequestBody
{
	Id = "5793aa3b-cca9-4794-679a240f8b58",
	Credentials = new List<Credential>
	{
		new Credential
		{
			FieldId = "param_username",
			Value = "myusername",
			Type = "username",
		},
		new Credential
		{
			FieldId = "param_password",
			Value = "pa$$w0rd",
			Type = "password",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.ServicePrincipals["{servicePrincipal-id}"].UpdatePasswordSingleSignOnCredentials.PostAsync(requestBody);
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
	  graphserviceprincipals "github.com/microsoftgraph/msgraph-beta-sdk-go/serviceprincipals"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphserviceprincipals.NewUpdatePasswordSingleSignOnCredentialsPostRequestBody()
id := "5793aa3b-cca9-4794-679a240f8b58"
requestBody.SetId(&id) 


credential := graphmodels.NewCredential()
fieldId := "param_username"
credential.SetFieldId(&fieldId) 
value := "myusername"
credential.SetValue(&value) 
type := "username"
credential.SetType(&type) 
credential1 := graphmodels.NewCredential()
fieldId := "param_password"
credential1.SetFieldId(&fieldId) 
value := "pa$$w0rd"
credential1.SetValue(&value) 
type := "password"
credential1.SetType(&type) 

credentials := []graphmodels.Credentialable {
	credential,
	credential1,
}
requestBody.SetCredentials(credentials)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.ServicePrincipals().ByServicePrincipalId("servicePrincipal-id").UpdatePasswordSingleSignOnCredentials().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.serviceprincipals.item.updatepasswordsinglesignoncredentials.UpdatePasswordSingleSignOnCredentialsPostRequestBody updatePasswordSingleSignOnCredentialsPostRequestBody = new com.microsoft.graph.beta.serviceprincipals.item.updatepasswordsinglesignoncredentials.UpdatePasswordSingleSignOnCredentialsPostRequestBody();
updatePasswordSingleSignOnCredentialsPostRequestBody.setId("5793aa3b-cca9-4794-679a240f8b58");
LinkedList<Credential> credentials = new LinkedList<Credential>();
Credential credential = new Credential();
credential.setFieldId("param_username");
credential.setValue("myusername");
credential.setType("username");
credentials.add(credential);
Credential credential1 = new Credential();
credential1.setFieldId("param_password");
credential1.setValue("pa$$w0rd");
credential1.setType("password");
credentials.add(credential1);
updatePasswordSingleSignOnCredentialsPostRequestBody.setCredentials(credentials);
graphClient.servicePrincipals().byServicePrincipalId("{servicePrincipal-id}").updatePasswordSingleSignOnCredentials().post(updatePasswordSingleSignOnCredentialsPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const updatePasswordSingleSignOnCredentials = {
  id: '5793aa3b-cca9-4794-679a240f8b58',
  credentials: [
    {
      fieldId: 'param_username',
      value: 'myusername',
      type: 'username'
    },
    {
      fieldId: 'param_password',
      value: 'pa$$w0rd',
      type: 'password'
    }
  ]
};

await client.api('/servicePrincipals/{id}/updatePasswordSingleSignOnCredentials')
	.version('beta')
	.post(updatePasswordSingleSignOnCredentials);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\ServicePrincipals\Item\UpdatePasswordSingleSignOnCredentials\UpdatePasswordSingleSignOnCredentialsPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\Credential;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UpdatePasswordSingleSignOnCredentialsPostRequestBody();
$requestBody->setId('5793aa3b-cca9-4794-679a240f8b58');
$credentialsCredential1 = new Credential();
$credentialsCredential1->setFieldId('param_username');
$credentialsCredential1->setValue('myusername');
$credentialsCredential1->setType('username');
$credentialsArray []= $credentialsCredential1;
$credentialsCredential2 = new Credential();
$credentialsCredential2->setFieldId('param_password');
$credentialsCredential2->setValue('pa$$w0rd');
$credentialsCredential2->setType('password');
$credentialsArray []= $credentialsCredential2;
$requestBody->setCredentials($credentialsArray);


$graphServiceClient->servicePrincipals()->byServicePrincipalId('servicePrincipal-id')->updatePasswordSingleSignOnCredentials()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Applications

$params = @{
	id = "5793aa3b-cca9-4794-679a240f8b58"
	credentials = @(
		@{
			fieldId = "param_username"
			value = "myusername"
			type = "username"
		}
		@{
			fieldId = "param_password"
			value = "pa$$w0rd"
			type = "password"
		}
	)
}

Update-MgBetaServicePrincipalPasswordSingleSignOnCredential -ServicePrincipalId $servicePrincipalId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.serviceprincipals.item.update_password_single_sign_on_credentials.update_password_single_sign_on_credentials_post_request_body import UpdatePasswordSingleSignOnCredentialsPostRequestBody
from msgraph_beta.generated.models.credential import Credential
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UpdatePasswordSingleSignOnCredentialsPostRequestBody(
	id = "5793aa3b-cca9-4794-679a240f8b58",
	credentials = [
		Credential(
			field_id = "param_username",
			value = "myusername",
			type = "username",
		),
		Credential(
			field_id = "param_password",
			value = "pa$$w0rd",
			type = "password",
		),
	],
)

await graph_client.service_principals.by_service_principal_id('servicePrincipal-id').update_password_single_sign_on_credentials.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
