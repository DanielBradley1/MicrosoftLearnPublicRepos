<!-- Source: https://learn.microsoft.com/en-us/graph/api/entrarecoveryservices-snapshot-post-recoveryjobs?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-19 -->

# Create recoveryJob

Namespace: microsoft.graph.entraRecoveryServices

Create a new [recoveryJob](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjob?view=graph-rest-1.0) object to restore the tenant's directory objects to a specific snapshot state. This operation follows the resource-based long running operation \(RELO\) pattern and returns a `202 Accepted` response with a `Location` header pointing to the job resource.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EntraBackup.ReadWrite.Recovery | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Entra Backup Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /directory/recovery/snapshots/{snapshot-id}/recoveryJobs
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, optionally supply a JSON representation with the following property.

| Property | Type | Description |
| :--- | :--- | :--- |
| filteringCriteria | [microsoft.graph.entraRecoveryServices.recoveryJobFilteringCriteriaBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobfilteringcriteriabase?view=graph-rest-1.0) | Optional. Filtering criteria to scope the job to specific entity types or entity IDs. If not specified, all supported entities are included. Use `@odata.type` to specify the derived type: `#microsoft.graph.entraRecoveryServices.recoveryJobEntityNamesFilter` or `#microsoft.graph.entraRecoveryServices.recoveryJobEntityNameAndIdsFilter`. |

## Response

If successful, this method returns a `202 Accepted` response code with a `Location` header pointing to the created job resource.

## Examples

### Example 1: Create a recovery job without filtering

The following example creates a recovery job for all changes.

#### Request

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryJobs
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryJobs')
	.post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

```http
HTTP/1.1 202 Accepted
Location: https://graph.microsoft.com/v1.0/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryJobs/3f4a6b60-7c1e-4e7c-9c7b-13f8d44b20c4
```

### Example 2: Create a recovery job filtered by entity types

The following example creates a recovery job for only user entity changes.

#### Request

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)

```http
POST https://graph.microsoft.com/v1.0/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryJobs
Content-Type: application/json

{
  "filteringCriteria": {
    "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryJobEntityNamesFilter",
    "entityTypes": [
      "user"
    ]
  }
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const recoveryJob = {
  filteringCriteria: {
    '@odata.type': '#microsoft.graph.entraRecoveryServices.recoveryJobEntityNamesFilter',
    entityTypes: [
      'user'
    ]
  }
};

await client.api('/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryJobs')
	.post(recoveryJob);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

```http
HTTP/1.1 202 Accepted
Location: https://graph.microsoft.com/v1.0/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryJobs/3f4a6b60-7c1e-4e7c-9c7b-13f8d44b20c4
```

### Example 3: Create a recovery job filtered by specific entity IDs

The following example creates a recovery job for specific users and groups.

#### Request

- [HTTP](#tabpanel_3_http)
- [JavaScript](#tabpanel_3_javascript)

```http
POST https://graph.microsoft.com/v1.0/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryJobs
Content-Type: application/json

{
  "filteringCriteria": {
    "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryJobEntityNameAndIdsFilter",
    "filterValues": [
      {
        "entityType": "user",
        "entityIds": [
          "52330fde-895a-4a99-ae59-1c35c2a263e9",
          "0c503c02-5554-4d59-9fcc-69736618fb8f"
        ]
      },
      {
        "entityType": "group",
        "entityIds": [
          "04181a71-a18d-4eee-94da-a77e7eb6520b",
          "2c888900-a7e8-4a01-ada5-17c04b29e8ec"
        ]
      }
    ]
  }
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const recoveryJob = {
  filteringCriteria: {
    '@odata.type': '#microsoft.graph.entraRecoveryServices.recoveryJobEntityNameAndIdsFilter',
    filterValues: [
      {
        entityType: 'user',
        entityIds: [
          '52330fde-895a-4a99-ae59-1c35c2a263e9',
          '0c503c02-5554-4d59-9fcc-69736618fb8f'
        ]
      },
      {
        entityType: 'group',
        entityIds: [
          '04181a71-a18d-4eee-94da-a77e7eb6520b',
          '2c888900-a7e8-4a01-ada5-17c04b29e8ec'
        ]
      }
    ]
  }
};

await client.api('/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryJobs')
	.post(recoveryJob);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

```http
HTTP/1.1 202 Accepted
Location: https://graph.microsoft.com/v1.0/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryJobs/fa0f72f4-68e8-4625-846f-38865c49a086
```
