<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-whoisrecord-list-history?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# List history

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Get the history for a [whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisrecord?view=graph-rest-1.0), as represented by a collection of [whoisHistoryRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoishistoryrecord?view=graph-rest-1.0) resources.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ThreatIntelligence.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ThreatIntelligence.Read.All | Not available. |

## HTTP request

```http
GET /security/threatIntelligence/hosts/{hostId}/whois/history
GET /security/threatIntelligence/whoisRecords/{id}/history
```

## Optional query parameters

This method supports the `$count`, `$select`, `$skip`, and `$top` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

| Name | Description |
| :--- | :--- |
| $count | `$count` is supported to return a holistic count of the number of [whoisHistoryRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoishistoryrecord?view=graph-rest-1.0) objects. `$count` is supported as a query parameter \(`?$count=true`\) or as a path parameter \(`/$count`\). |
| $select | `$select` is supported to limit the properties returned in this query. |
| $skip | `$skip` is supported to skip over elements in pages. Combine with `$top` to perform pagination or use the `@odata.nextLink` for server-side pagination. |
| $top | `$top` is supported to limit the number of elements per page. Combine with `$skip` to perform pagination or use the `@odata.nextLink` for server-side pagination. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.security.whoisHistoryRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoishistoryrecord?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/v1.0/security/threatIntelligence/hosts/contoso.com/whois/history
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let history = await client.api('/security/threatIntelligence/hosts/contoso.com/whois/history')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.security.whoisRecord",
      "id": "Y29udG9zby5jb20kJDY5NjQ3ODEyMDc3NDY1NzI0MzM=",
      "expirationDateTime": "2023-08-31T00:00:00Z",
      "registrationDateTime": "2022-07-30T09:43:19Z",
      "firstSeenDateTime": null,
      "lastSeenDateTime": null,
      "lastUpdateDateTime": "2023-06-24T08:34:15.984Z",
      "billing": null,
      "noc": null,
      "zone": null,
      "whoisServer": "rdap.markmonitor.com",
      "domainStatus": "client update prohibited,client transfer prohibited,client delete prohibited",
      "rawWhoisText": "Registrar: \n  Handle: 1891582_DOMAIN_COM-VRSN\n  LDH Name: contoso.com\n  Nameserver: \n    LDH Name: ns1.contoso.com\n    Event: \n      Action: last changed\n...",
      "abuse": {
        "email": "noreply@contoso.com",
        "name": null,
        "organization": null,
        "telephone": "+1.5555555555",
        "fax": null,
        "address": {
          "city": null,
          "countryOrRegion": null,
          "postalCode": null,
          "state": null,
          "street": null
        }
      },
      "admin": {
        "email": "noreply@contoso.com",
        "name": "Domain Administrator",
        "organization": "Contoso Org",
        "telephone": "+1.5555555555",
        "fax": "+1.5555555555",
        "address": {
          "city": "Redmond",
          "countryOrRegion": "US",
          "postalCode": "98052",
          "state": "WA",
          "street": "123 Fake St."
        }
      },
      "registrar": {
        "email": null,
        "name": null,
        "organization": "MarkMonitor Inc.",
        "telephone": null,
        "fax": null,
        "address": null
      },
      "registrant": {
        "email": "noreply@contoso.com",
        "name": "Domain Administrator",
        "organization": "Contoso Corporation",
        "telephone": "+1.5555555555",
        "fax": "+1.5555555555",
        "address": {
          "city": "Redmond",
          "countryOrRegion": "US",
          "postalCode": "98052",
          "state": "WA",
          "street": "123 Fake St."
        }
      },
      "technical": {
        "email": "noreply@contoso.com",
        "name": "Hostmaster",
        "organization": "Contoso Corporation",
        "telephone": "+1.5555555555",
        "fax": "+1.5555555555",
        "address": {
          "city": "Redmond",
          "countryOrRegion": "US",
          "postalCode": "98052",
          "state": "WA",
          "street": "123 Fake St."
        }
      },
      "nameservers": [
        {
          "firstSeenDateTime": null,
          "lastSeenDateTime": null,
          "host": {
            "id": "ns1.contoso-dns.com"
          }
        },
        {
          "firstSeenDateTime": null,
          "lastSeenDateTime": null,
          "host": {
            "id": "ns2.contoso-dns.com"
          }
        },
        {
          "firstSeenDateTime": null,
          "lastSeenDateTime": null,
          "host": {
            "id": "ns3.contoso-dns.com"
          }
        },
        {
          "firstSeenDateTime": null,
          "lastSeenDateTime": null,
          "host": {
            "id": "ns4.contoso-dns.com"
          }
        }
      ],
      "host": {
        "id": "contoso.com"
      }
    }
  ]
}
```
