<!-- Source: https://learn.microsoft.com/en-us/graph/api/industrydata-outboundprovisioningflowset-list-provisioningflows?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-16 -->

# List provisioningFlow objects

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta) objects and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | IndustryData-OutboundFlow.Read.All | IndustryData-OutboundFlow.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | IndustryData-OutboundFlow.Read.All | IndustryData-OutboundFlow.ReadWrite.All |

## HTTP request

```http
GET /external/industryData/outboundProvisioningFlowSets/{id}/provisioningFlows
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta) objects in the response body.

Caution

The **markAllStudentsAsMinors** property of **additionalOptions** under **managementOptions** in [userProvisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-userprovisioningflow?view=graph-rest-beta) is deprecated and will stop returning data on October 15, 2025. Going forward, use the **studentAgeGroup** property.

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
GET https://graph.microsoft.com/beta/external/industryData/outboundProvisioningFlowSets/8c33d025-5e64-4550-2aa3-08dc4ac66fca/provisioningFlows
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.IndustryData.OutboundProvisioningFlowSets["{outboundProvisioningFlowSet-id}"].ProvisioningFlows.GetAsync();
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
provisioningFlows, err := graphClient.External().IndustryData().OutboundProvisioningFlowSets().ByOutboundProvisioningFlowSetId("outboundProvisioningFlowSet-id").ProvisioningFlows().Get(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.industrydata.ProvisioningFlowCollectionResponse result = graphClient.external().industryData().outboundProvisioningFlowSets().byOutboundProvisioningFlowSetId("{outboundProvisioningFlowSet-id}").provisioningFlows().get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let provisioningFlows = await client.api('/external/industryData/outboundProvisioningFlowSets/8c33d025-5e64-4550-2aa3-08dc4ac66fca/provisioningFlows')
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


$result = $graphServiceClient->external()->industryData()->outboundProvisioningFlowSets()->byOutboundProvisioningFlowSetId('outboundProvisioningFlowSet-id')->provisioningFlows()->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Search

Get-MgBetaExternalIndustryDataOutboundProvisioningFlowSetProvisioningFlow -OutboundProvisioningFlowSetId $outboundProvisioningFlowSetId
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.external.industry_data.outbound_provisioning_flow_sets.by_outbound_provisioning_flow_set_id('outboundProvisioningFlowSet-id').provisioning_flows.get()
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#external/industryData/outboundProvisioningFlowSets('8c33d025-5e64-4550-2aa3-08dc4ac66fca')/provisioningFlows",
    "value": [
        {
            "@odata.type": "#microsoft.graph.industryData.securityGroupProvisioningFlow",
            "id": "51f99e09-bdc5-47ff-7a0a-08dc4ac74cf1",
            "createdDateTime": "2024-03-25T22:29:22.6303479Z",
            "lastModifiedDateTime": "2024-03-25T22:29:22.6303479Z",
            "readinessStatus": "disabled",
            "creationOptions": {
                "createBasedOnRoleGroup": true,
                "createBasedOnOrgPlusRoleGroup": false
            }
        },
        {
            "@odata.type": "#microsoft.graph.industryData.classGroupProvisioningFlow",
            "id": "6207e7d7-5eba-4ddc-e607-08dc4ac77409",
            "createdDateTime": "2024-03-25T22:29:16.1177912Z",
            "lastModifiedDateTime": "2024-03-25T22:29:16.1177912Z",
            "readinessStatus": "disabled",
            "configuration": {
                "additionalAttributes": [
                    "courseTitle",
                    "courseCode",
                    "courseSubject",
                    "courseGradeLevel",
                    "courseExternalId",
                    "academicSessionTitle",
                    "academicSessionExternalId"
                ],
                "additionalOptions": {
                    "createTeam": true,
                    "writeDisplayNameOnCreateOnly": true
                },
                "enrollmentMappings": {
                    "ownerEnrollmentMappings": [
                        {
                            "code": "teacher"
                        },
                        {
                            "code": "proctor"
                        },
                        {
                            "code": "teacherAssistant"
                        },
                        {
                            "code": "paraprofessional"
                        },
                        {
                            "code": "physicalTherapist"
                        },
                        {
                            "code": "speechTherapist"
                        },
                        {
                            "code": "visionTherapist"
                        },
                        {
                            "code": "occupationalTherapist"
                        },
                        {
                            "code": "staff"
                        }
                    ],
                    "memberEnrollmentMappings": [
                        {
                            "code": "student"
                        },
                        {
                            "code": "substitute"
                        },
                        {
                            "code": "aide"
                        },
                        {
                            "code": "proctor"
                        },
                        {
                            "code": "teacherAssistant"
                        },
                        {
                            "code": "paraprofessional"
                        },
                        {
                            "code": "physicalTherapist"
                        },
                        {
                            "code": "speechTherapist"
                        },
                        {
                            "code": "visionTherapist"
                        },
                        {
                            "code": "occupationalTherapist"
                        },
                        {
                            "code": "staff"
                        }
                    ]
                }
            }
        },
        {
            "@odata.type": "#microsoft.graph.industryData.administrativeUnitProvisioningFlow",
            "id": "7b355e84-0af2-42fd-d392-08dc4ac68cf2",
            "createdDateTime": "2024-03-25T22:29:05.4272368Z",
            "lastModifiedDateTime": "2024-03-25T22:29:05.4272368Z",
            "readinessStatus": "disabled",
            "creationOptions": {
                "createBasedOnOrg": true,
                "createBasedOnOrgPlusRoleGroup": true
            }
        },
        {
            "@odata.type": "#microsoft.graph.industryData.userProvisioningFlow",
            "id": "dfeec276-d507-4008-d393-08dc4ac68cf2",
            "createdDateTime": "2024-03-25T22:29:10.0687495Z",
            "lastModifiedDateTime": "2024-03-25T22:29:10.0687495Z",
            "readinessStatus": "disabled",
            "createUnmatchedUsers": true,
            "managementOptions": {
                "additionalAttributes": [
                    "userGradeLevel"
                ],
                "additionalOptions": {
                    "markAllStudentsAsMinors": true,
                    "allowStudentContactAssociation": false,
                    "studentAgeGroup": "minor"
                }
            },
            "creationOptions": {
                "configurations": [
                    {
                        "licenseSkus": [
                            "world-class"
                        ],
                        "defaultPasswordSettings": {
                            "@odata.type": "#microsoft.graph.industryData.simplePasswordSettings",
                            "password": "***************"
                        },
                        "roleGroup@odata.context": "https://graph.microsoft.com/beta/$metadata#external/industryData/outboundProvisioningFlowSets('8c33d025-5e64-4550-2aa3-08dc4ac66fca')/provisioningFlows('dfeec276-d507-4008-d393-08dc4ac68cf2')/microsoft.graph.industryData.userProvisioningFlow/creationOptions/configurations/roleGroup/$entity",
                        "roleGroup": {
                            "id": "students",
                            "displayName": "Students",
                            "roles": [
                                {
                                    "code": "student"
                                }
                            ]
                        }
                    },
                    {
                        "licenseSkus": [
                            "Strategist"
                        ],
                        "defaultPasswordSettings": {
                            "@odata.type": "#microsoft.graph.industryData.simplePasswordSettings",
                            "password": "***************"
                        },
                        "roleGroup@odata.context": "https://graph.microsoft.com/beta/$metadata#external/industryData/outboundProvisioningFlowSets('8c33d025-5e64-4550-2aa3-08dc4ac66fca')/provisioningFlows('dfeec276-d507-4008-d393-08dc4ac68cf2')/microsoft.graph.industryData.userProvisioningFlow/creationOptions/configurations/roleGroup/$entity",
                        "roleGroup": {
                            "id": "staff",
                            "displayName": "Staff",
                            "roles": [
                                {
                                    "code": "adjunct"
                                },
                                {
                                    "code": "administrator"
                                },
                                {
                                    "code": "advisor"
                                },
                                {
                                    "code": "affiliate"
                                },
                                {
                                    "code": "aide"
                                },
                                {
                                    "code": "alumni"
                                },
                                {
                                    "code": "assistant"
                                },
                                {
                                    "code": "chair"
                                },
                                {
                                    "code": "coach"
                                },
                                {
                                    "code": "faculty"
                                },
                                {
                                    "code": "instructor"
                                },
                                {
                                    "code": "itAdmin"
                                },
                                {
                                    "code": "lecturer"
                                },
                                {
                                    "code": "nurse"
                                },
                                {
                                    "code": "occupationalTherapist"
                                },
                                {
                                    "code": "officeStaff"
                                },
                                {
                                    "code": "paraprofessional"
                                },
                                {
                                    "code": "physicalTherapist"
                                },
                                {
                                    "code": "principal"
                                },
                                {
                                    "code": "proctor"
                                },
                                {
                                    "code": "professor"
                                },
                                {
                                    "code": "researcher"
                                },
                                {
                                    "code": "specialServices"
                                },
                                {
                                    "code": "speechTherapist"
                                },
                                {
                                    "code": "staff"
                                },
                                {
                                    "code": "substitute"
                                },
                                {
                                    "code": "teacher"
                                },
                                {
                                    "code": "teacherAssistant"
                                },
                                {
                                    "code": "visionTherapist"
                                }
                            ]
                        }
                    }
                ]
            }
        }
    ]
}
```
