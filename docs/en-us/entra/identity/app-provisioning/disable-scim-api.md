<!-- Source: https://learn.microsoft.com/en-us/entra/identity/app-provisioning/disable-scim-api -->
<!-- Sitemap-Last-Modified: 2026-03-31 -->

# Disable the SCIM Provisioning API

If you no longer need programmatic SCIM access, you can turn off the SCIM Provisioning API to stop all API access and billing.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. In the left navigation, expand **ID Governance** and select **Dashboard**.
3. On the Dashboard page, locate the **SCIM Provisioning API** tile and select **Edit**.
4. In the **SCIM Provisioning API** pane, select **Turn off**.
5. Confirm the action when prompted. After the feature is turned off, all SCIM API calls to the tenant return an error and billing stops.

## Verify that the SCIM API is disabled

Use the following steps to validate that the disable operation was successful.

1. Obtain an app-only access token that previously worked for SCIM API calls.
2. Send a GET request to any SCIM endpoint. For example, call the user read endpoint:

```http
GET https://graph.microsoft.com/rp/scim/users/{id}
Authorization: Bearer {token}
Accept: application/json
```

1. Confirm that the API returns **HTTP 400 Bad Request**.
2. Confirm that the response includes an error message similar to the following:

```text
No 'scimapiconsumptions' resource found for TenantId: {tenantId}. Please ensure 'SCIM Provisioning API' feature is enabled and only one 'scimapiconsumptions' resource exists.
```

If you receive this error, the SCIM APIs are now disabled in your tenant.

## Next steps

- [Enable the SCIM Provisioning API](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/enable-scim-api) – Learn how to enable the SCIM Provisioning API and set up credentials.
- [Microsoft Entra ID SCIM API reference](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/entra-id-scim-api-reference) – Learn about the supported SCIM API endpoints, request formats, and constraints.
