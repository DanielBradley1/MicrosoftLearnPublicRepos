<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-list-alerts_v2?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-19 -->

# List alerts\_v2

Namespace: microsoft.graph.security

Get a list of [alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-1.0) resources created to track suspicious activities in an organization.

This operation lets you filter and sort through alerts to create an informed cyber security response. It exposes a collection of alerts that were flagged in your network, within the time range you specified in your environment retention policy. The most recent alerts are displayed at the top of the list.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SecurityAlert.Read.All | SecurityAlert.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SecurityAlert.Read.All | SecurityAlert.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Security Reader
- Global Reader
- Security Operator
- Security Administrator

## HTTP request

```http
GET /security/alerts_v2
```

## Optional query parameters

This method supports the following OData query parameters to help customize the response: `$count`, `$filter`, `$skip`, `$top`.

The following properties support `$filter` : **assignedTo**, **classification**, **determination**, **createdDateTime**, **lastUpdateDateTime**, **severity**, **serviceSource** and **status**.

Use `@odata.nextLink` for pagination.

The following are examples of their use:

```http
GET /security/alerts_v2?$filter={property}+eq+'{property-value}'
GET /security/alerts_V2?$top=100&$skip=200
```

For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1: Get all alerts

Get a list of [alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-1.0) objects.

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

