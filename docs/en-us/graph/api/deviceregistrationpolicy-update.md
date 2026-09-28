<!-- Source: https://learn.microsoft.com/en-us/graph/api/deviceregistrationpolicy-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-06 -->

# Update deviceRegistrationPolicy

Namespace: microsoft.graph

Update the properties of a [deviceRegistrationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/deviceregistrationpolicy?view=graph-rest-1.0) object. Represents deviceRegistrationPolicy quota restrictions, additional authentication, and authorization policies to register device identities to your organization.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.DeviceConfiguration | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.ReadWrite.DeviceConfiguration | Not available. |

Important

In delegated scenarios with work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role with a supported role permission. The following least privileged role is supported for this operation.

- Cloud Device Administrator

## HTTP request

```http
PUT /policies/deviceRegistrationPolicy
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a [deviceRegistrationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/deviceregistrationpolicy?view=graph-rest-1.0) object with all the updatable properties. The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| userDeviceQuota | Int32 | Required. Specifies the maximum number of devices that a user can have within your organization before blocking new device registrations. Required. |
| multiFactorAuthConfiguration | multiFactorAuthConfiguration | Required. Specifies the authentication policy for a user to complete registration using Microsoft Entra join or Microsoft Entra registered within your organization. The possible values are: `notRequired` or `required`. |
| azureADRegistration | [azureADRegistrationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/azureadregistrationpolicy?view=graph-rest-1.0) | Required. Specifies the authorization policy for controlling registration of new devices using Microsoft Entra registration within your organization. Required. For more information, see [What is a device identity?](https://learn.microsoft.com/en-us/azure/active-directory/devices/overview). If Intune is enabled this property cannot be modified. |
| azureADJoin | [azureADJoinPolicy](https://learn.microsoft.com/en-us/graph/api/resources/azureadjoinpolicy?view=graph-rest-1.0) | Required. Specifies the authorization policy for controlling the registration of new devices using Microsoft Entra join within your organization. For more information, see [What is a device identity?](https://learn.microsoft.com/en-us/azure/active-directory/devices/overview). |
| localAdminPassword | [localAdminPasswordSettings](https://learn.microsoft.com/en-us/graph/api/resources/localadminpasswordsettings?view=graph-rest-1.0) | Required. Specifies the setting for **Local Admin Password Solution \(LAPS\)** within your organization. |

## Response

If successful, this method returns a `200 OK` response code and an updated [deviceRegistrationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/deviceregistrationpolicy?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PUT https://graph.microsoft.com/v1.0/policies/deviceRegistrationPolicy
Content-Type: application/json

{
  "userDeviceQuota": 2,
  "multiFactorAuthConfiguration": "notRequired",
  "azureADRegistration": {
    "isAdminConfigurable": false,
    "allowedToRegister": {
      "@odata.type": "#microsoft.graph.enumeratedDeviceRegistrationMembership",
      "users": ["3c8ef067-8b96-44de-b2ae-557dfa0f97a0"],
      "groups": []
    }
  },
  "azureADJoin": {
    "isAdminConfigurable": true,
    "allowedToJoin": {
      "@odata.type": "#microsoft.graph.allDeviceRegistrationMembership"
    },
    "localAdmins": {
      "enableGlobalAdmins": false,
      "registeringUsers": {
        "@odata.type": "#microsoft.graph.noDeviceRegistrationMembership"
      }
    }
  },
  "localAdminPassword": {
    "isEnabled": true
  }
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const deviceRegistrationPolicy = {
  userDeviceQuota: 2,
  multiFactorAuthConfiguration: 'notRequired',
  azureADRegistration: {
    isAdminConfigurable: false,
    allowedToRegister: {
      '@odata.type': '#microsoft.graph.enumeratedDeviceRegistrationMembership',
      users: ['3c8ef067-8b96-44de-b2ae-557dfa0f97a0'],
      groups: []
    }
  },
  azureADJoin: {
    isAdminConfigurable: true,
    allowedToJoin: {
      '@odata.type': '#microsoft.graph.allDeviceRegistrationMembership'
    },
    localAdmins: {
      enableGlobalAdmins: false,
      registeringUsers: {
        '@odata.type': '#microsoft.graph.noDeviceRegistrationMembership'
      }
    }
  },
  localAdminPassword: {
    isEnabled: true
  }
};

await client.api('/policies/deviceRegistrationPolicy')
	.put(deviceRegistrationPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "deviceRegistrationPolicy",
  "displayName": "Device Registration Policy",
  "description": "Tenant-wide policy that manages intial provisioning controls using quota restrictions, additional authentication and authorization checks",
  "userDeviceQuota": 2,
  "multiFactorAuthConfiguration": "notRequired",
  "azureADRegistration": {
    "isAdminConfigurable": false,
    "allowedToRegister": {
      "@odata.type": "#microsoft.graph.enumeratedDeviceRegistrationMembership",
      "users": ["3c8ef067-8b96-44de-b2ae-557dfa0f97a0"],
      "groups": []
    }
  },
  "azureADJoin": {
    "isAdminConfigurable": true,
    "allowedToJoin": {
      "@odata.type": "#microsoft.graph.allDeviceRegistrationMembership"
    },
    "localAdmins": {
      "enableGlobalAdmins": false,
      "registeringUsers": {
        "@odata.type": "#microsoft.graph.noDeviceRegistrationMembership"
      }
    }
  },
  "localAdminPassword": {
    "isEnabled": true
  }
}
```
