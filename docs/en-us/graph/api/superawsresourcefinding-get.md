<!-- Source: https://learn.microsoft.com/en-us/graph/api/superawsresourcefinding-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# Get superAwsResourceFinding

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Read the properties and relationships of a [superAwsResourceFinding](https://learn.microsoft.com/en-us/graph/api/resources/superawsresourcefinding?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /identityGovernance/permissionsAnalytics/aws/findings/{id}/microsoft.graph.superAwsResourceFinding
```

## Optional query parameters

This method doesn't support OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [superAwsResourceFinding](https://learn.microsoft.com/en-us/graph/api/resources/superawsresourcefinding?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/beta/identityGovernance/permissionsAnalytics/aws/findings/c3VwZXJSZXNvdXJjZUZpbmRpbmc0/microsoft.graph.superAwsResourceFinding
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let superAwsResourceFinding = await client.api('/identityGovernance/permissionsAnalytics/aws/findings/c3VwZXJSZXNvdXJjZUZpbmRpbmc0/microsoft.graph.superAwsResourceFinding')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/identityGovernance/$metadata#permissionsAnalytics/aws/findings/microsoft.graph.superAwsResourceFinding",
  "value": [
    {
      "@odata.type": "graph.superAwsResourceFinding",
      "id": "c3VwZXJSZXNvdXJjZUZpbmRpbmc0",
      "identity": {
          "@odata.type": "graph.awsEc2Instance",
          "id":"YXJuOmF3czplYzI6dXMtd2VzdC0xOjM3NzU5NjEzMTc3NDppbnN0YW5jZS9pLTA5MWM5OTAyMDc0NTY5ZDc0",
          "externalId": "arn:aws:ec2:us-west-1:377596131774:instance/i-091c9902074569d74",
          "displayName": "do not terminate* parag_notion_ubuntu",
          "source": {
            "@odata.type": "graph.awsSource",
            "identityProviderType": "aws",
            "accountId": "377596131774"
          },
          "authorizationSystem": {
            "@odata.type": "graph.awsAuthorizationSystem",
            "id": "{Id}",
            "authorizationSystemId": "377596131774",
            "authorizationSystemName": "cloudknox-staging",
            "authorizationSystemType": "aws"
          }
      },
      "actionSummary": {
        "assigned": 170,
        "exercised": 0,
        "available": 10542
      },
      "identityDetails": {
        "createdDateTime": "String (timestamp)",
        "lastActiveDateTime": "String (timestamp)"
      },
      "permissionsCreepIndex": {
        "score": 1
      },
      "createdDateTime": "2020-10-11T20:11:45.6711Z",
      "identityDetails": {
        "createdDateTime": "2018-04-12T20:34:24Z",
        "lastActiveDateTime": "2018-10-30T03:21:05Z"
      }
    }
  ]
}
```