```msgraph
GET https://graph.microsoft.com/v1.0/security/alerts_v2
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Alerts_v2.GetAsync();
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
alerts_v2, err := graphClient.Security().Alerts_v2().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.AlertCollectionResponse result = graphClient.security().alertsV2().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let alerts_v2 = await client.api('/security/alerts_v2')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->security()->alerts_v2()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

Get-MgSecurityAlertV2
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.security.alerts_v2.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.security.alert",
      "id": "da637551227677560813_-961444813",
      "providerAlertId": "da637551227677560813_-961444813",
      "incidentId": "28282",
      "status": "new",
      "severity": "low",
      "classification": "unknown",
      "determination": "unknown",
      "serviceSource": "microsoftDefenderForEndpoint",
      "detectionSource": "antivirus",
      "detectorId": "e0da400f-affd-43ef-b1d5-afc2eb6f2756",
      "tenantId": "b3c1b5fc-828c-45fa-a1e1-10d74f6d6e9c",
      "title": "Suspicious execution of hidden file",
      "description": "A hidden file has been launched. This activity could indicate a compromised host. Attackers often hide files associated with malicious tools to evade file system inspection and defenses.",
      "recommendedActions": "Collect artifacts and determine scope\n�\tReview the machine timeline for suspicious activities that may have occurred before and after the time of the alert, and record additional related artifacts (files, IPs/URLs) \n�\tLook for the presence of relevant artifacts on other systems. Identify commonalities and differences between potentially compromised systems.\n�\tSubmit relevant files for deep analysis and review resulting detailed behavioral information.\n�\tSubmit undetected files to the MMPC malware portal\n\nInitiate containment & mitigation \n�\tContact the user to verify intent and initiate local remediation actions as needed.\n�\tUpdate AV signatures and run a full scan. The scan might reveal and remove previously-undetected malware components.\n�\tEnsure that the machine has the latest security updates. In particular, ensure that you have installed the latest software, web browser, and Operating System versions.\n�\tIf credential theft is suspected, reset all relevant users passwords.\n�\tBlock communication with relevant URLs or IPs at the organization�s perimeter.",
      "category": "DefenseEvasion",
      "assignedTo": null,
      "alertWebUrl": "https://security.microsoft.com/alerts/da637551227677560813_-961444813?tid=b3c1b5fc-828c-45fa-a1e1-10d74f6d6e9c",
      "incidentWebUrl": "https://security.microsoft.com/incidents/28282?tid=b3c1b5fc-828c-45fa-a1e1-10d74f6d6e9c",
      "actorDisplayName": null,
      "threatDisplayName": null,
      "threatFamilyName": null,
      "mitreTechniques": [
        "T1564.001"
      ],
      "createdDateTime": "2021-04-27T12:19:27.7211305Z",
      "lastUpdateDateTime": "2021-05-02T14:19:01.3266667Z",
      "resolvedDateTime": null,
      "firstActivityDateTime": "2021-04-26T07:45:50.116Z",
      "lastActivityDateTime": "2021-05-02T07:56:58.222Z",
      "comments": [],
      "evidence": [
        {
          "@odata.type": "#microsoft.graph.security.deviceEvidence",
          "createdDateTime": "2021-04-27T12:19:27.7211305Z",
          "verdict": "unknown",
          "remediationStatus": "none",
          "remediationStatusDetails": null,
          "firstSeenDateTime": "2020-09-12T07:28:32.4321753Z",
          "mdeDeviceId": "73e7e2de709dff64ef64b1d0c30e67fab63279db",
          "azureAdDeviceId": null,
          "deviceDnsName": "yonif-lap3.middleeast.corp.microsoft.com",
          "hostName": "yonif-lap3",
          "ntDomain": null,
          "dnsDomain": "middleeast.corp.microsoft.com",
          "osPlatform": "Windows10",
          "osBuild": 22424,
          "version": "Other",
          "healthStatus": "active",
          "riskScore": "medium",
          "rbacGroupId": 75,
          "rbacGroupName": "UnassignedGroup",
          "onboardingStatus": "onboarded",
          "defenderAvStatus": "unknown",
          "ipInterfaces": [
            "1.1.1.1"
          ],
          "loggedOnUsers": [],
          "roles": [
            "compromised"
          ],
          "detailedRoles": [
            "Main device"
          ],
          "tags": [
            "Test Machine"
          ],
          "vmMetadata": {
            "vmId": "ca1b0d41-5a3b-4d95-b48b-f220aed11d78",
            "cloudProvider": "azure",
            "resourceId": "/subscriptions/8700d3a3-3bb7-4fbe-a090-488a1ad04161/resourceGroups/WdatpApi-EUS-STG/providers/Microsoft.Compute/virtualMachines/NirLaviTests",
            "subscriptionId": "8700d3a3-3bb7-4fbe-a090-488a1ad04161"
          }
        },
        {
          "@odata.type": "#microsoft.graph.security.fileEvidence",
          "createdDateTime": "2021-04-27T12:19:27.7211305Z",
          "verdict": "unknown",
          "remediationStatus": "none",
          "remediationStatusDetails": null,
          "detectionStatus": "detected",
          "mdeDeviceId": "73e7e2de709dff64ef64b1d0c30e67fab63279db",
          "roles": [],
          "detailedRoles": [
            "Referred in command line"
          ],
          "tags": [],
          "fileDetails": {
            "sha1": "5f1e8acedc065031aad553b710838eb366cfee9a",
            "sha256": "8963a19fb992ad9a76576c5638fd68292cffb9aaac29eb8285f9abf6196a7dec",
            "fileName": "MsSense.exe",
            "filePath": "C:\\Program Files\\temp",
            "fileSize": 6136392,
            "filePublisher": "Microsoft Corporation",
            "signer": null,
            "issuer": null
          }
        },
        {
          "@odata.type": "#microsoft.graph.security.processEvidence",
          "createdDateTime": "2021-04-27T12:19:27.7211305Z",
          "verdict": "unknown",
          "remediationStatus": "none",
          "remediationStatusDetails": null,
          "processId": 4780,
          "parentProcessId": 668,
          "processCommandLine": "\"MsSense.exe\"",
          "processCreationDateTime": "2021-08-12T12:43:19.0772577Z",
          "parentProcessCreationDateTime": "2021-08-12T07:39:09.0909239Z",
          "detectionStatus": "detected",
          "mdeDeviceId": "73e7e2de709dff64ef64b1d0c30e67fab63279db",
          "roles": [],
          "detailedRoles": [],
          "tags": [],
          "imageFile": {
            "sha1": "5f1e8acedc065031aad553b710838eb366cfee9a",
            "sha256": "8963a19fb992ad9a76576c5638fd68292cffb9aaac29eb8285f9abf6196a7dec",
            "fileName": "MsSense.exe",
            "filePath": "C:\\Program Files\\temp",
            "fileSize": 6136392,
            "filePublisher": "Microsoft Corporation",
            "signer": null,
            "issuer": null
          },
          "parentProcessImageFile": {
            "sha1": null,
            "sha256": null,
            "fileName": "services.exe",
            "filePath": "C:\\Windows\\System32",
            "fileSize": 731744,
            "filePublisher": "Microsoft Corporation",
            "signer": null,
            "issuer": null
          },
          "userAccount": {
            "accountName": "SYSTEM",
            "domainName": "NT AUTHORITY",
            "userSid": "S-1-5-18",
            "azureAdUserId": null,
            "userPrincipalName": null,
            "displayName": "System"
          }
        },
        {
          "@odata.type": "#microsoft.graph.security.registryKeyEvidence",
          "createdDateTime": "2021-04-27T12:19:27.7211305Z",
          "verdict": "unknown",
          "remediationStatus": "none",
          "remediationStatusDetails": null,
          "registryKey": "SYSTEM\\CONTROLSET001\\CONTROL\\WMI\\AUTOLOGGER\\SENSEAUDITLOGGER",
          "registryHive": "HKEY_LOCAL_MACHINE",
          "roles": [],
          "detailedRoles": [],
          "tags": []
        }
        ],
        "systemTags" : [
            "Defender Experts"
      ]
    }
  ]
}
```

