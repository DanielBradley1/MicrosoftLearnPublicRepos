<!-- Source: https://learn.microsoft.com/en-us/graph/api/onpremisespublishingprofile-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Update onPremisesPublishingProfile

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of an [onPremisesPublishingProfile](https://learn.microsoft.com/en-us/graph/api/resources/onpremisespublishingprofile?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Directory.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PATCH /onPremisesPublishingProfiles/{profile-id}/hybridAgentUpdaterConfiguration
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply the values for relevant fields to update. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance, don't include existing values that haven't changed.

| Property | Type | Description |
| :--- | :--- | :--- |
| hybridAgentUpdaterConfiguration | hybridAgentUpdaterConfiguration | Represents [hybridAgentUpdaterConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/hybridagentupdaterconfiguration?view=graph-rest-beta). |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Example 1: Update updateWindow in the hybridAgentUpdaterConfiguration

The following example updates the **updateWindow** in the **hybridAgentUpdaterConfiguration**.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PATCH https://graph.microsoft.com/beta/onPremisesPublishingProfiles/provisioning/hybridAgentUpdaterConfiguration
Content-Type: application/json

{
   "updateWindow" :
{
      "updateWindowStartTime" : "0:00:00",
      "updateWindowEndTime" : "23:59:00"
  }
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const hybridAgentUpdaterConfiguration = {
   updateWindow: 
{
      updateWindowStartTime: '0:00:00',
      updateWindowEndTime: '23:59:00'
  }
};

await client.api('/onPremisesPublishingProfiles/provisioning/hybridAgentUpdaterConfiguration')
	.version('beta')
	.update(hybridAgentUpdaterConfiguration);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 2: Update deferUpdate in the hybridAgentUpdaterConfiguration

The following example updates **deferUpdate** in the **hybridAgentUpdaterConfiguration**.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)

```http
PATCH https://graph.microsoft.com/beta/onPremisesPublishingProfiles/provisioning/hybridAgentUpdaterConfiguration
Content-Type: application/json

{
    "deferUpdate" : "2018-08-20T12:00"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const hybridAgentUpdaterConfiguration = {
    deferUpdate: '2018-08-20T12:00'
};

await client.api('/onPremisesPublishingProfiles/provisioning/hybridAgentUpdaterConfiguration')
	.version('beta')
	.update(hybridAgentUpdaterConfiguration);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 3: Update allowUpdateConfigurationOverride in the hybridAgentUpdaterConfiguration

The following example updates **allowUpdateConfigurationOverride** in the **hybridAgentUpdaterConfiguration**.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [JavaScript](#tabpanel_3_javascript)

```http
PATCH https://graph.microsoft.com/beta/onPremisesPublishingProfiles/provisioning/hybridAgentUpdaterConfiguration
Content-Type: application/json

{
    "allowUpdateConfigurationOverride" : false
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const hybridAgentUpdaterConfiguration = {
    allowUpdateConfigurationOverride: false
};

await client.api('/onPremisesPublishingProfiles/provisioning/hybridAgentUpdaterConfiguration')
	.version('beta')
	.update(hybridAgentUpdaterConfiguration);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```
