<!-- Source: https://learn.microsoft.com/en-us/graph/api/userflowlanguagepage-put?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Update userFlowLanguagePage

Namespace: microsoft.graph

Update the values in an userFlowLanguagePage object. You may only update the values in an overridesPage, which is used to customize the values shown to a user during a user journey defined by a user flow.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | IdentityUserFlow.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | IdentityUserFlow.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *External ID User Flow Administrator* is the least privileged role supported for this operation.

## HTTP request

To reference the content within the object, you must use `$value`. This returns the content within the object and allows you to reference it directly.

```http
PUT /identity/b2xUserFlows/{id}/languages/{id}/overridesPages/{id}/$value
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation for the values contained within a [userFlowLanguagePage](https://learn.microsoft.com/en-us/graph/api/resources/userflowlanguagepage?view=graph-rest-1.0).

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PUT https://graph.microsoft.com/v1.0/identity/b2xUserFlows/B2X_1_Partner/languages/en/overridesPages/selfasserted1_1/$value
Content-Type: application/json

{
"LocalizedStrings": [
      {
          "ElementType": "UxElement",
          "ElementId": null,
          "StringId": "alert_message",
          "Override": true,
          "Value": "Are you sure that you want to cancel entering your information?"
      }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Identity.B2xUserFlows.Item.Languages.Item.OverridesPages.Item.Value;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new $valuePutRequestBody
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"LocalizedStrings" , new List<object>
			{
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"elementType", new UntypedString("UxElement")
					},
					{
						"elementId", new UntypedNull()
					},
					{
						"stringId", new UntypedString("alert_message")
					},
					{
						"override", new UntypedBoolean(true)
					},
					{
						"value", new UntypedString("Are you sure that you want to cancel entering your information?")
					},
				}),
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Identity.B2xUserFlows["{b2xIdentityUserFlow-id}"].Languages["{userFlowLanguageConfiguration-id}"].OverridesPages["{userFlowLanguagePage-id}"].Content.PutAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.identity.b2xuserflows.item.languages.item.overridespages.item.value.$valuePutRequestBody valuePutRequestBody = new com.microsoft.graph.identity.b2xuserflows.item.languages.item.overridespages.item.value.$valuePutRequestBody();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<Object> localizedStrings = new LinkedList<Object>();
 property = new ();
property.setElementType("UxElement");
property.setElementId(null);
property.setStringId("alert_message");
property.setOverride(true);
property.setValue("Are you sure that you want to cancel entering your information?");
localizedStrings.add(property);
additionalData.put("LocalizedStrings", localizedStrings);
valuePutRequestBody.setAdditionalData(additionalData);
graphClient.identity().b2xUserFlows().byB2xIdentityUserFlowId("{b2xIdentityUserFlow-id}").languages().byUserFlowLanguageConfigurationId("{userFlowLanguageConfiguration-id}").overridesPages().byUserFlowLanguagePageId("{userFlowLanguagePage-id}").content().put(valuePutRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const stream = {
LocalizedStrings: [
      {
          ElementType: 'UxElement',
          ElementId: null,
          StringId: 'alert_message',
          Override: true,
          Value: 'Are you sure that you want to cancel entering your information?'
      }
  ]
};

await client.api('/identity/b2xUserFlows/B2X_1_Partner/languages/en/overridesPages/selfasserted1_1/$value')
	.put(stream);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Identity\B2xUserFlows\Item\Languages\Item\OverridesPages\Item\Value\$valuePutRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new $valuePutRequestBody();
$additionalData = [
	'LocalizedStrings' => [
			[
				'elementType' => 'UxElement',
				'elementId' => null,
				'stringId' => 'alert_message',
				'override' => true,
				'value' => 'Are you sure that you want to cancel entering your information?',
			],
		],
];
$requestBody->setAdditionalData($additionalData);

$graphServiceClient->identity()->b2xUserFlows()->byB2xIdentityUserFlowId('b2xIdentityUserFlow-id')->languages()->byUserFlowLanguageConfigurationId('userFlowLanguageConfiguration-id')->overridesPages()->byUserFlowLanguagePageId('userFlowLanguagePage-id')->content()->put($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	LocalizedStrings = @(
		@{
			ElementType = "UxElement"
			ElementId = $null
			StringId = "alert_message"
			Override = $true
			Value = "Are you sure that you want to cancel entering your information?"
		}
	)
}

Set-MgIdentityB2XUserFlowLanguageOverridePageContent -B2xIdentityUserFlowId $b2xIdentityUserFlowId -UserFlowLanguageConfigurationId $userFlowLanguageConfigurationId -UserFlowLanguagePageId $userFlowLanguagePageId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity.b2xuserflows.item.languages.item.overridespages.item.value.$value_put_request_body import $valuePutRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = $valuePutRequestBody(
	additional_data = {
			"localized_strings" : [
				{
						"element_type" : "UxElement",
						"element_id" : None,
						"string_id" : "alert_message",
						"override" : True,
						"value" : "Are you sure that you want to cancel entering your information?",
				},
			],
	}
)

await graph_client.identity.b2x_user_flows.by_b2x_identity_user_flow_id('b2xIdentityUserFlow-id').languages.by_user_flow_language_configuration_id('userFlowLanguageConfiguration-id').overrides_pages.by_user_flow_language_page_id('userFlowLanguagePage-id').content.put(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

**Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 204 No Content
```
