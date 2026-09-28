<!-- Source: https://learn.microsoft.com/en-us/graph/api/inheritablepermission-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-24 -->

# Update inheritablePermission

Namespace: microsoft.graph

Update the properties of an [inheritablePermission](https://learn.microsoft.com/en-us/graph/api/resources/inheritablepermission?view=graph-rest-1.0) object on an agent identity blueprint. When moving to a more restrictive inheritance pattern, such as from `allAllowedScopes` to `enumeratedScopes` or `noScopes`, any agent identities that require access will require new consent grant to acquire the newly restricted scopes.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentIdentityBlueprint.ReadWrite.All | Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentIdentityBlueprint.ReadWrite.All | Directory.ReadWrite.All |

Important

- A principal who creates an agent identity blueprint or blueprint principal is automatically assigned as the owner.
- Owners can create and modify agent identities associated with a blueprint they own without being assigned an Agent ID role.
- For nonowners to call this API in delegated scenarios using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference). This operation supports the following least-privileged built-in role:

  - [Agent ID Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-administrator)

## HTTP request

```http
PATCH /applications/{id}/microsoft.graph.agentIdentityBlueprint/inheritablePermissions/{resourceAppId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| inheritableScopes | [inheritableScopes](https://learn.microsoft.com/en-us/graph/api/resources/inheritablescopes?view=graph-rest-1.0) | Inheritance pattern applied to delegated permission scopes for the agent identity blueprint. Required. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Example 1: Update inheritablePermission to use allAllowedScopes pattern

This example updates an existing inheritablePermission to use the allAllowedScopes inheritance pattern, allowing all delegated permission scopes from the resource application to be inheritable by agent identities.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PATCH https://graph.microsoft.com/v1.0/applications/bc057821-f236-49d6-9f2c-1ebf43e9437a/microsoft.graph.agentIdentityBlueprint/inheritablePermissions/00000003-0000-0ff1-ce00-000000000000
Content-Type: application/json

{
  "inheritableScopes": {
    "@odata.type": "microsoft.graph.allAllowedScopes"
  }
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const inheritablePermission = {
  inheritableScopes: {
    '@odata.type': 'microsoft.graph.allAllowedScopes'
  }
};

await client.api('/applications/bc057821-f236-49d6-9f2c-1ebf43e9437a/microsoft.graph.agentIdentityBlueprint/inheritablePermissions/00000003-0000-0ff1-ce00-000000000000')
	.update(inheritablePermission);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Update inheritablePermission to use enumeratedScopes pattern

This example updates an existing inheritablePermission to use the enumeratedScopes inheritance pattern, allowing only the specified delegated permission scopes from the resource application to be inheritable by agent identities.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)

```http
PATCH https://graph.microsoft.com/v1.0/applications/bc057821-f236-49d6-9f2c-1ebf43e9437a/microsoft.graph.agentIdentityBlueprint/inheritablePermissions/00000003-0000-0000-c000-000000000000
Content-Type: application/json

{
  "inheritableScopes": {
    "@odata.type": "microsoft.graph.enumeratedScopes",
    "scopes": [
      "User.Read",
      "Mail.Read"
    ]
  }
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const inheritablePermission = {
  inheritableScopes: {
    '@odata.type': 'microsoft.graph.enumeratedScopes',
    scopes: [
      'User.Read',
      'Mail.Read'
    ]
  }
};

await client.api('/applications/bc057821-f236-49d6-9f2c-1ebf43e9437a/microsoft.graph.agentIdentityBlueprint/inheritablePermissions/00000003-0000-0000-c000-000000000000')
	.update(inheritablePermission);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 3: Update inheritablePermission to use noScopes pattern

This example updates an existing inheritablePermission to use the noScopes inheritance pattern, preventing any delegated permission scopes from the resource application from being inheritable by agent identities.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [JavaScript](#tabpanel_3_javascript)

```http
PATCH https://graph.microsoft.com/v1.0/applications/bc057821-f236-49d6-9f2c-1ebf43e9437a/microsoft.graph.agentIdentityBlueprint/inheritablePermissions/00000003-0000-0000-c000-000000000000
Content-Type: application/json

{
  "inheritableScopes": {
    "@odata.type": "microsoft.graph.noScopes"
  }
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const inheritablePermission = {
  inheritableScopes: {
    '@odata.type': 'microsoft.graph.noScopes'
  }
};

await client.api('/applications/bc057821-f236-49d6-9f2c-1ebf43e9437a/microsoft.graph.agentIdentityBlueprint/inheritablePermissions/00000003-0000-0000-c000-000000000000')
	.update(inheritablePermission);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
