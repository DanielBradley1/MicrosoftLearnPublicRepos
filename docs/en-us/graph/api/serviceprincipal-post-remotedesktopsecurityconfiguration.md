<!-- Source: https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-remotedesktopsecurityconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-17 -->

# Create remoteDesktopSecurityConfiguration

Namespace: microsoft.graph

Create a new remoteDesktopSecurityConfiguration object on the servicePrincipal. Use this configuration to enable the Microsoft Entra ID [Remote Desktop Services \(RDS\) authentication protocol](https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-rdpbcgr/dc43f040-d75d-49a9-90c6-0c9999281136) to authenticate a user to [Microsoft Entra joined](https://learn.microsoft.com/en-us/azure/active-directory/devices/concept-directory-join) or [Microsoft Entra hybrid joined](https://learn.microsoft.com/en-us/azure/active-directory/devices/concept-hybrid-join) devices.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Application-RemoteDesktopConfig.ReadWrite.All | Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Application-RemoteDesktopConfig.ReadWrite.All | Directory.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Application Administrator
- Cloud Application Administrator

## HTTP request

```http
POST /servicePrincipals/{servicePrincipalsId}/remoteDesktopSecurityConfiguration
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [remoteDesktopSecurityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0) object.

You can specify the following properties when creating a **remoteDesktopSecurityConfiguration**.

| Property | Type | Description |
| :--- | :--- | :--- |
| isRemoteDesktopProtocolEnabled | Boolean | Whether new Microsoft Entra ID [Remote Desktop Services \(RDS\) authentication protocol](https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-rdpbcgr/dc43f040-d75d-49a9-90c6-0c9999281136) to authenticate a user to [Microsoft Entra joined](https://learn.microsoft.com/en-us/azure/active-directory/devices/concept-directory-join) or [Microsoft Entra hybrid joined](https://learn.microsoft.com/en-us/azure/active-directory/devices/concept-hybrid-join) devices over RDP is enabled or not. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [remoteDesktopSecurityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/servicePrincipals/00af5dfb-85da-4b41-a677-0c6b86dd34f8/remoteDesktopSecurityConfiguration
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.remoteDesktopSecurityConfiguration",
  "isRemoteDesktopProtocolEnabled": true
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const remoteDesktopSecurityConfiguration = {
  '@odata.type': '#microsoft.graph.remoteDesktopSecurityConfiguration',
  isRemoteDesktopProtocolEnabled: true
};

await client.api('/servicePrincipals/00af5dfb-85da-4b41-a677-0c6b86dd34f8/remoteDesktopSecurityConfiguration')
	.post(remoteDesktopSecurityConfiguration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.remoteDesktopSecurityConfiguration",
  "id": "ca738153-c98a-f822-a7d1-5a6e1058462b",
  "isRemoteDesktopProtocolEnabled": true
}
```
