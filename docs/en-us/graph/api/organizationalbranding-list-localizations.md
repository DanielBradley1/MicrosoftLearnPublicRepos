<!-- Source: https://learn.microsoft.com/en-us/graph/api/organizationalbranding-list-localizations?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# List localizations

Namespace: microsoft.graph

Retrieve all localization branding objects, including the default branding.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | User.Read | Organization.Read.All, Organization.ReadWrite.All, OrganizationalBranding.Read.All, OrganizationalBranding.ReadWrite.All, User.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | OrganizationalBranding.Read.All | Organization.Read.All, Organization.ReadWrite.All, OrganizationalBranding.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Global Reader* or *Organizational Branding Administrator* are the least privileged roles supported for this operation.

## HTTP request

```http
GET /organization/{organizationId}/branding/localizations
```

## Optional query parameters

This method supports only the `$select` OData query parameter to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [organizationalBrandingLocalization](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandinglocalization?view=graph-rest-1.0) objects in the response body.

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

```msgraph
GET https://graph.microsoft.com/v1.0/organization/dcd219dd-bc68-4b9b-bf0b-4a33a796be35/branding/localizations/
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Organization["{organization-id}"].Branding.Localizations.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
localizations, err := graphClient.Organization().ByOrganizationId("organization-id").Branding().Localizations().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OrganizationalBrandingLocalizationCollectionResponse result = graphClient.organization().byOrganizationId("{organization-id}").branding().localizations().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let localizations = await client.api('/organization/dcd219dd-bc68-4b9b-bf0b-4a33a796be35/branding/localizations/')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->organization()->byOrganizationId('organization-id')->branding()->localizations()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

Get-MgOrganizationBrandingLocalization -OrganizationId $organizationId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.organization.by_organization_id('organization-id').branding.localizations.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#organization('84841066-274d-4ec0-a5c1-276be684bdd3')/branding/localizations",
    "value": [
        {
            "@odata.id": "https://graph.microsoft.com/v2/84841066-274d-4ec0-a5c1-276be684bdd3/directoryObjects/$/Microsoft.DirectoryServices.Organization('84841066-274d-4ec0-a5c1-276be684bdd3')//localizations/0",
            "id": "0",
            "backgroundColor": "",
            "backgroundImageRelativeUrl": "c1c6b6c8-ctwpxrbizfcsectmtir3yvna3hrhaib9j7ueqv0ldne/logintenantbranding/0/illustration?ts=637635061764954395",
            "bannerLogoRelativeUrl": "c1c6b6c8-ctwpxrbizfcsectmtir3yvna3hrhaib9j7ueqv0ldne/logintenantbranding/0/bannerlogo?ts=637635061773126717",
            "cdnList": [
                "secure.aadcdn.microsoftonline-p.com",
                "aadcdn.msftauthimages.net",
                "aadcdn.msauthimages.net"
            ],
            "signInPageText": "Contoso",
            "squareLogoRelativeUrl": "c1c6b6c8-ctwpxrbizfcsectmtir3yvna3hrhaib9j7ueqv0ldne/logintenantbranding/0/tilelogo?ts=637635061781098977",
            "usernameHintText": ""
        },
        {
            "@odata.id": "https://graph.microsoft.com/v2/84841066-274d-4ec0-a5c1-276be684bdd3/directoryObjects/$/Microsoft.DirectoryServices.Organization('84841066-274d-4ec0-a5c1-276be684bdd3')//localizations/fr",
            "id": "fr",
            "backgroundColor": "#FFFF33",
            "backgroundImageRelativeUrl": null,
            "bannerLogoRelativeUrl": null,
            "cdnList": [],
            "signInPageText": "Welcome",
            "squareLogoRelativeUrl": null,
            "usernameHintText": "hint"
        }
    ]
}
```
