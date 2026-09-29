<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/api-entities -->
<!-- Sitemap-Last-Modified: 2024-12-10 -->

# Entities API

Note

This API is not available for Microsoft 365 Cloud App Security.

The Entities API provides you with basic information about the users and accounts using your organization's cloud apps, allowing you to understand service use patterns.

The following lists the supported requests:

- [List entities](https://learn.microsoft.com/en-us/defender-cloud-apps/api-entities-list)
- [Fetch entity](https://learn.microsoft.com/en-us/defender-cloud-apps/api-entities-fetch)
- [Fetch entity tree](https://learn.microsoft.com/en-us/defender-cloud-apps/api-entities-fetch-tree)

## Filters

For information about how filters work, see [Filters](https://learn.microsoft.com/en-us/defender-cloud-apps/api-introduction#filters).

The following table describes the supported filters:

| Filter | Type | Operators | Description |
| --- | --- | --- | --- |
| type | string | eq, neq | Filter entities by their type |
| isAdmin | string | eq | Filter entities that are admins |
| entity | entity pk | eq, neq | Filter entities with specific entities pks. If a user is selected, this filter also returns all of the user's accounts. Example: `[{ "id": "entity-id", "inst": 0 }]` |
| userGroups | string | eq, neq | Filter entities by their associated group IDs |
| app | integer | eq, neq | Filter entities using services with the specified SaaS ID for example: 11770 |
| instance | integer | eq, neq | Filter entities using services with the specified app instances \(SaaS ID and Instance ID\). For example: 11770, 1059065 |
| isExternal | boolean | eq | The entity's affiliation. Possible values include:  <br>  <br>**true**: External  <br>**false**: Internal  <br>**null**: No value |
| domain | string | eq, neq, isset, isnotset | The entity's related domain |
| organization | string | eq, neq, isset, isnotset | Filter entities with the specified organization unit |
| status | string | eq, neq | Filter entities by status. Possible values include:  <br>  <br>**0**: N/A  <br>**1**: Staged  <br>**2**: Active  <br>**3**: Suspended  <br>**4**: Deleted |

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
