<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-casemanagement-case-post-attachments?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-20 -->

# Create case attachment

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create [attachment](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-attachment?view=graph-rest-beta) metadata for a [case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta). This method doesn't upload the file content. After creating the attachment, use [Upload attachment content](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-attachment-upload-content?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CaseManagement.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CaseManagement.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This API supports the following built-in roles:

- Global Reader
- Security Reader
- Security Operator
- Security Administrator

## HTTP request

```http
POST /security/caseManagement/cases/{caseId}/attachments
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.security.caseManagement.attachment](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-attachment?view=graph-rest-beta) object.

You can specify the following properties when creating an **attachment**.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description of the resource. Optional. |
| displayName | String | The display name of the attachment. The value must be unique among attachments in the same case; creating another attachment with the same display name isn't allowed. Required. |
| fileExtension | String | The file extension of the attachment. The service normalizes the value to include a leading period. Optional. |
| fileSize | Int64 | The size of the attachment in bytes. The maximum file size is 100 MB. Required. |

The **origin** and **scanResult** properties are service controlled and can't be supplied.

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.security.caseManagement.attachment](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-attachment?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/security/caseManagement/cases/{caseId}/attachments
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.caseManagement.attachment",
  "displayName": "Case MS-001 Attachment",
  "description": "Screenshot of suspicious sign-in activity",
  "fileSize": 1000,
  "fileExtension": "jpeg"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Security.CaseManagement;

var requestBody = new Attachment
{
	OdataType = "#microsoft.graph.security.caseManagement.attachment",
	DisplayName = "Case MS-001 Attachment",
	Description = "Screenshot of suspicious sign-in activity",
	FileSize = 1000L,
	FileExtension = "jpeg",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.CaseManagement.Cases["{case-id}"].Attachments.PostAsync(requestBody);
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
	  graphmodelssecuritycasemanagement "github.com/microsoftgraph/msgraph-beta-sdk-go/models/security/casemanagement"
	  //other-imports
)

requestBody := graphmodelssecuritycasemanagement.NewAttachment()
displayName := "Case MS-001 Attachment"
requestBody.SetDisplayName(&displayName) 
description := "Screenshot of suspicious sign-in activity"
requestBody.SetDescription(&description) 
fileSize := int64(1000)
requestBody.SetFileSize(&fileSize) 
fileExtension := "jpeg"
requestBody.SetFileExtension(&fileExtension) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
attachments, err := graphClient.Security().CaseManagement().Cases().ByCaseId("case-id").Attachments().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.security.casemanagement.Attachment attachment = new com.microsoft.graph.beta.models.security.casemanagement.Attachment();
attachment.setOdataType("#microsoft.graph.security.caseManagement.attachment");
attachment.setDisplayName("Case MS-001 Attachment");
attachment.setDescription("Screenshot of suspicious sign-in activity");
attachment.setFileSize(1000L);
attachment.setFileExtension("jpeg");
com.microsoft.graph.models.security.casemanagement.Attachment result = graphClient.security().caseManagement().cases().byCaseId("{case-id}").attachments().post(attachment);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const attachment = {
  '@odata.type': '#microsoft.graph.security.caseManagement.attachment',
  displayName: 'Case MS-001 Attachment',
  description: 'Screenshot of suspicious sign-in activity',
  fileSize: 1000,
  fileExtension: 'jpeg'
};

await client.api('/security/caseManagement/cases/{caseId}/attachments')
	.version('beta')
	.post(attachment);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Security\CaseManagement\Attachment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Attachment();
$requestBody->setOdataType('#microsoft.graph.security.caseManagement.attachment');
$requestBody->setDisplayName('Case MS-001 Attachment');
$requestBody->setDescription('Screenshot of suspicious sign-in activity');
$requestBody->setFileSize(1000);
$requestBody->setFileExtension('jpeg');

$result = $graphServiceClient->security()->caseManagement()->cases()->byCaseId('case-id')->attachments()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Security

$params = @{
	"@odata.type" = "#microsoft.graph.security.caseManagement.attachment"
	displayName = "Case MS-001 Attachment"
	description = "Screenshot of suspicious sign-in activity"
	fileSize = 1000
	fileExtension = "jpeg"
}

New-MgBetaSecurityCaseManagementCaseAttachment -CaseId $caseId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.security.case_management.attachment import Attachment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Attachment(
	odata_type = "#microsoft.graph.security.caseManagement.attachment",
	display_name = "Case MS-001 Attachment",
	description = "Screenshot of suspicious sign-in activity",
	file_size = 1000,
	file_extension = "jpeg",
)

result = await graph_client.security.case_management.cases.by_case_id('case-id').attachments.post(request_body)
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
  "@odata.type": "#microsoft.graph.security.caseManagement.attachment",
  "id": "1719f11c-21e9-acf2-85db-ade533556fba",
  "createdDateTime": "2026-05-20T11:12:28Z",
  "createdBy": "user@contoso.com",
  "lastModifiedDateTime": "2026-05-20T11:18:45Z",
  "lastModifiedBy": "user@contoso.com",
  "displayName": "Case MS-001 Attachment",
  "description": "Screenshot of suspicious sign-in activity",
  "fileSize": 1000,
  "fileExtension": ".jpeg",
  "scanResult": "unscanned"
}
```
