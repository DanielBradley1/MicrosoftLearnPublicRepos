<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/api-discovery-script -->
<!-- Sitemap-Last-Modified: 2024-10-23 -->

# Generate block script - cloud discovery API

Note

This request is not available for Microsoft 365 Cloud App Security.

Run the GET request to get a block script for your network appliance.

## HTTP request

```rest
GET /api/discovery_block_scripts/
```

## Request URL parameters

| Parameter | Description |
| --- | --- |
| format | The format of the network appliance. |

The following formats are currently supported:

| Appliance | Format |
| --- | --- |
| BlueCoat ProxySG | 102 |
| Cisco ASA | 104 |
| Fortinet FortiGate | 108 |
| Juniper SRX | 129 |
| Palo Alto | 112 |
| Websense | 135 |
| Zscaler | 120 |

Note

If you can't find your appliance, generate a block script manually using the portal.

## Response

This request returns the block script as text.

## Example

### Request

Here is an example of the request.

Bearer token:

```rest
curl -XGET -H "Authorization:Bearer <your_token>" "https://<tenant_id>.<tenant_region>.portal.cloudappsecurity.com/api/discovery_block_scripts/?format=102&type=banned"
```

Legacy token:

```rest
curl -XGET -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.portal.cloudappsecurity.com/api/discovery_block_scripts/?format=102&type=banned"
```

Note

This API supports both `token` and `bearer` options. When using the `token` option, enter the token you generated in the **API Token** tab. When using the `bearer` option, provide the token you generated through Azure AD Graph.

### Response example

```text
url.domain=application.com deny
url.domain=application.be deny
url.domain=application.co deny
```

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
