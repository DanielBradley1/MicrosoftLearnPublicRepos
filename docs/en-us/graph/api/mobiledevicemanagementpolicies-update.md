<!-- Source: https://learn.microsoft.com/en-us/graph/api/mobiledevicemanagementpolicies-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# Update mobileDeviceManagementPolicy

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [mobilityManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobilitymanagementpolicy?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.MobilityManagement | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Cloud Device Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
PATCH /policies/mobileDeviceManagementPolicies/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [mobilityManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobilitymanagementpolicy?view=graph-rest-beta) object.

In the request body, supply the values for fields listed below that should be updated. **Note:** You cannot use `PATCH` operation for `appliesTo` with the other properties.

| Property | Type | Description |
| :--- | :--- | :--- |
| appliesTo | policyScope | Determines the groups this policy setting applies to. The possible values are: `none`, `all`, `selected` **Important:** `selected` cannot be used when specifying this property. Use [includedGroups](https://learn.microsoft.com/en-us/graph/api/mobiledevicemanagementpolicies-post-includedgroups?view=graph-rest-beta) to add specific groups. Using `all` will remove any existing groups. |
| isMdmEnrollmentDuringRegistrationDisabled | Boolean | Controls the option if users in an automatic enrollment configuration on Microsoft Entra registered devices are prompted to MDM enroll their device in the Entra account registration flow. |
| complianceUrl | String | Compliance URL of the mobility management application |
| discoveryUrl | String | Discovery URL of the mobility management application |
| termsOfUseUrl | String | Terms of Use URL of the mobility management application |

## Response

If successful, this method returns a `204 No Content` response code.

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

```http
PATCH https://graph.microsoft.com/beta/policies/mobileDeviceManagementPolicies/ab90bacf-55a3-4a3e-839a-aa4b74e4f020
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.mobileDeviceManagementPolicy",
  "complianceUrl": "https://portal.uem.contoso.com/?portalAction=Compliance",
  "discoveryUrl": "https://enrollment.uem.contoso.com/enrollmentserver/discovery.svc",
  "termsOfUseUrl": "https://portal.uem.contoso.com/TermsofUse.aspx"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new MobileDeviceManagementPolicy
{
	OdataType = "#microsoft.graph.mobileDeviceManagementPolicy",
	ComplianceUrl = "https://portal.uem.contoso.com/?portalAction=Compliance",
	DiscoveryUrl = "https://enrollment.uem.contoso.com/enrollmentserver/discovery.svc",
	TermsOfUseUrl = "https://portal.uem.contoso.com/TermsofUse.aspx",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.MobileDeviceManagementPolicies["{mobileDeviceManagementPolicy-id}"].PatchAsync(requestBody);
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewMobileDeviceManagementPolicy()
complianceUrl := "https://portal.uem.contoso.com/?portalAction=Compliance"
requestBody.SetComplianceUrl(&complianceUrl) 
discoveryUrl := "https://enrollment.uem.contoso.com/enrollmentserver/discovery.svc"
requestBody.SetDiscoveryUrl(&discoveryUrl) 
termsOfUseUrl := "https://portal.uem.contoso.com/TermsofUse.aspx"
requestBody.SetTermsOfUseUrl(&termsOfUseUrl) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
mobileDeviceManagementPolicies, err := graphClient.Policies().MobileDeviceManagementPolicies().ByMobileDeviceManagementPolicyId("mobileDeviceManagementPolicy-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MobileDeviceManagementPolicy mobileDeviceManagementPolicy = new MobileDeviceManagementPolicy();
mobileDeviceManagementPolicy.setOdataType("#microsoft.graph.mobileDeviceManagementPolicy");
mobileDeviceManagementPolicy.setComplianceUrl("https://portal.uem.contoso.com/?portalAction=Compliance");
mobileDeviceManagementPolicy.setDiscoveryUrl("https://enrollment.uem.contoso.com/enrollmentserver/discovery.svc");
mobileDeviceManagementPolicy.setTermsOfUseUrl("https://portal.uem.contoso.com/TermsofUse.aspx");
MobileDeviceManagementPolicy result = graphClient.policies().mobileDeviceManagementPolicies().byMobileDeviceManagementPolicyId("{mobileDeviceManagementPolicy-id}").patch(mobileDeviceManagementPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const mobileDeviceManagementPolicy = {
  '@odata.type': '#microsoft.graph.mobileDeviceManagementPolicy',
  complianceUrl: 'https://portal.uem.contoso.com/?portalAction=Compliance',
  discoveryUrl: 'https://enrollment.uem.contoso.com/enrollmentserver/discovery.svc',
  termsOfUseUrl: 'https://portal.uem.contoso.com/TermsofUse.aspx'
};

await client.api('/policies/mobileDeviceManagementPolicies/ab90bacf-55a3-4a3e-839a-aa4b74e4f020')
	.version('beta')
	.update(mobileDeviceManagementPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\MobileDeviceManagementPolicy;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MobileDeviceManagementPolicy();
$requestBody->setOdataType('#microsoft.graph.mobileDeviceManagementPolicy');
$requestBody->setComplianceUrl('https://portal.uem.contoso.com/?portalAction=Compliance');
$requestBody->setDiscoveryUrl('https://enrollment.uem.contoso.com/enrollmentserver/discovery.svc');
$requestBody->setTermsOfUseUrl('https://portal.uem.contoso.com/TermsofUse.aspx');

$result = $graphServiceClient->policies()->mobileDeviceManagementPolicies()->byMobileDeviceManagementPolicyId('mobileDeviceManagementPolicy-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.mobileDeviceManagementPolicy"
	complianceUrl = "https://portal.uem.contoso.com/?portalAction=Compliance"
	discoveryUrl = "https://enrollment.uem.contoso.com/enrollmentserver/discovery.svc"
	termsOfUseUrl = "https://portal.uem.contoso.com/TermsofUse.aspx"
}

Update-MgBetaPolicyMobileDeviceManagementPolicy -MobileDeviceManagementPolicyId $mobileDeviceManagementPolicyId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.mobile_device_management_policy import MobileDeviceManagementPolicy
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MobileDeviceManagementPolicy(
	odata_type = "#microsoft.graph.mobileDeviceManagementPolicy",
	compliance_url = "https://portal.uem.contoso.com/?portalAction=Compliance",
	discovery_url = "https://enrollment.uem.contoso.com/enrollmentserver/discovery.svc",
	terms_of_use_url = "https://portal.uem.contoso.com/TermsofUse.aspx",
)

result = await graph_client.policies.mobile_device_management_policies.by_mobile_device_management_policy_id('mobileDeviceManagementPolicy-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 204 No Content
```
