<!-- Source: https://learn.microsoft.com/en-us/graph/api/place-patch-places?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-24 -->

# Upsert places

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Upsert one or more [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-beta) objects in async mode. This API allows you to create and update multiple places efficiently in a single request.

For more information on how to use this API, including scenarios, best practices, and concurrency limits, see [Working with the upsert Places API in Microsoft Graph](https://learn.microsoft.com/en-us/graph/places-upsert-overview).

Note

- Operations are retained for 15 days from creation.
- This API has a throttling limit of three calls per second. For more information, see [Microsoft Graph service-specific throttling limits](https://learn.microsoft.com/en-us/graph/throttling-limits).
- All requests require the `OData-Version: 4.01` header.
- Currently, this API doesn’t support the assigned mode for desks or the `isTeamsEnabled` property for rooms.
- For now, the place operation can’t handle a large number of places at once—especially rooms, desks, and workspaces. The current limit is approximately 20–30 rooms, desks, or workspaces.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Place.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Place.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Exchange Administrator* is the least privileged role supported for this operation.

When using application permissions, you must configure the required `TenantPlacesManagement` role \(to manage Places\) and the `MailRecipient` role \(to manage users and mailboxes\). For more information on how to configure these roles, see [Role Based Access Control for Applications in Exchange Online](https://learn.microsoft.com/en-us/exchange/permissions-exo/application-rbac).

## HTTP request

```http
PATCH /places
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| OData-Version | 4.01. Required. |

## Request body

In the request body, supply a JSON representation of the [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-beta) delta set.

The same properties can be specified as when you [create](https://learn.microsoft.com/en-us/graph/api/place-post?view=graph-rest-beta) or [update](https://learn.microsoft.com/en-us/graph/api/place-update?view=graph-rest-beta) a **place** object.

## Response

If successful, this method returns a `202 Accepted` response code and an operation URL in the `Location` response header that you can use to [get](https://learn.microsoft.com/en-us/graph/api/place-getoperation?view=graph-rest-beta) the operation.

## Example

### Request

The following example shows a request that combines multiple operations, including updating an existing building, creating new places with a hierarchy, and updating properties:

- Update an existing building to set the display name to `Demo Building A`, enable Wi-Fi, and create a new floor `Demo Floor 1` as a child of the updated building.
- Create a new building `Demo Building B` with a child floor `Demo Floor 1` that contains a new section `Demo Section A` with an existing desk and a new room `Demo Room 1`.
- Create a new workspace in reservable mode under an existing parent.
- Update the display name of an existing section.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PATCH https://graph.microsoft.com/beta/places
Content-Type: application/json
OData-Version: 4.01

{
  "@context": "#$delta",
  "value": [
    {
      "@odata.type": "microsoft.graph.building",
      "id": "25e5905a-7fee-4f36-ba31-29e85c14bf18",
      "displayName": "Demo Building A",
      "hasWifi": true,
      "children@delta": [
        {
          "@odata.type": "microsoft.graph.floor",
          "displayName": "Demo Floor 1"
        }
      ]
    },
    {
      "@odata.type": "microsoft.graph.building",
      "displayName": "Demo Building B",
      "children@delta": [
        {
          "@odata.type": "microsoft.graph.floor",
          "displayName": "Demo Floor 1",
          "children@delta": [
            {
              "@odata.type": "microsoft.graph.section",
              "displayName": "Demo Section A",
              "children@delta": [
                {
                  "@odata.type": "#microsoft.graph.desk",
                  "id": "211ffb37-e880-475a-b73a-43f484609536"
                },
                {
                  "@odata.type": "#microsoft.graph.room",
                  "displayName": "Demo Room 1"
                }
              ]
            }
          ]
        }
      ]
    },
    {
      "@odata.type": "microsoft.graph.workspace",
      "parentId": "2cb2701d-0896-4c69-91bb-582d82d7c68c",
      "displayName": "Demo Workspace 1",
      "mode": {
        "@odata.type": "#microsoft.graph.reservablePlaceMode"
      }
    },
    {
      "@odata.type": "#microsoft.graph.section",
      "id": "2cb2701d-0896-4c69-91bb-582d82d7c68c",
      "displayName": "HR"
    }
  ]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const places = {
  '@context': '#$delta',
  value: [
    {
      '@odata.type': 'microsoft.graph.building',
      id: '25e5905a-7fee-4f36-ba31-29e85c14bf18',
      displayName: 'Demo Building A',
      hasWifi: true,
      'children@delta': [
        {
          '@odata.type': 'microsoft.graph.floor',
          displayName: 'Demo Floor 1'
        }
      ]
    },
    {
      '@odata.type': 'microsoft.graph.building',
      displayName: 'Demo Building B',
      'children@delta': [
        {
          '@odata.type': 'microsoft.graph.floor',
          displayName: 'Demo Floor 1',
          'children@delta': [
            {
              '@odata.type': 'microsoft.graph.section',
              displayName: 'Demo Section A',
              'children@delta': [
                {
                  '@odata.type': '#microsoft.graph.desk',
                  id: '211ffb37-e880-475a-b73a-43f484609536'
                },
                {
                  '@odata.type': '#microsoft.graph.room',
                  displayName: 'Demo Room 1'
                }
              ]
            }
          ]
        }
      ]
    },
    {
      '@odata.type': 'microsoft.graph.workspace',
      parentId: '2cb2701d-0896-4c69-91bb-582d82d7c68c',
      displayName: 'Demo Workspace 1',
      mode: {
        '@odata.type': '#microsoft.graph.reservablePlaceMode'
      }
    },
    {
      '@odata.type': '#microsoft.graph.section',
      id: '2cb2701d-0896-4c69-91bb-582d82d7c68c',
      displayName: 'HR'
    }
  ]
};

await client.api('/places')
	.version('beta')
	.update(places);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
Location: https://graph.microsoft.com/beta/places/getOperation(id='0f5d3cc5-d1bd-4cba-9b0e-e9ad68527ab5')
```