### Example 2: Get all alerts from Microsoft Sentinel

The following example shows how to get all security alerts that originated from Microsoft Sentinel.

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

```msgraph
GET https://graph.microsoft.com/v1.0/security/alerts_v2?$filter=serviceSource eq 'microsoftSentinel'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Alerts_v2.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "serviceSource eq 'microsoftSentinel'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsecurity "github.com/microsoftgraph/msgraph-sdk-go/security"
	  //other-imports
)


requestFilter := "serviceSource eq 'microsoftSentinel'"

requestParameters := &graphsecurity.SecurityAlerts_v2RequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphsecurity.SecurityAlerts_v2RequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
alerts_v2, err := graphClient.Security().Alerts_v2().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.AlertCollectionResponse result = graphClient.security().alertsV2().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "serviceSource eq 'microsoftSentinel'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let alerts_v2 = await client.api('/security/alerts_v2')
	.filter('serviceSource eq \'microsoftSentinel\'')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Alerts_v2\Alerts_v2RequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new Alerts_v2RequestBuilderGetRequestConfiguration();
$queryParameters = Alerts_v2RequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "serviceSource eq 'microsoftSentinel'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->security()->alerts_v2()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

Get-MgSecurityAlertV2 -Filter "serviceSource eq 'microsoftSentinel'" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.alerts_v2.alerts_v2_request_builder import Alerts_v2RequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = Alerts_v2RequestBuilder.Alerts_v2RequestBuilderGetQueryParameters(
		filter = "serviceSource eq 'microsoftSentinel'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.security.alerts_v2.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.security.alert",
      "id": "da637878227677560813_-334257894",
      "providerAlertId": "da637878227677560813_-334257894",
      "incidentId": "33",
      "status": "new",
      "severity": "high",
      "classification": "unknown",
      "determination": "unknown",
      "serviceSource": "microsoftSentinel",
      "detectionSource": "scheduledAlerts",
      "detectorId": "a1b2c3d4-e5f6-47a8-b9c0-d1e2f3a4b5c6",
      "tenantId": "b3c1b5fc-828c-45fa-a1e1-10d74f6d6e9c",
      "title": "Suspicious sign-in activity detected",
      "description": "Multiple failed sign-in attempts followed by a successful sign-in detected from an unusual location.",
      "recommendedActions": "Review the user's recent activity and verify the legitimacy of the sign-in.",
      "category": "CredentialAccess",
      "assignedTo": null,
      "alertWebUrl": "https://security.microsoft.com/alerts/da637878227677560813_-334257894?tid=b3c1b5fc-828c-45fa-a1e1-10d74f6d6e9c",
      "incidentWebUrl": "https://security.microsoft.com/incidents/33?tid=b3c1b5fc-828c-45fa-a1e1-10d74f6d6e9c",
      "actorDisplayName": null,
      "threatDisplayName": null,
      "threatFamilyName": null,
      "mitreTechniques": [
        "T1110"
      ],
      "createdDateTime": "2026-05-05T08:30:00.0000000Z",
      "lastUpdateDateTime": "2026-05-05T09:15:00.0000000Z",
      "resolvedDateTime": null,
      "firstActivityDateTime": "2026-05-05T07:00:00.000Z",
      "lastActivityDateTime": "2026-05-05T08:25:00.000Z",
      "comments": [],
      "evidence": [],
      "systemTags": []
    }
  ]
}
```
