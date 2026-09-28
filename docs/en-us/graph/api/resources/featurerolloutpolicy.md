<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/featurerolloutpolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-08 -->

# featureRolloutPolicy resource type

Namespace: microsoft.graph

Represents a feature rollout policy associated with a directory object. Creating a feature rollout policy helps tenant administrators to pilot features of Microsoft Entra ID with a specific group before enabling features for entire organization. This minimizes the impact and helps administrators to test and rollout authentication related features gradually.

The following are limitations of feature rollout:

- Each feature supports a maximum of 10 groups.
- The **appliesTo** field only supports groups.
- Dynamic groups and nested groups are not supported.

For more information about staged rollout, see [How to configure staged rollout in Microsoft Entra ID](https://www.youtube.com/watch?v=LFTE1epYDFQ).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/featurerolloutpolicies-list?view=graph-rest-1.0) | [featureRolloutPolicy](https://learn.microsoft.com/en-us/graph/api/resources/featurerolloutpolicy?view=graph-rest-1.0) | Retrieve a list of featureRolloutPolicy objects. |
| [Get](https://learn.microsoft.com/en-us/graph/api/featurerolloutpolicy-get?view=graph-rest-1.0) | [featureRolloutPolicy](https://learn.microsoft.com/en-us/graph/api/resources/featurerolloutpolicy?view=graph-rest-1.0) | Retrieve the properties and relationships of featurerolloutpolicy object. |
| [Create](https://learn.microsoft.com/en-us/graph/api/featurerolloutpolicies-post?view=graph-rest-1.0) | [featureRolloutPolicy](https://learn.microsoft.com/en-us/graph/api/resources/featurerolloutpolicy?view=graph-rest-1.0) | Create a new featureRolloutPolicy object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/featurerolloutpolicy-update?view=graph-rest-1.0) | [featureRolloutPolicy](https://learn.microsoft.com/en-us/graph/api/resources/featurerolloutpolicy?view=graph-rest-1.0) | Update the properties of featurerolloutpolicy object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/featurerolloutpolicy-delete?view=graph-rest-1.0) | None | Delete a featureRolloutPolicy object. |
| [Create applies to](https://learn.microsoft.com/en-us/graph/api/featurerolloutpolicy-post-appliesto?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Assign a directoryObject to feature rollout. |
| [Delete applies to](https://learn.microsoft.com/en-us/graph/api/featurerolloutpolicy-delete-appliesto?view=graph-rest-1.0) | None | Remove a directoryObject from feature rollout. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A description for this feature rollout policy. |
| displayName | String | The display name for this feature rollout policy. |
| feature | stagedFeatureName | The possible values are: `passthroughAuthentication`, `seamlessSso`, `passwordHashSync`, `emailAsAlternateId`, `unknownFutureValue`, `certificateBasedAuthentication`, `multiFactorAuthentication`. Use the `Prefer: include-unknown-enum-members` request header to get the following value or values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `certificateBasedAuthentication`, `multiFactorAuthentication`. For more information about the prerequisites for the enabled features, see [Prerequisites for enabled features](#prerequisites-for-enabled-features). |
| id | String | Read-only. |
| isAppliedToOrganization | Boolean | Indicates whether this feature rollout policy should be applied to the entire organization. |
| isEnabled | Boolean | Indicates whether the feature rollout is enabled. |

### Prerequisites for enabled features

The following are prerequisites for each of the features that are currently supported for rollout using this rollout policy.

#### Passthrough Authentication

- Identify a server running Windows Server 2012 R2 or later where you want the [PassthroughAuthentication](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-pta) Agent to run. Ensure that the server is domain-joined, can authenticate selected users with Active Directory, and can communicate with Microsoft Entra ID on outbound ports / URLs.
- [Download](https://aka.ms/getauthagent) & install the Microsoft Entra Connect Authentication Agent on the server.
- To enable high availability, install additional Authentication Agents on other servers as described [here](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-pta-quick-start#step-4-ensure-high-availability).
- Ensure that you've configured your [Smart Lockout](https://learn.microsoft.com/en-us/azure/active-directory/authentication/howto-password-smart-lockout) settings appropriately. This is to ensure that your users' on-premises Active Directory accounts don't get locked out by bad actors.

#### SeamlessSso

- Enable [SeamlessSso](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-sso) for the AD forests based on [these](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/tshoot-connect-sso#manual-reset-of-the-feature) instructions.

#### PasswordHashSync

- Enable [PasswordHashSync](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/whatis-phs) from the "Optional features" page in Microsoft Entra Connect.

#### EmailAsAlternateId

- Associate alternate email with user accounts.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appliesTo | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Nullable. Specifies a list of directoryObject resources that feature is enabled for. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "description": "String",
  "displayName": "String",
  "feature": "string",
  "id": "String (identifier)",
  "isAppliedToOrganization": false,
  "isEnabled": true
}
```

## Related content

- [Migrate to cloud authentication using Staged Rollout](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-staged-rollout)
