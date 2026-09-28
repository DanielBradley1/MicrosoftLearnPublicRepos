<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/phoneoptions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-02-05 -->

# phoneOptions resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines the calling codes to opt in and opt out for telephony services in [external identities user flow for Microsoft Entra workforce or external tenants](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-beta). These codes are displayed on the user flow start-up step up for the customer to select from.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultRegions | Int16 collection | A read-only, Microsoft-defined list of regions that already enable MFA. For more information, see the following \[list of countries\]\(/entra/external-id/customers/how-to-region-code-opt in\). |
| excludeRegions | Int16 collection | A numbers-only set representing the region telecom codes to prevent or disable the telephony service. Validates against current International Subscriber Dialing \(ISD\) country codes where the maximum code length is 4. Values must be non-null. |
| includeAdditionalRegions | Int16 collection | A numbers-only set representing the country codes that can be manually added to enable telephony service in those regions, in addition to the list of countries that are already enabled. For more information about regions that require opt in, see \[Regions that need to opt in for MFA telephony verification\]\(/entra/external-id/customers/how-to-region-code-opt in\). Validates against current International Subscriber Dialing \(ISD\) country codes where the maximum code length is 4. Values must be positive integers and can't overlap with 'excludeRegions'. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.phoneOptions",
  "defaultRegions": [
    "Integer"
  ],
  "includeAdditionalRegions": [
    "Integer"
  ],
  "excludeRegions": [
    "Integer"
  ]
}
```
