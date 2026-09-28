<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentregistry-list-agentcardmanifests?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# List agentCardManifests

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Retrieve all [agent card manifests](https://learn.microsoft.com/en-us/graph/api/resources/agentcardmanifest?view=graph-rest-beta) for the tenant.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentCardManifest.Read.All | AgentCardManifest.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentCardManifest.Read.All | AgentCardManifest.ReadWrite.All, AgentCardManifest.ReadWrite.ManagedBy |

Important

When using delegated permissions, the authenticated user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation.

*Agent Registry Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
GET /agentRegistry/agentCardManifests
```

## Optional query parameters

This method supports the `$select` and `$filter` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [agentCardManifest](https://learn.microsoft.com/en-us/graph/api/resources/agentcardmanifest?view=graph-rest-beta) objects in the response body.

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
GET https://graph.microsoft.com/beta/agentRegistry/agentCardManifests
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.AgentRegistry.AgentCardManifests.GetAsync();
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
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
agentCardManifests, err := graphClient.AgentRegistry().AgentCardManifests().Get(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AgentCardManifestCollectionResponse result = graphClient.agentRegistry().agentCardManifests().get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let agentCardManifests = await client.api('/agentRegistry/agentCardManifests')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->agentRegistry()->agentCardManifests()->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.agent_registry.agent_card_manifests.get()
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
  "value": [
    {
      "id": "Security Copilot Platform Agent Card Manifest: 00223",
      "ownerIds": [
        "daf58b0e-44e1-433c-b6b0-ca70cae320b8",
        "b9108c41-d2d2-4e78-b073-92f57b752bd0"
      ],
      "managedBy": "719cc904-9700-4e08-9941-fd826cc84c60",
      "originatingStore": "Microsoft Security Copilot",
      "createdBy": "d47bffae-411a-4de9-8548-05e79bc01f0d",
      "protocolVersion": "0.2.9",
      "createdDateTime": "2025-01-01T00:00:00.1234567Z",
      "lastModifiedDateTime": "2025-01-01T00:00:00.1234567Z",
      "displayName": "Conditional Access Agent",
      "description": "The Conditional Access optimization agent helps you ensure all users and applications are protected by Conditional Access policies.",
      "iconUrl": "https://conditional-access-agent.example.com/icon",
      "provider": {
        "organization": "Microsoft Inc.",
        "url": "https://www.microsoft.com"
      },
      "version": "1.2.0",
      "documentationUrl": "https://learn.microsoft.com/en-us/entra/identity/conditional-access/agent-optimization",
      "capabilities": {
        "streaming": true,
        "pushNotifications": true,
        "stateTransitionHistory": false,
        "extensions": [
          {
            "uri": "https://contoso.example.com/a2a/capabilities/secureMessaging",
            "description": null,
            "required": false,
            "params": {
              "useHttps": true,
              "info": {
                "version": "1.0.0"
              }
            }
          }
        ]
      },
      "securitySchemes": {
        "google": {
          "@odata.type": "#microsoft.graph.apiKeySecurityScheme",
          "type": "apiKey",
          "description": "Use an api key",
          "name": "key",
          "in": "cookie"
        },
        "entra": {
          "@odata.type": "#microsoft.graph.oAuth2SecurityScheme",
          "type": "oauth2",
          "description": "Use oauth",
          "flows": {
            "clientCredentials": {
              "tokenUrl": "https://login.microsoftonline.com",
              "refreshUrl": null,
              "scopes": {
                "agent.run": "run the agent"
              }
            }
          }
        }
      },
      "security": [
        {
          "google": []
        },
        {
          "entra": []
        }
      ],
      "defaultInputModes": [
        "application/json"
      ],
      "defaultOutputModes": [
        "application/json",
        "text/html"
      ],
      "skills": [
        {
          "id": "analyze-conditional-access",
          "displayName": "CA Optimizer",
          "description": "The agent can recommend new policies and update existing conditional access policies.",
          "tags": [
            "security",
            "optimize",
            "conditional-access"
          ],
          "examples": [
            "Find policies that need updating."
          ],
          "inputModes": [
            "application/json",
            "text/plain"
          ],
          "outputModes": [
            "application/json",
            "application/vnd.geo+json",
            "text/html"
          ],
          "security": [
            {
              "entra": []
            }
          ]
        }
      ],
      "supportsAuthenticatedExtendedCard": false
    }
  ]
}
```
