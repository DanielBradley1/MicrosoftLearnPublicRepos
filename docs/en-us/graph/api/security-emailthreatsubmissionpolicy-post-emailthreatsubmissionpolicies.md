<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-emailthreatsubmissionpolicy-post-emailthreatsubmissionpolicies?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# Create emailThreatSubmissionPolicy

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [emailThreatSubmissionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-emailthreatsubmissionpolicy?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ThreatSubmissionPolicy.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ThreatSubmissionPolicy.ReadWrite.All | Not available. |

## HTTP request

```http
POST /security/threatSubmission/emailThreatSubmissionPolicies
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [emailThreatSubmissionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-emailthreatsubmissionpolicy?view=graph-rest-beta) object.

You can also specify the following properties when creating an **emailThreatSubmissionPolicy**. These properties are related to the user reported message settings. For details, see [User reported message settings](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/user-submission).

| Property | Type | Description |
| :--- | :--- | :--- |
| customizedNotificationSenderEmailAddress | String | Specifies the email address of the sender from which email notifications will be sent to end users to inform them whether an email is spam, phish or clean. The default value is `null`. Optional for creation. |
| customizedReportRecipientEmailAddress | String | Specifies the destination where the reported messages from end users will land whenever they report something as phish, junk or not junk. The default value is `null`. Optional for creation. |
| isAlwaysReportEnabledForUsers | Boolean | Indicates whether end users can report a message as spam, phish or junk directly without a confirmation\(popup\). The default value is `true`. Optional for creation. |
| isAskMeEnabledForUsers | Boolean | Indicates whether end users can confirm using a popup before reporting messages as spam, phish or not junk. The default value is `true`. Optional for creation. |
| isCustomizedMessageEnabled | Boolean | Indicates whether the email notifications sent to end users to inform them if an email is phish, spam or junk is customized or not. The default value is `false`. Optional for creation. |
| isCustomizedMessageEnabledForPhishing | Boolean | If enabled, customized message only shows when email is reported as phishing. The default value is `false`. Optional for creation. |
| isCustomizedNotificationSenderEnabled | Boolean | Indicates whether to use the sender email address set using customizedNotificationSenderEmailAddress for sending email notifications to end users. The default value is `false`. Optional for creation. |
| isNeverReportEnabledForUsers | Boolean | Indicates whether end users can simply move the message from one folder to another based on the action of spam, phish or not junk without actually reporting it. The default value is `true`. Optional for creation. |
| isOrganizationBrandingEnabled | Boolean | Indicates whether the branding logo should be used in the email notifications sent to end users. The default value is `false`. Optional for creation. |
| isReportFromQuarantineEnabled | Boolean | Indicates whether end users can submit from the quarantine page. The default value is `true`. Optional for creation. |
| isReportToCustomizedEmailAddressEnabled | Boolean | Indicates whether emails reported by end users should be send to the custom mailbox configured using customizedReportRecipientEmailAddress. The default value is `false`. Optional for creation. |
| isReportToMicrosoftEnabled | Boolean | If enabled, the email will be sent to Microsoft for analysis. The default value is `false`. Requried for creation. |
| isReviewEmailNotificationEnabled | Boolean | Indicates whether an email notification is sent to the end user who reported the email when it has been reviewed by the admin. The default value is `false`. Optional for creation. |

## Response

If successful, this method returns a `201 Created` response code and an [emailThreatSubmissionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-emailthreatsubmissionpolicy?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/security/threatSubmission/emailthreatSubmissionPolicies
Content-type: application/json

{
  "isReportToMicrosoftEnabled": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Security;

var requestBody = new EmailThreatSubmissionPolicy
{
	IsReportToMicrosoftEnabled = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.ThreatSubmission.EmailThreatSubmissionPolicies.PostAsync(requestBody);
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
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-beta-sdk-go/models/security"
	  //other-imports
)

requestBody := graphmodelssecurity.NewEmailThreatSubmissionPolicy()
isReportToMicrosoftEnabled := true
requestBody.SetIsReportToMicrosoftEnabled(&isReportToMicrosoftEnabled) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
emailThreatSubmissionPolicies, err := graphClient.Security().ThreatSubmission().EmailThreatSubmissionPolicies().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.security.EmailThreatSubmissionPolicy emailThreatSubmissionPolicy = new com.microsoft.graph.beta.models.security.EmailThreatSubmissionPolicy();
emailThreatSubmissionPolicy.setIsReportToMicrosoftEnabled(true);
com.microsoft.graph.models.security.EmailThreatSubmissionPolicy result = graphClient.security().threatSubmission().emailThreatSubmissionPolicies().post(emailThreatSubmissionPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const emailThreatSubmissionPolicy = {
  isReportToMicrosoftEnabled: true
};

await client.api('/security/threatSubmission/emailthreatSubmissionPolicies')
	.version('beta')
	.post(emailThreatSubmissionPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Security\EmailThreatSubmissionPolicy;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EmailThreatSubmissionPolicy();
$requestBody->setIsReportToMicrosoftEnabled(true);

$result = $graphServiceClient->security()->threatSubmission()->emailThreatSubmissionPolicies()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Security

$params = @{
	isReportToMicrosoftEnabled = $true
}

New-MgBetaSecurityThreatSubmissionEmailThreatSubmissionPolicy -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.security.email_threat_submission_policy import EmailThreatSubmissionPolicy
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EmailThreatSubmissionPolicy(
	is_report_to_microsoft_enabled = True,
)

result = await graph_client.security.threat_submission.email_threat_submission_policies.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.emailThreatSubmissionPolicy",
  "id": "DefaultReportSubmissionPolicy",
  "isReportToMicrosoftEnabled": true,
  "isReportToCustomizedEmailAddressEnabled": false,
  "isAskMeEnabledForUsers": true,
  "isAlwaysReportEnabledForUsers": true,
  "isNeverReportEnabledForUsers": true,
  "isCustomizedMessageEnabledForPhishing": false,
  "isCustomizedMessageEnabled": false,
  "customizedReportRecipientEmailAddress": null,
  "isReviewEmailNotificationEnabled": false,
  "isCustomNotificationSenderEnabled": false,
  "isOrganizationBrandingEnabled": false,
  "customizedNotificationSenderEmailAddress": null,
  "isReportFromQuarantineEnabled": false
}
```
