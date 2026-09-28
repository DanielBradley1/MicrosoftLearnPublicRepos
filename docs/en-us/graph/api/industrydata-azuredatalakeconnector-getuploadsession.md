<!-- Source: https://learn.microsoft.com/en-us/graph/api/industrydata-azuredatalakeconnector-getuploadsession?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# azureDataLakeConnector: getUploadSession

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Retrieve an upload session used to supply file-based data to an inbound flow.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | IndustryData-DataConnector.Upload | IndustryData-DataConnector.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | IndustryData-DataConnector.ReadWrite.All | IndustryData-DataConnector.Upload |

## HTTP request

```http
GET /external/industryData/dataConnectors/{industryDataConnectorId}/microsoft.graph.industryData.azureDataLakeConnector/getUploadSession
```

## Function parameters

In the request URL, provide the following query parameters with values.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| resetSession | Boolean | `True` indicates that a new [microsoft.graph.industryData.fileUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-fileuploadsession?view=graph-rest-beta) with an empty container is returned. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [microsoft.graph.industryData.fileUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-fileuploadsession?view=graph-rest-beta) in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/beta/external/industryData/dataConnectors/51dca0a0-85f6-4478-f526-08daddab2271/microsoft.graph.industryData.azureDataLakeConnector/getUploadSession
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let fileUploadSession = await client.api('/external/industryData/dataConnectors/51dca0a0-85f6-4478-f526-08daddab2271/microsoft.graph.industryData.azureDataLakeConnector/getUploadSession')
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
Content-Type: application/json

{
  "containerExpirationDateTime": "2022-12-16T06:07:39.3096785Z",
  "containerId": "40fe691e-a4b8-4b47-8c86-08daddab241e",
  "sessionExpirationDateTime": "2022-12-14T20:07:39.5792917Z",
  "sessionUrl": "https://azureBlobSas.example/"
}
```
