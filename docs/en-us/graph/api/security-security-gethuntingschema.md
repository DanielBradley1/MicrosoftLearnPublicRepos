<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-security-gethuntingschema?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# security: getHuntingSchema

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Retrieve the advanced hunting schema accessible to the signed-in user, including the tables and functions the user is authorized to query and invoke in [advanced hunting](https://learn.microsoft.com/en-us/microsoft-365/security/defender/advanced-hunting-overview?view=o365-worldwide&preserve-view=true) with Microsoft Defender XDR.

The returned schema reflects the user's effective permissions. Each user within a tenant may have a different effective schema depending on their role and access level.

Common use cases include:

- **Preventing unauthorized queries**: Determine which tables and functions a user can access before executing Kusto queries, reducing the risk of authorization failures.
- **Permission-aware query generation**: Enable applications and tools to construct queries dynamically based on the user's effective schema.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

The signed-in user must also be assigned a [Microsoft Defender XDR Unified RBAC role](https://learn.microsoft.com/en-us/microsoft-365/security/defender/manage-rbac) that grants permission to run advanced hunting queries, or one of the following Microsoft Entra ID roles which provide only the least privilege necessary: **Security Reader**, **Security Operator**, **Security Administrator**.

## HTTP request

```http
GET /security/getHuntingSchema
```

## Function parameters

This method doesn't support any OData query parameters to customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [huntingSchemaResult](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschemaresult?view=graph-rest-beta) in the response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/beta/security/getHuntingSchema
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.MicrosoftGraphSecurityGetHuntingSchema.GetAsync();
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
microsoftGraphSecurityGetHuntingSchema, err := graphClient.Security().MicrosoftGraphSecurityGetHuntingSchema().Get(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.security().microsoftGraphSecurityGetHuntingSchema().get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let huntingSchemaResult = await client.api('/security/getHuntingSchema')
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


$result = $graphServiceClient->security()->microsoftGraphSecurityGetHuntingSchema()->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Security

Get-MgBetaSecurityHuntingSchema
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.security.microsoft_graph_security_get_hunting_schema.get()
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "tables": [
    {
      "name": "DeviceProcessEvents",
      "description": "Process creation and related events",
      "columns": [
        {
          "name": "Timestamp",
          "dataType": "DateTime",
          "description": "Date and time when the record was generated"
        },
        {
          "name": "DeviceId",
          "dataType": "String",
          "description": "Unique identifier for the device in the service"
        },
        {
          "name": "DeviceName",
          "dataType": "String",
          "description": "Fully qualified domain name (FQDN) of the device"
        }
      ]
    },
    {
      "name": "DeviceNetworkEvents",
      "description": "Network connection and related events",
      "columns": [
        {
          "name": "Timestamp",
          "dataType": "DateTime",
          "description": "Date and time when the record was generated"
        },
        {
          "name": "DeviceId",
          "dataType": "String",
          "description": "Unique identifier for the device in the service"
        }
      ]
    }
  ],
  "functions": {
    "builtInFunctions": [
      {
        "huntingFunctionId": 1,
        "name": "FileProfile",
        "path": "Built-in",
        "documentation": "Enriches query results with file information such as file name, size, and hash.",
        "inputParameters": [
          {
            "name": "SHA1",
            "cslType": "string",
            "defaultValue": null
          }
        ],
        "outputColumns": [
          {
            "name": "SHA1",
            "dataType": "String",
            "description": "SHA-1 hash of the file"
          },
          {
            "name": "SHA256",
            "dataType": "String",
            "description": "SHA-256 hash of the file"
          }
        ]
      }
    ],
    "savedFunctions": [
      {
        "huntingFunctionId": 100,
        "name": "MyCustomQuery",
        "path": "Shared",
        "description": "A custom query that filters device events by severity.",
        "createdBy": "user@contoso.com",
        "lastModifiedBy": "user@contoso.com",
        "lastModifiedDateTime": "2026-04-15T10:30:00Z",
        "inputParameters": [],
        "outputColumns": [
          {
            "name": "DeviceId",
            "dataType": "String",
            "description": "Unique identifier for the device"
          }
        ]
      }
    ]
  }
}
```
