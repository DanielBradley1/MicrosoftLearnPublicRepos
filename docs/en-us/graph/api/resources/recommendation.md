<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-17 -->

# recommendation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a Microsoft Entra ID best practice or improvement action recommended by Microsoft for your Microsoft Entra tenant.

The Microsoft Entra recommendation service runs daily to check your tenant against predefined conditions for every recommendation. If the service detects that a recommendation applies to your tenant, the corresponding recommendation object is generated and its status is set to active.

For more information, see [What is Microsoft Entra recommendations?](https://go.microsoft.com/fwlink/?linkid=2221712).

Inherits from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/directory-list-recommendation?view=graph-rest-beta) | [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) collection | Get a list of the [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/recommendation-get?view=graph-rest-beta) | [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) | Read the properties and relationships of a [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) object. |
| [Postpone](https://learn.microsoft.com/en-us/graph/api/recommendation-postpone?view=graph-rest-beta) | [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) | Mark the status of a [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) object as `postponed` to a specified date and time. |
| [Dismiss](https://learn.microsoft.com/en-us/graph/api/recommendation-dismiss?view=graph-rest-beta) | [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) | Mark the status of a [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) object as `dismissed`. |
| [Complete](https://learn.microsoft.com/en-us/graph/api/recommendation-complete?view=graph-rest-beta) | [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) | Mark the status of a [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) object as `completedByUser`. |
| [Reactivate](https://learn.microsoft.com/en-us/graph/api/recommendation-reactivate?view=graph-rest-beta) | [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) | Mark the status of a [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) object as `active`. |
| [Mark planned](https://learn.microsoft.com/en-us/graph/api/recommendation-markplanned?view=graph-rest-beta) | [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) | Mark the status of a [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) object as `planned`. |
| [Accept risk](https://learn.microsoft.com/en-us/graph/api/recommendation-acceptrisk?view=graph-rest-beta) | [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) | Mark the status of a [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) object as `riskAccepted`. |
| [Apply alternate mitigation](https://learn.microsoft.com/en-us/graph/api/recommendation-applyalternatemitigation?view=graph-rest-beta) | [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) | Mark the status of a [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) object as `alternateMitigation`. |
| [Add tag](https://learn.microsoft.com/en-us/graph/api/recommendation-addtag?view=graph-rest-beta) | [recommendationTag](https://learn.microsoft.com/en-us/graph/api/resources/recommendationtag?view=graph-rest-beta) | Add a user-defined tag to a [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta). |
| [Remove tag](https://learn.microsoft.com/en-us/graph/api/recommendation-removetag?view=graph-rest-beta) | [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) | Remove a user-defined tag from a [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta). |
| [Get tenant Secure Score](https://learn.microsoft.com/en-us/graph/api/recommendation-tenantsecurescores?view=graph-rest-beta) | [tenantSecureScore](https://learn.microsoft.com/en-us/graph/api/resources/tenantsecurescore?view=graph-rest-beta) collection | Get historical Secure Score data for your tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionSteps | [actionStep](https://learn.microsoft.com/en-us/graph/api/resources/actionstep?view=graph-rest-beta) collection | List of actions to take to complete a [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta). Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |
| benefits | String | An explanation of why [completing the recommendation](https://learn.microsoft.com/en-us/graph/api/recommendation-complete?view=graph-rest-beta) will benefit you. Corresponds to the *Value* section of a recommendation shown in the Microsoft Entra admin center. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |
| category | recommendationCategory | Indicates the category of intelligent guidance that the recommendation falls under. The possible values are: `identityBestPractice`, `identitySecureScore`, `unknownFutureValue`, `mdiSecureScore`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `mdiSecureScore`. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta).  <br>  <br>Supports `$filter`\(`eq`\). |
| categoryGroup | recommendationCategoryGroup | The business taxonomy group that the [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) belongs to, used to organize recommendations in the Microsoft Entra admin center. The possible values are: `strengthenAuthentication`, `detectAndRespondToThreats`, `enforceLeastPrivilege`, `governAppsCredentialsAndAgents`, `hardenInfrastructure`, `defenderForIdentity`, `unknownFutureValue`. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). Read-only.  <br>  <br>Supports `$filter`\(`eq`\). |
| completedBySystemDateTime | DateTimeOffset | The date and time when the recommendations service verified that the [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) was fully remediated and set its **status** to `completedBySystem`. Is `null` if the recommendation wasn't completed by the system. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |
| completedByUserDateTime | DateTimeOffset | The date and time when the [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) was marked as completed by the user for the current review cycle. Is `null` if the recommendation wasn't completed by a user in the current cycle. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time when the [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) was detected as applicable to your directory. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |
| currentScore | Double | The number of points the tenant has attained. Only applies to [recommendations](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) with **category** set to `identitySecureScore`. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |
| displayName | String | The title of the [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta). Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |
| failedReviewDateTime | DateTimeOffset | The date and time when the recommendations service most recently verified that one or more impacted resources the user marked as completed are still impacted, moving them to `needsMoreAction`. Is mutually exclusive with **remediatedDateTime**. Is `null` when no user-reviewed resource is currently failing verification. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |
| featureAreas | recommendationFeatureAreas collection | The directory feature that the [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) is related to. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta).  <br>  <br>Supports `$filter`\(`eq`\). |
| id | String | The unique identifier for the [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) object generated for your tenant. This is a concatenation of your tenant ID and a Microsoft Entra ID-assigned nickname for the recommendation. For example, `7918d4b5-0442-4a97-be2d-36f9f9962ece_Microsoft.Identity.IAM.Insights.ThirdPartyApps`. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |
| impactStartDateTime | DateTimeOffset | The future date and time when a [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) should be completed. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |
| impactType | String | Indicates the scope of impact of a recommendation. `tenantLevel` indicates that the recommendation impacts the whole tenant. Other possible values include `users`, `apps`. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |
| insights | String | Describes why a recommendation uniquely applies to your directory. Corresponds to the *Description* section of a recommendation shown in the Microsoft Entra admin center. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |
| lastCheckedDateTime | DateTimeOffset | The most recent date and time a [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) was deemed applicable to your directory. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |
| lastModifiedBy | String | Name of the user who last updated the **status** of the [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta). Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time the **status** of a [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) was last updated. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |
| maxScore | Double | The maximum number of points attainable. Only applies to [recommendations](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) with **category** set to `identitySecureScore`. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |
| needsMoreActionResourceCount | Int32 | The number of impacted resources that the user marked as completed and that the recommendations service subsequently verified are still impacted \(moved to `needsMoreAction`\). This value is greater than zero exactly when **failedReviewDateTime** is set. Is `null` when the [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) doesn't participate in the review lifecycle. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |
| nistClassifications | [nistClassification](https://learn.microsoft.com/en-us/graph/api/resources/nistclassification?view=graph-rest-beta) collection | The NIST Cybersecurity Framework \(CSF\) 2.0 categories that the [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) maps to. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). Read-only. |
| postponeUntilDateTime | DateTimeOffset | The future date and time when the **status** of a postponed [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) will be `active` again. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |
| priority | recommendationPriority | Indicates the time sensitivity for a [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) to be completed. Microsoft auto assigns this value. The possible values are: `low`, `medium`, `high`, `critical`, `unknownFutureValue`. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). Read-only.  <br>  <br>Supports `$filter`\(`eq`\). |
| recommendationType | recommendationType | Friendly shortname to identify the [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta). The possible values are: `adfsAppsMigration`, `enableDesktopSSO`, `enablePHS`, `enableProvisioning`, `switchFromPerUserMFA`, `tenantMFA`, `thirdPartyApps`, `turnOffPerUserMFA`, `useAuthenticatorApp`, `useMyApps`, `staleApps`, `staleAppCreds`, `applicationCredentialExpiry`, `servicePrincipalKeyExpiry`, `adminMFAV2`, `blockLegacyAuthentication`, `integratedApps`, `mfaRegistrationV2`, `pwagePolicyNew`, `passwordHashSync`, `oneAdmin`, `roleOverlap`, `selfServicePasswordReset`, `signinRiskPolicy`, `userRiskPolicy`, `verifyAppPublisher`, `privateLinkForAAD`, `appRoleAssignmentsGroups`, `appRoleAssignmentsUsers`, `managedIdentity`, `overprivilegedApps`, `unknownFutureValue`, `longLivedCredentials`, `aadConnectDeprecated`, `adalToMsalMigration`, `ownerlessApps`, `inactiveGuests`, `aadGraphDeprecationApplication`, `aadGraphDeprecationServicePrincipal`, `mfaServerDeprecation`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `longLivedCredentials` , `aadConnectDeprecated` , `adalToMsalMigration` , `ownerlessApps` , `inactiveGuests` , `aadGraphDeprecationApplication` , `aadGraphDeprecationServicePrincipal` , `mfaServerDeprecation`. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta).  <br>  <br>Currently, only a limited number are available. For more information, see [Types of recommendations](https://learn.microsoft.com/en-us/graph/api/resources/recommendations-api-overview?view=graph-rest-beta#types-of-recommendations). Supports `$filter`\(`eq`\). |
| releaseType | releaseType | The current release type of the recommendation. The possible values are: `preview`, `generallyAvailable`, `unknownFutureValue`. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |
| remediatedDateTime | DateTimeOffset | The date and time when the recommendations service verified that the impacted resources the user marked as completed were remediated, meaning the user-reviewed resources reached `completedBySystem`. Is superseded by **failedReviewDateTime** if a reviewed resource subsequently fails verification. Is `null` if the system hasn't verified a user-driven remediation in the current cycle. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |
| remediationImpact | String | Description of the impact on users of the remediation. Only applies to [recommendations](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) with **category** set to `identitySecureScore`. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |
| status | recommendationStatus | Indicates the status of the [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) based on user or system action. The possible values are: `active`, `completedBySystem`, `completedByUser`, `dismissed`, `postponed`, `unknownFutureValue`, `riskAccepted`, `thirdParty`, `planned`, `alternateMitigation`, `needsMoreAction`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `riskAccepted` , `thirdParty` , `planned` , `alternateMitigation` , `needsMoreAction`. By default, a recommendation's **status** is set to `active` when the recommendation is first generated. **Status** is set to `completedBySystem` when our service detects that a recommendation which was previously active no longer applies. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta).  <br>  <br>Supports `$filter`\(`eq`\). |
| statusModifiedDateTime | DateTimeOffset | The date and time when the recommendation's **status** last changed, for example from `active` to `completedByUser`, `dismissed`, `postponed`, or `needsMoreAction`. Unlike **lastModifiedDateTime**, this value isn't updated when only the recommendation's insight data changes while the **status** stays the same. Is `null` until the recommendation's **status** changes for the first time. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| impactedResources | [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) collection | The list of directory objects associated with the [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta). Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |
| tags | [recommendationTag](https://learn.microsoft.com/en-us/graph/api/resources/recommendationtag?view=graph-rest-beta) collection | The user-defined free-form labels applied to the [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta). The collection isn't directly writable; tags are created and removed through the [addTag](https://learn.microsoft.com/en-us/graph/api/recommendation-addtag?view=graph-rest-beta) and [removeTag](https://learn.microsoft.com/en-us/graph/api/recommendation-removetag?view=graph-rest-beta) actions. Inherited from [recommendationBase](https://learn.microsoft.com/en-us/graph/api/resources/recommendationbase?view=graph-rest-beta). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.recommendation",
  "id": "String (identifier)",
  "actionSteps": [
    {
      "@odata.type": "microsoft.graph.actionStep"
    }
  ],
  "benefits": "String",
  "category": "String",
  "categoryGroup": "String",
  "completedBySystemDateTime": "String (timestamp)",
  "completedByUserDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "currentScore": "Double",
  "displayName": "String",
  "failedReviewDateTime": "String (timestamp)",
  "featureAreas": [
    "String"
  ],
  "impactType": "String",
  "impactStartDateTime": "String (timestamp)",
  "insights": "String",
  "lastCheckedDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": "String",
  "maxScore": "Double",
  "needsMoreActionResourceCount": "Int32",
  "nistClassifications": [
    {
      "@odata.type": "microsoft.graph.nistClassification"
    }
  ],
  "postponeUntilDateTime": "String (timestamp)",
  "priority": "String",
  "remediatedDateTime": "String (timestamp)",
  "status": "String",
  "statusModifiedDateTime": "String (timestamp)",
  "remediationImpact": "String",
  "recommendationType": "String"
}
```
