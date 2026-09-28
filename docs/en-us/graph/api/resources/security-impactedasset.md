<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-impactedasset?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# impactedAsset resource type \(deprecated\)

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

The **impactedAsset** resource type and all derived types are deprecated and will be removed on 2026-10-01. Use [entityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-entitymapping?view=graph-rest-beta) and its derived types via `alertTemplate.entityMappings` instead. See the [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) topic for the new shape.

Represents an asset that was identified in an alert triggered by a [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta).

This type is abstract, and serves as the base type for the following asset types.

- [User](https://learn.microsoft.com/en-us/graph/api/resources/security-impacteduserasset?view=graph-rest-beta)
- [Device](https://learn.microsoft.com/en-us/graph/api/resources/security-impacteddeviceasset?view=graph-rest-beta)
- [Mailbox](https://learn.microsoft.com/en-us/graph/api/resources/security-impactedmailboxasset?view=graph-rest-beta)

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.impactedAsset"
}
```
