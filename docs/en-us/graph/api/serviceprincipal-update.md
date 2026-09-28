<!-- Source: https://learn.microsoft.com/en-us/graph/api/serviceprincipal-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# Update servicePrincipal

Namespace: microsoft.graph

Update the properties of [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) object. This API can also update an [agentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0) object when the **@odata.type** property is set to `#microsoft.graph.agentIdentityBlueprintPrincipal`, or an [agentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0) object when the **@odata.type** property is set to `#microsoft.graph.agentIdentity`.

Important

- Using PATCH to set [**passwordCredential**](https://learn.microsoft.com/en-us/graph/api/resources/passwordcredential?view=graph-rest-1.0) is not supported. Use the [addPassword](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-addpassword?view=graph-rest-1.0) and [removePassword](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-removepassword?view=graph-rest-1.0) methods to update the password or secret for a servicePrincipal.
- Service principals inherit specific properties from their associated app registrations. These properties are synchronized from the app registration, but the synchronization isn't immediate or continuous. Sometimes, updating a service principal may prompt the directory to refresh properties from the app registration, causing updates that weren't part of the original request.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Application.ReadWrite.All | AgentIdentity.ReadWrite.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Application.ReadWrite.OwnedBy | AgentIdentity.ReadWrite.All, Application.ReadWrite.All, Directory.ReadWrite.All |

Important

For delegated access using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- For multitenant apps:

  - Application Administrator
  - Cloud Application Administrator

- For single-tenant apps where the calling user is a non-admin user but is the owner of the backing application, the user must have the *Application Developer* role.

In delegated scenarios using work or school accounts, the following privileges are supported for managing agent identities and agent identity blueprint principals:

- The signed-in user is the owner, or
- The signed-in user is assigned the *Agent ID Administrator* role.

### Permissions for specific scenarios

- To update the **customSecurityAttributes** property:

  - In delegated scenarios, the admin must be assigned the *Attribute Assignment Administrator* role and the app granted the *CustomSecAttributeAssignment.ReadWrite.All* delegated permission.
  - In app-only scenarios using Microsoft Graph permissions, the app must be granted the *CustomSecAttributeAssignment.ReadWrite.All* application permission.

## HTTP request

You can address the service principal using either its **id** or **appId**. **id** and **appId** are referred to as the **Object ID** and **Application \(Client\) ID**, respectively, in app registrations in the Microsoft Entra admin center.

```http
PATCH /servicePrincipals/{id}
PATCH /servicePrincipals(appId='{appId}')
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that aren't included in the request body maintains their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

| Property | Type | Description |
| :--- | :--- | :--- |
| accountEnabled | Boolean | **true** if the service principal account is enabled; otherwise, **false**. |
| addIns | [addIn](https://learn.microsoft.com/en-us/graph/api/resources/addin?view=graph-rest-1.0) | Defines custom behavior that a consuming service can use to call an app in specific contexts. For example, applications that can render file streams [may set the addIns property](https://learn.microsoft.com/en-us/onedrive/developer/file-handlers/?view=odsp-graph-online&preserve-view=true) for its "FileHandler" functionality. This lets services like Microsoft 365 call the application in the context of a document the user is working on. |
| alternativeNames | String collection | Used to retrieve service principals by subscription, identify resource group and full resource IDs for [managed identities](https://learn.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/overview). |
| appRoleAssignmentRequired | Boolean | Specifies whether an **appRoleAssignment** to a user or group is required before Microsoft Entra ID will issue a user or access token to the application. Not nullable. |
| appRoles | [appRole](https://learn.microsoft.com/en-us/graph/api/resources/approle?view=graph-rest-1.0) collection | The application roles exposed by the associated application. For more information, see the **appRoles** property definition on the [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) resource. Not nullable. |
| customSecurityAttributes | [customSecurityAttributeValue](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributevalue?view=graph-rest-1.0) | An open complex type that holds the value of a custom security attribute that is assigned to a directory object.  <br><br><br><li>To update this property in delegated scenarios, the calling principal must be assigned the Attribute Assignment Administrator role and the app granted the <em>CustomSecAttributeAssignment.ReadWrite.All</em> delegated permission.</li><br><br><li>To update this property in app-only scenarios with Microsoft Graph permissions, the app must be granted the <em>CustomSecAttributeAssignment.ReadWrite.All</em> application permission.</li> |
| displayName | String | The display name for the service principal. |
| homepage | String | Home page or landing page of the application. |
| keyCredentials | [keyCredential](https://learn.microsoft.com/en-us/graph/api/resources/keycredential?view=graph-rest-1.0) collection | The collection of key credentials associated with the service principal. Not nullable. |
| logoutUrl | String | Specifies the URL that will be used by Microsoft's authorization service to log out a user using [front-channel](https://openid.net/specs/openid-connect-frontchannel-1_0.html), [back-channel](https://openid.net/specs/openid-connect-backchannel-1_0.html) or SAML logout protocols. |
| oauth2PermissionScopes | [permissionScope](https://learn.microsoft.com/en-us/graph/api/resources/permissionscope?view=graph-rest-1.0) collection | The OAuth 2.0 permission scopes exposed by the associated application. For more information, see the **oauth2PermissionScopes** property definition on the [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) resource. Not nullable. |
| preferredSingleSignOnMode | string | Specifies the single sign-on mode configured for this application. Microsoft Entra ID uses the preferred single sign-on mode to launch the application from Microsoft 365 or the My Apps portal. The supported values are `password`, `saml`, `external`, and `oidc`. |
| replyUrls | String collection | The URLs that user tokens are sent to for sign in with the associated application, or the redirect URIs that OAuth 2.0 authorization codes and access tokens are sent to for the associated application. Not nullable. |
| servicePrincipalNames | String collection | Contains the list of **identifiersUris**, copied over from the associated [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). Additional values can be added to hybrid applications. These values can be used to identify the permissions exposed by this app within Microsoft Entra ID. For example,<br><br>- Client apps requesting permissions to this resource can use these URIs to specify needed permissions in the **requiredResourceAccess** property of their application manifest, or in the "API permissions" blade on the App registrations experience.<br>- Client apps can specify a resource URI which is based on the values of this property to acquire an access token, which is the URI returned in the "aud" claim.<br><br>  <br>The any operator is required for filter expressions on multi-valued properties. Not nullable. |
| tags | String collection | Custom strings that can be used to categorize and identify the application. Not nullable. |
| tokenEncryptionKeyId | String | Specifies the keyId of a public key from the keyCredentials collection. When configured, Microsoft Entra ID issues tokens for this application encrypted using the key specified by this property. The application code that receives the encrypted token must use the matching private key to decrypt the token before it can be used for the signed-in user. |

## Response

If successful, this method returns a `204 No Content` response code and updated [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) object in the response body.

## Example

### Example 1: Update properties of the specified service principal

#### Request

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
PATCH https://graph.microsoft.com/v1.0/servicePrincipals/{id}
Content-type: application/json

{
  "appRoleAssignmentRequired": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ServicePrincipal
{
	AppRoleAssignmentRequired = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ServicePrincipals["{servicePrincipal-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewServicePrincipal()
appRoleAssignmentRequired := true
requestBody.SetAppRoleAssignmentRequired(&appRoleAssignmentRequired) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
servicePrincipals, err := graphClient.ServicePrincipals().ByServicePrincipalId("servicePrincipal-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ServicePrincipal servicePrincipal = new ServicePrincipal();
servicePrincipal.setAppRoleAssignmentRequired(true);
ServicePrincipal result = graphClient.servicePrincipals().byServicePrincipalId("{servicePrincipal-id}").patch(servicePrincipal);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const servicePrincipal = {
  appRoleAssignmentRequired: true
};

await client.api('/servicePrincipals/{id}')
	.update(servicePrincipal);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ServicePrincipal;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ServicePrincipal();
$requestBody->setAppRoleAssignmentRequired(true);

$result = $graphServiceClient->servicePrincipals()->byServicePrincipalId('servicePrincipal-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	appRoleAssignmentRequired = $true
}

Update-MgServicePrincipal -ServicePrincipalId $servicePrincipalId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.service_principal import ServicePrincipal
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ServicePrincipal(
	app_role_assignment_required = True,
)

result = await graph_client.service_principals.by_service_principal_id('servicePrincipal-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 204 No Content
```

### Example 2: Assign a custom security attribute with a string value to a service principal

The following example shows how to assign a custom security attribute with a string value to a service principal.

- Attribute set: `Engineering`
- Attribute: `ProjectDate`
- Attribute data type: String
- Attribute value: `"2022-10-01"`

To assign custom security attributes, the calling principal must be assigned the Attribute Assignment Administrator role and must be granted the *CustomSecAttributeAssignment.ReadWrite.All* permission.

For other similar examples for users, see [Examples: Assign, update, list, or remove custom security attribute assignments using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/custom-security-attributes-examples).

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/servicePrincipals/{id}
Content-type: application/json

{
    "customSecurityAttributes":
    {
        "Engineering":
        {
            "@odata.type":"#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
            "ProjectDate":"2022-10-01"
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new ServicePrincipal
{
	CustomSecurityAttributes = new CustomSecurityAttributeValue
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"Engineering" , new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"@odata.type", new UntypedString("#Microsoft.DirectoryServices.CustomSecurityAttributeValue")
					},
					{
						"projectDate", new UntypedString("2022-10-01")
					},
				})
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ServicePrincipals["{servicePrincipal-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewServicePrincipal()
customSecurityAttributes := graphmodels.NewCustomSecurityAttributeValue()
additionalData := map[string]interface{}{
engineering := graph.New()
projectDate := "2022-10-01"
engineering.SetProjectDate(&projectDate) 
	customSecurityAttributes.SetEngineering(engineering)
}
customSecurityAttributes.SetAdditionalData(additionalData)
requestBody.SetCustomSecurityAttributes(customSecurityAttributes)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
servicePrincipals, err := graphClient.ServicePrincipals().ByServicePrincipalId("servicePrincipal-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ServicePrincipal servicePrincipal = new ServicePrincipal();
CustomSecurityAttributeValue customSecurityAttributes = new CustomSecurityAttributeValue();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 engineering = new ();
engineering.setOdataType("#Microsoft.DirectoryServices.CustomSecurityAttributeValue");
engineering.setProjectDate("2022-10-01");
additionalData.put("Engineering", engineering);
customSecurityAttributes.setAdditionalData(additionalData);
servicePrincipal.setCustomSecurityAttributes(customSecurityAttributes);
ServicePrincipal result = graphClient.servicePrincipals().byServicePrincipalId("{servicePrincipal-id}").patch(servicePrincipal);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const servicePrincipal = {
    customSecurityAttributes: 
    {
        Engineering: 
        {
            '@odata.type':'#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
            ProjectDate: '2022-10-01'
        }
    }
};

await client.api('/servicePrincipals/{id}')
	.update(servicePrincipal);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ServicePrincipal;
use Microsoft\Graph\Generated\Models\CustomSecurityAttributeValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ServicePrincipal();
$customSecurityAttributes = new CustomSecurityAttributeValue();
$additionalData = [
	'Engineering' => [
		'@odata.type' => '#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
		'projectDate' => '2022-10-01',
	],
];
$customSecurityAttributes->setAdditionalData($additionalData);
$requestBody->setCustomSecurityAttributes($customSecurityAttributes);

$result = $graphServiceClient->servicePrincipals()->byServicePrincipalId('servicePrincipal-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	customSecurityAttributes = @{
		Engineering = @{
			"@odata.type" = "#Microsoft.DirectoryServices.CustomSecurityAttributeValue"
			ProjectDate = "2022-10-01"
		}
	}
}

Update-MgServicePrincipal -ServicePrincipalId $servicePrincipalId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.service_principal import ServicePrincipal
from msgraph.generated.models.custom_security_attribute_value import CustomSecurityAttributeValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ServicePrincipal(
	custom_security_attributes = CustomSecurityAttributeValue(
		additional_data = {
				"engineering" : {
						"@odata_type" : "#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
						"project_date" : "2022-10-01",
				},
		}
	),
)

result = await graph_client.service_principals.by_service_principal_id('servicePrincipal-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
