<!-- Source: https://learn.microsoft.com/en-us/graph/api/inactiveawsresourcefinding-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# Get inactiveAwsResourceFinding

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Read the properties and relationships of an [inactiveAwsResourceFinding](https://learn.microsoft.com/en-us/graph/api/resources/inactiveawsresourcefinding?view=graph-rest-beta) object, representing an inactive AWS resource.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /identityGovernance/permissionsAnalytics/aws/findings/{id}/microsoft.graph.inactiveAwsResourceFinding
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

If successful, this method returns a `200 OK` response code and an [inactiveAwsResourceFinding](https://learn.microsoft.com/en-us/graph/api/resources/inactiveawsresourcefinding?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/beta/identityGovernance/permissionsAnalytics/aws/findings/MSxJbmFjdGl2ZUF3c1Jlc291cmNlRmluZGluZywxNDA1Ng/microsoft.graph.inactiveAwsResourceFinding
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let inactiveAwsResourceFinding = await client.api('/identityGovernance/permissionsAnalytics/aws/findings/MSxJbmFjdGl2ZUF3c1Jlc291cmNlRmluZGluZywxNDA1Ng/microsoft.graph.inactiveAwsResourceFinding')
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/permissionsAnalytics/aws/findings/microsoft.graph.inactiveAwsResourceFinding/$entity",
    "id": "MSxJbmFjdGl2ZUF3c1Jlc291cmNlRmluZGluZywxNDA1Ng",
    "createdDateTime": "2023-11-02T17:33:02.447118Z",
    "actionSummary": {
        "assigned": 1553,
        "exercised": 0,
        "available": 9925
    },
    "identityDetails": {
        "createdDateTime": null,
        "lastActiveDateTime": null
    },
    "permissionsCreepIndex": {
        "score": 1
    },
    "identity": {
        "@odata.type": "#microsoft.graph.awsEc2Instance",
        "id": "YXJuOmF3czplYzI6dXMtZWFzdC0yOjM3NzU5NjEzMTc3NDppbnN0YW5jZS9pLTBhZmEwOTdiMjIzZjRjOTQ5",
        "externalId": "arn:aws:ec2:us-east-2:377596131774:instance/i-0afa097b223f4c949",
        "displayName": "automation-ec2",
        "source": {
            "@odata.type": "#microsoft.graph.awsSource",
            "identityProviderType": "aws",
            "accountId": "377596131774"
        },
        "authorizationSystem": {
            "@odata.type": "#microsoft.graph.awsAuthorizationSystem",
            "authorizationSystemId": "377596131774",
            "authorizationSystemName": "cloudknox-staging",
            "authorizationSystemType": "aws",
            "id": "MSxhd3MsMzc3NTk2MTMxNzc0"
        }
    }
}
```
