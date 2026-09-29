<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/api-data-enrichment-create -->
<!-- Sitemap-Last-Modified: 2025-11-05 -->

# Create IP address range - Data Enrichment API

Run the POST request to add a new IP address range.

## HTTP request

```rest
POST /api/v1/subnet/create_rule/
```

## Request BODY parameters

| Parameter | Description |
| --- | --- |
| name | The unique name of the range |
| category | The ID of the range category. Providing a category helps you easily recognize activities from interesting IP addresses. Possible values include:  <br>  <br>**1**: Corporate  <br>**2**: Administrative  <br>**3**: Risky  <br>**4**: VPN  <br>**5**: Cloud provider  <br>**6**: Other |
| subnets | An array of masks as strings \(IPv4 / IPv6\) |
| organization \(Optional\) | The registered ISP |
| tags \(Optional\) | An array of new or existing objects including the tag name, ID, description, name template, and tenant ID |

## Example

### Request

Here's an example of the request.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" -H "Content-Type: application/json" "https://<tenant_id>.<tenant_region>.portal.cloudappsecurity.com/api/v1/subnet/create_rule/" -d '{
  "name":"range name",
  "category":5,
  "organization":"Microsoft",
  "subnets":[
    "192.168.1.0/24",
    "192.168.2.0/16"
  ],
  "tags":[
    "existing tag"
  ]
}'
```

### Response

Returns the ID of the new range as a string.

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
