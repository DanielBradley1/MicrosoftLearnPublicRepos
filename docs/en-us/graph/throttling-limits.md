<!-- Source: https://learn.microsoft.com/en-us/graph/throttling-limits -->
<!-- Sitemap-Last-Modified: 2026-02-06 -->

# Microsoft Graph service-specific throttling limits

Microsoft Graph concurrently imposes two categories of throttling limits for all API calls:

- Global limits that apply to all services
- Service-specific limits that apply to individual services

Any request can be evaluated against multiple limits, depending on the scope of the limit \(per app across all tenants, per tenant for all apps, per app per tenant, and so on\), the request type \(GET, POST, PATCH, and so on\), and other factors. The first limit to be reached triggers throttling behavior.

The following table indicates the global limits:

| Request type | Per app across all tenants |
| --- | --- |
| Any | 130,000 requests per 10 seconds |

The rest of this article provides an overview of the service-specific throttling limits for each Microsoft Graph service.

Note

The specific limits described in this article are subject to change.

In this section, the term *tenant* refers to the Microsoft 365 organization where the application is installed. For a single-tenant application, this tenant can be the same as the one where the application was created; for a multitenant application, it can be a different tenant.

## Assignment service limits

| Request type | Limit per app per tenant | Limit per tenant for all apps |
| --- | --- | --- |
| Any | 350 requests per 10 seconds | 700 requests per 10 seconds |
| Any | 10,000 requests per 3,600 seconds | 20,000 requests per 3,600 seconds |
| POST /publish | 25 requests per 10 seconds | 25 requests per 10 seconds |

The preceding limits apply to the following resources:

- [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment)
- [educationSubmission](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmission)
- [trending](https://learn.microsoft.com/en-us/graph/api/resources/insights-trending)
- [educationResource](https://learn.microsoft.com/en-us/graph/api/resources/educationresource)

## Bookings service limits

The Bookings service applies limits to each app ID and mailbox combination, specifically when a particular app accesses a particular booking mailbox. Exceeding the limit for one mailbox doesn't affect the ability of the application to access another mailbox.

| Limit | Applies to |
| --- | --- |
| Four concurrent requests | v1.0 and beta endpoints |

The preceding limits apply to the following resources:

- [business](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness)
- [appointment](https://learn.microsoft.com/en-us/graph/api/resources/bookingappointment)
- [customQuestion](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomquestion)
- [customer](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomer)
- [service](https://learn.microsoft.com/en-us/graph/api/resources/bookingservice)
- [staffMember](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember)

## Cloud communication service limits

| Resource | Limits per app |
| --- | --- |
| [Calls](https://learn.microsoft.com/en-us/graph/api/resources/call) | 50,000 requests in a 15-second period, per application per tenant |
| [Meeting information](https://learn.microsoft.com/en-us/graph/api/resources/meetinginfo) | 2,000 meetings/user each month |
| [Presence](https://learn.microsoft.com/en-us/graph/api/resources/presence) | 10,000 requests in a 30-second period, per application per tenant |
| [Virtual event](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent) | 750 `GET` requests per app across all tenants in a 30-second period, and 15 `Create`, `Update`, and `Delete` requests per app across all tenants in a 30-second period. |

### Call records limits

The limits listed in the following table apply to the following resources:

- [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord)
- [participant](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participant)
- [session](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-session)

| Limit type | Limit |
| --- | --- |
| Per application for all tenants | 15,000 requests per 20 seconds |
| Per tenant for all applications | 10,000 requests per 20 seconds |
| Per application per tenant | 1,500 requests per 20 seconds |
| Per call record | 40 requests per 20 seconds |
| List call records | 40 requests per 20 seconds |

### PSTN call records limits

The limits listed in the following table apply to the following resources:

- [directRoutingLogRow](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-directroutinglogrow)
- [pstnBlockedUsersLogRow](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-pstnblockeduserslogrow)
- [pstnCallLogRow](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-pstncalllogrow)
- [pstnOnlineMeetingDialoutReport](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-pstnonlinemeetingdialoutreport)
- [smsLogRow](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-smslogrow)

| Limit type | Limit |
| --- | --- |
| Per tenant | 1,000 requests per 60 seconds |
| Per application per tenant | 200 requests per 60 seconds |
| Per collection | 50 requests per 60 seconds |

## Excel service limits

For explanations and best practices related to Excel service throttling, see [Reduce throttling errors](https://learn.microsoft.com/en-us/graph/workbook-best-practice#reduce-throttling-errors). In addition, following are some throttling limits.

| Request type | Limit per app for all tenants | Limit per app per tenant |
| --- | --- | --- |
| Any | 5000 requests per 10 seconds | 1500 requests per 10 seconds |

The preceding limits apply to the following resources:

|  |  |
| --- | --- |
| - [workbook](https://learn.microsoft.com/en-us/graph/api/resources/workbook)<br>- [workbookApplication](https://learn.microsoft.com/en-us/graph/api/resources/workbookapplication)<br>- [workbookChart](https://learn.microsoft.com/en-us/graph/api/resources/workbookchart)<br>- [workbookChartAreaFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartareaformat)<br>- [workbookChartAxes](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartaxes)<br>- [workbookChartAxis](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartaxis)<br>- [workbookChartAxisFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartaxisformat)<br>- [workbookChartAxisTitle](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartaxistitle)<br>- [workbookChartAxisTitleFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartaxistitleformat)<br>- [workbookChartDataLabelFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartdatalabelformat)<br>- [workbookChartDataLabels](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartdatalabels)<br>- [workbookChartFill](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartfill)<br>- [workbookChartFont](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartfont)<br>- [workbookChartGridlines](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartgridlines)<br>- [workbookChartGridlinesFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartgridlinesformat)<br>- [workbookChartLegend](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartlegend)<br>- [workbookChartLegendFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartlegendformat)<br>- [workbookChartLineFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartlineformat)<br>- [workbookChartPoint](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartpoint)<br>- [workbookChartPointFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartpointformat)<br>- [workbookChartSeries](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartseries)<br>- [workbookChartSeriesFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartseriesformat)<br>- [workbookChartTitle](https://learn.microsoft.com/en-us/graph/api/resources/workbookcharttitle) | - [workbookChartTitleFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookcharttitleformat)<br>- [workbookComment](https://learn.microsoft.com/en-us/graph/api/resources/workbookcomment)<br>- [workbookCommentReply](https://learn.microsoft.com/en-us/graph/api/resources/workbookcommentreply)<br>- [workbookFilter](https://learn.microsoft.com/en-us/graph/api/resources/workbookfilter)<br>- [workbookFormatProtection](https://learn.microsoft.com/en-us/graph/api/resources/formatprotection)<br>- [workbookNamedItem](https://learn.microsoft.com/en-us/graph/api/resources/workbooknameditem)<br>- [workbookOperation](https://learn.microsoft.com/en-us/graph/api/resources/workbookoperation)<br>- [workbookPivotTable](https://learn.microsoft.com/en-us/graph/api/resources/workbookpivottable)<br>- [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange)<br>- [workbookRangeBorder](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeborder)<br>- [workbookRangeFill](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangefill)<br>- [workbookRangeFont](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangefont)<br>- [workbookRangeFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeformat)<br>- [workbookRangeSort](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangesort)<br>- [workbookRangeView](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeview)<br>- [workbookTable](https://learn.microsoft.com/en-us/graph/api/resources/workbooktable)<br>- [workbookTableColumn](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablecolumn)<br>- [workbookTableRow](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablerow)<br>- [workbookTableSort](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablesort)<br>- [workbookWorksheet](https://learn.microsoft.com/en-us/graph/api/resources/workbookworksheet)<br>- [workbookWorksheetProtection](https://learn.microsoft.com/en-us/graph/api/resources/workbookworksheetprotection) |

## Education service limits

| Request type | Limit per app for all tenants | Limit per app per tenant |
| --- | --- | --- |
| Any | 400,000 requests per 20 seconds | 35,000 requests per 10 seconds |

The preceding limits apply to the following resources:

|  |  |
| --- | --- |
| - [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass)<br>- [educationCourse](https://learn.microsoft.com/en-us/graph/api/resources/educationcourse)<br>- [educationOnPremisesInfo](https://learn.microsoft.com/en-us/graph/api/resources/educationonpremisesinfo)<br>- [educationOrganization](https://learn.microsoft.com/en-us/graph/api/resources/educationorganization)<br>- [educationRelatedContact](https://learn.microsoft.com/en-us/graph/api/resources/relatedcontact)<br>- [educationRoot](https://learn.microsoft.com/en-us/graph/api/resources/educationroot) | - [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool)<br>- [educationStudent](https://learn.microsoft.com/en-us/graph/api/resources/educationstudent)<br>- [educationTeacher](https://learn.microsoft.com/en-us/graph/api/resources/educationteacher)<br>- [educationTerm](https://learn.microsoft.com/en-us/graph/api/resources/educationterm)<br>- [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser) |

## Exchange message trace service limits

| Limit type | Limit |
| --- | --- |
| Per tenant | 100 requests per 5 minutes |

The preceding limits apply to the following resources:

|  |  |
| --- | --- |
| - [exchangeMessageTrace](https://learn.microsoft.com/en-us/graph/api/resources/exchangemessagetrace) |  |

## Files and lists service limits

For service limits for OneDrive and SharePoint, see [Avoid getting throttled or blocked in SharePoint](https://learn.microsoft.com/en-us/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online).

The preceding information applies to the following resources:

|  |  |
| --- | --- |
| - [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem)<br>- [baseItemVersion](https://learn.microsoft.com/en-us/graph/api/resources/baseitemversion)<br>- [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition)<br>- [columnLink](https://learn.microsoft.com/en-us/graph/api/resources/columnlink)<br>- [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype)<br>- [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive)<br>- [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem)<br>- [driveItemVersion](https://learn.microsoft.com/en-us/graph/api/resources/driveitemversion)<br>- [fieldValueSet](https://learn.microsoft.com/en-us/graph/api/resources/fieldvalueset)<br>- [itemActivity](https://learn.microsoft.com/en-us/graph/api/resources/itemactivity) | - [itemActivityStat](https://learn.microsoft.com/en-us/graph/api/resources/itemactivitystat)<br>- [itemAnalytics](https://learn.microsoft.com/en-us/graph/api/resources/itemanalytics)<br>- [list](https://learn.microsoft.com/en-us/graph/api/resources/list)<br>- [listItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem)<br>- [listItemVersion](https://learn.microsoft.com/en-us/graph/api/resources/listitemversion)<br>- [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission)<br>- [sharedDriveItem](https://learn.microsoft.com/en-us/graph/api/resources/shareddriveitem)<br>- [site](https://learn.microsoft.com/en-us/graph/api/resources/site)<br>- [thumbnailSet](https://learn.microsoft.com/en-us/graph/api/resources/thumbnailset) |

## Identity and access reports service limits

| Request type | Limit per app for all tenants | Limit per app per tenant |
| --- | --- | --- |
| Any | 122 requests per 10 seconds | Five requests per 10 seconds |
| GET [signInActivity](https://learn.microsoft.com/en-us/graph/api/resources/signinactivity) | 10 requests per minute | 10 requests per minute |

The preceding limits apply to the following resources:

|  |  |
| --- | --- |
| - [applicationSignInDetailedSummary](https://learn.microsoft.com/en-us/graph/api/resources/applicationsignindetailedsummary)<br>- [applicationSignInSummary](https://learn.microsoft.com/en-us/graph/api/resources/applicationsigninsummary)<br>- [auditLogRoot](https://learn.microsoft.com/en-us/graph/api/resources/auditlogroot)<br>- [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod)<br>- [azureADUserFeatureUsage](https://learn.microsoft.com/en-us/graph/api/resources/userregistrationfeaturesummary)<br>- [credentialUsageSummary](https://learn.microsoft.com/en-us/graph/api/resources/credentialusagesummary)<br>- [credentialUserRegistrationCount](https://learn.microsoft.com/en-us/graph/api/resources/credentialuserregistrationcount) | - [credentialUserRegistrationDetails](https://learn.microsoft.com/en-us/graph/api/resources/credentialuserregistrationdetails)<br>- [directoryAudit](https://learn.microsoft.com/en-us/graph/api/resources/directoryaudit)<br>- [provisioningObjectSummary](https://learn.microsoft.com/en-us/graph/api/resources/provisioningobjectsummary)<br>- [relyingPartyDetailedSummary](https://learn.microsoft.com/en-us/graph/api/resources/relyingpartydetailedsummary)<br>- [signIn](https://learn.microsoft.com/en-us/graph/api/resources/signin)<br>- [userCredentialUsageDetails](https://learn.microsoft.com/en-us/graph/api/resources/usercredentialusagedetails)<br>- [signInActivity](https://learn.microsoft.com/en-us/graph/api/resources/signinactivity)<br>- [userCredentialUsageDetails](https://learn.microsoft.com/en-us/graph/api/resources/usercredentialusagedetails) |

### Identity and access reports best practices

Microsoft Entra reporting APIs are throttled when Microsoft Entra ID receives too many calls during a given timeframe from a tenant or app. Calls might also be throttled if the service takes too long to respond. If your requests still fail with a `429 Too Many Requests` error code despite applying the [best practices to handle throttling](https://learn.microsoft.com/en-us/graph/throttling#best-practices-to-handle-throttling), try reducing the amount of data returned. Try these approaches first:

- Use filters to target your query to just the data you need. If you only need a certain type of event or a subset of users, for example, filter out other events using the `$filter` and `$select` query parameters to reduce the size of your response object and the risk of throttling.
- If you need a broad set of Microsoft Entra ID reporting data, use `$filter` on the **createdDateTime** to limit the number of sign-in events you query in a single call. Then, iterate through the next timespan until you have all the records you need. For example, if you're being throttled, you can begin with a call that requests three days of data and iterate with shorter timespans until your requests are no longer throttled.
- The `$select=signInActivity` parameter on the [List users](https://learn.microsoft.com/en-us/graph/api/user-list) operation may cause stricter throttling than standard Microsoft Graph API calls. To avoid these limits, only use this parameter when necessary. If you need sign-in activity data, use `$top=500` to get the maximum 500 users per page instead of the default 100. This reduces the total number of API calls required.

## Identity and access service limits

### Pattern

Throttling is based on a token bucket algorithm, which works by adding individual costs of requests. The sum of request costs is then compared against predetermined limits. Only the requests exceeding the limits are throttled. If any of the limits are exceeded, the response is `429 Too Many Requests`. It's possible to receive `429 Too Many Requests` responses even when the following limits aren't reached, in situations when the services are under an important load or based on data volume for a specific tenant. The following table lists existing limits.

| Limit type | Resource unit quota | Write quota |
| --- | --- | --- |
| application+tenant pair | S: 3,500 ResourceUnits per 10 seconds  <br>M: 5,000 ResourceUnits per 10 seconds  <br>L: 8,000 ResourceUnits per 10 seconds | 3,000 requests per 2 minutes and 30 seconds |
| application | 150,000 ResourceUnits per 20 seconds | 35,000 requests per 5 minutes |
| tenant | Not Applicable | 18,000 requests per 5 minutes |

Note

The application + tenant pair limit varies based on the number of users in the tenant requests are run against. The tenant sizes are defined as follows: S - under 50 users, M - between 50 and 500 users, and L - above 500 users.

---

The preceding limits apply to the following resources:

|  |  |
| --- | --- |
| - [application](https://learn.microsoft.com/en-us/graph/api/resources/application)<br>- [contract](https://learn.microsoft.com/en-us/graph/api/resources/contract)<br>- [device](https://learn.microsoft.com/en-us/graph/api/resources/device)<br>- [directoryObjectPartnerReference](https://learn.microsoft.com/en-us/graph/api/resources/directoryobjectpartnerreference)<br>- [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject)<br>- [directoryRoleTemplate](https://learn.microsoft.com/en-us/graph/api/resources/directoryroletemplate)<br>- [directoryRole](https://learn.microsoft.com/en-us/graph/api/resources/directoryrole)<br>- [domainDnsCnameRecord](https://learn.microsoft.com/en-us/graph/api/resources/domaindnscnamerecord)<br>- [domainDnsMxRecord](https://learn.microsoft.com/en-us/graph/api/resources/domaindnsmxrecord)<br>- [domainDnsRecord](https://learn.microsoft.com/en-us/graph/api/resources/domaindnsrecord)<br>- [domainDnsSrvRecord](https://learn.microsoft.com/en-us/graph/api/resources/domaindnssrvrecord)<br>- [domainDnsTxtRecord](https://learn.microsoft.com/en-us/graph/api/resources/domaindnstxtrecord)<br>- [domainDnsUnavailableRecord](https://learn.microsoft.com/en-us/graph/api/resources/domaindnsunavailablerecord)<br>- [domain](https://learn.microsoft.com/en-us/graph/api/resources/domain)<br>- [endpoint](https://learn.microsoft.com/en-us/graph/api/resources/endpoint)<br>- [extensionProperty](https://learn.microsoft.com/en-us/graph/api/resources/extensionproperty) | - [groupSettingTemplate](https://learn.microsoft.com/en-us/graph/api/resources/groupsettingtemplate)<br>- [groupSetting](https://learn.microsoft.com/en-us/graph/api/resources/groupsetting)<br>- [group](https://learn.microsoft.com/en-us/graph/api/resources/group)<br>- [homeRealmDiscoveryPolicy](https://learn.microsoft.com/en-us/graph/api/resources/homerealmdiscoverypolicy)<br>- [licenseDetails](https://learn.microsoft.com/en-us/graph/api/resources/licensedetails)<br>- [oauth2PermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant)<br>- [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization)<br>- [orgContact](https://learn.microsoft.com/en-us/graph/api/resources/orgcontact)<br>- [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase)<br>- [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal)<br>- [stsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/stspolicy)<br>- [subscribedSku](https://learn.microsoft.com/en-us/graph/api/resources/subscribedsku)<br>- [tokenIssuancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/tokenissuancepolicy)<br>- [tokenLifetimePolicy](https://learn.microsoft.com/en-us/graph/api/resources/tokenlifetimepolicy)<br>- [user](https://learn.microsoft.com/en-us/graph/api/resources/user) |

---

The following table lists base request costs. Any requests not listed have a base cost of 1.

| Operation | Request Path | Base Resource Unit Cost | Write Cost |
| --- | --- | --- | --- |
| GET | `applications` | 2 | 0 |
| GET | `applications/{id}/extensionProperties` | 2 | 0 |
| GET | `contracts` | 3 | 0 |
| POST | `directoryObjects/getByIds` | 5 | 0 |
| GET | `domains/{id}/domainNameReferences` | 4 | 0 |
| POST | `getObjectsById` | 5 | 0 |
| GET | `groups/{id}/members` | 3 | 0 |
| GET | `groups/{id}/transitiveMembers` | 5 | 0 |
| POST | `isMemberOf` | 4 | 0 |
| POST | `me/checkMemberGroups` | 4 | 0 |
| POST | `me/checkMemberObjects` | 4 | 0 |
| POST | `me/getMemberGroups` | 2 | 0 |
| POST | `me/getMemberObjects` | 2 | 0 |
| GET | `me/licenseDetails` | 2 | 0 |
| GET | `me/memberOf` | 2 | 0 |
| GET | `me/ownedObjects` | 2 | 0 |
| GET | `me/transitiveMemberOf` | 2 | 0 |
| GET | `oauth2PermissionGrants` | 2 | 0 |
| GET | `oauth2PermissionGrants/{id}` | 2 | 0 |
| GET | `servicePrincipals/{id}/appRoleAssignments` | 2 | 0 |
| GET | `subscribedSkus` | 3 | 0 |
| GET | `users` | 2 | 0 |
| GET | Any identity path not listed in the table | 1 | 0 |
| POST | Any identity path not listed in the table | 1 | 1 |
| PATCH | Any identity path not listed in the table | 1 | 1 |
| PUT | Any identity path not listed in the table | 1 | 1 |
| DELETE | Any identity path not listed in the table | 1 | 1 |

Important

The cost of POST, PATCH, and DELETE operations on the `applications` request path depends on the **signInAudience** type. For apps where the **signInAudience** is `AzureADMyOrg` or `AzureADMultipleOrgs`, the cost is 70,000 requests per 5 minutes; while for apps where the **signInAudience** is `AzureADandPersonalMicrosoftAccount` or `PersonalMicrosoftAccount`, the cost is 60 requests per minute.

Other factors that affect a request cost:

- Using `$select` decreases cost by 1
- Using `$expand` increases cost by 1
- Using `$top` with a value of less than 20 decreases cost by 1
- Creating a user in a Microsoft Entra ID B2C tenant increases cost by 4

Note

- A request cost can never be lower than 1. Any request cost that applies to a request path starting with `me/` also applies to equivalent requests starting with `users/{id | userPrincipalName}/`.
- Using `$select` for `directoryObjects/getByIds` and `getObjectsById` results in 2 ResourceUnits.

### Other headers

#### Request headers

- **x-ms-throttle-priority** - If the header doesn't exist or is set to any other value, it indicates a normal request. We recommend setting priority to `high` only for the requests initiated by the user. This header can have one of the following values:

  - Low - Indicates the request is low priority. Throttling this request doesn't cause user-visible failures.
  - Normal - Default if no value is provided. Indicates that the request is default priority.
  - High - Indicates that the request is high priority. Throttling this request causes user-visible failures.

Note

Should requests be throttled, low priority requests are throttled first, normal priority requests second, and high priority requests last. Using the priority request header doesn't change the limits.

#### Regular responses requests

- **x-ms-resource-unit** - Indicates the resource unit used for this request. Values are positive integers.
- **x-ms-throttle-limit-percentage** - Returned only when the application consumed more than 0.8 of its limit. The value ranges from 0.8 to 1.8 and is a percentage of the use of the limit. Callers can use this value to set up an alert and take action.

  - 0.8 indicates you're using 80% of the granted limit.
  - 1.0 indicates you're using 100 % of the granted limit. You start to see throttling.
  - 1.2 indicates 20% of the incoming requests are throttled.
  - 1.8 indicates 80% of the incoming requests are throttled.

#### Throttled responses requests

- **x-ms-throttle-scope** - for example, `Tenant_Application/ReadWrite/9a3d526c-b3c1-4479-ba74-197b5c5751ae/0785ef7c-2d7a-4542-b048-95bcab406e0b`. Indicates the scope of throttling with the following format `<Scope>/<Limit>/<ApplicationId>/<TenantId|UserId|ResourceId>`:

  - Scope: \(string, required\)

    - Tenant\_Application - All requests for a particular tenant for the current application.
    - Tenant - All requests for the current tenant, regardless of the application.
    - Application - All requests for the current application.

  - Limit: \(string, required\)

    - Read: Read requests for the scope \(GET\)
    - Write: Write requests for the scope \(POST, PATCH, PUT, DELETE...\)
    - ReadWrite: All Requests for the scope \(any\)

  - ApplicationId \(Guid, required\)
  - TenantId\|UserId\|ResourceId: \(Guid, required\)

- **x-ms-throttle-information** - Indicates the reason for throttling and can have any value \(string\). The value is provided for diagnostics and troubleshooting purposes, some examples include:

  - CPULimitExceeded - Throttling is because the limit for cpu allocation is exceeded.
  - WriteLimitExceeded - Throttling is because the write limit is exceeded.
  - ResourceUnitLimitExceeded - Throttling is because the limit for the allocated resource unit is exceeded.

## Identity and access data policy operation service limits

| Request type | Limit per tenant |
| --- | --- |
| POST on `exportPersonalData` | 1,000 requests per day for any subject and 100 per subject per day |
| Any other request | 10,000 requests per hour |

The preceding limits apply to the following resources:

- [dataPolicyOperation](https://learn.microsoft.com/en-us/graph/api/resources/datapolicyoperation)

Note

The resources listed earlier don't return a `Retry-After` header on `429 Too Many Requests` responses.

## Identity and access device operation service limits

| Request type | Limit per app per tenant | Limit per user per tenant |
| --- | --- | --- |
| POST, PATCH, DELETE | 3,000 requests per 2 minutes and 30 seconds | 25 requests per 10 seconds |

The preceding limits apply to write quota for the [device](https://learn.microsoft.com/en-us/graph/api/resources/device) resource.

## Identity protection and conditional access service limits

| Request type | Limit per tenant for all apps |
| --- | --- |
| Any | One request per second |

|  |
| --- |
| - [riskDetection](https://learn.microsoft.com/en-us/graph/api/resources/riskdetection)<br>- [riskyUser](https://learn.microsoft.com/en-us/graph/api/resources/riskyuser)<br>- [riskyUserHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/riskyuserhistoryitem)<br>- [namedLocation](https://learn.microsoft.com/en-us/graph/api/resources/namedlocation)<br>- [countryNamedLocation](https://learn.microsoft.com/en-us/graph/api/resources/countrynamedlocation)<br>- [ipNamedLocation](https://learn.microsoft.com/en-us/graph/api/resources/ipnamedlocation)<br>- [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy) |

Note

The resources listed earlier don't return a `Retry-After` header on `429 Too Many Requests` responses.

## Identity providers service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| Any | 300 requests per 1 minute | 200 requests per 1 minute |

The preceding limits apply to the following resources:

|  |  |
| --- | --- |
| - [assignmentOrder](https://learn.microsoft.com/en-us/graph/api/resources/assignmentorder)<br>- [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener)<br>- [authenticationFlowsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationflowspolicy)<br>- [b2cAuthenticationMethodsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/b2cauthenticationmethodspolicy)<br>- [b2cIdentityUserFlow](https://learn.microsoft.com/en-us/graph/api/resources/b2cidentityuserflow)<br>- [b2xIdentityUserFlow](https://learn.microsoft.com/en-us/graph/api/resources/b2xidentityuserflow)<br>- [builtInIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/builtinidentityprovider)<br>- [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension)<br>- [identityApiConnector](https://learn.microsoft.com/en-us/graph/api/resources/identityapiconnector)<br>- [identityBuiltInUserFlowAttribute](https://learn.microsoft.com/en-us/graph/api/resources/identitybuiltinuserflowattribute)<br>- [identityCustomUserFlowAttribute](https://learn.microsoft.com/en-us/graph/api/resources/identitycustomuserflowattribute)<br>- [identityProvider](https://learn.microsoft.com/en-us/graph/api/resources/identityprovider)<br>- [identityUserFlow](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflow) | - [identityUserFlowAttribute](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattribute)<br>- [identityUserFlowAttributeAssignment](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattributeassignment)<br>- [openIdConnectIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/openidconnectidentityprovider)<br>- [openIdConnectProvider](https://learn.microsoft.com/en-us/graph/api/resources/openidconnectprovider)<br>- [socialIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/socialidentityprovider)<br>- [trustFrameworkKeySet](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkeyset)<br>- [trustFrameworkPolicy](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkpolicy)<br>- [userFlowLanguageConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userflowlanguageconfiguration)<br>- [userFlowLanguagePage](https://learn.microsoft.com/en-us/graph/api/resources/userflowlanguagepage) |

## Industry data ETL service limits

The industry data service limits on-demand [runs](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarun) to a maximum of five successful starts every 12 hours.

## Information protection service limits

The following limits apply to any request on `/informationProtection`.

For email, the resource is a unique network message ID/recipient pair. For example, submitting an email with the same message ID sent to the same person multiple times in a 15-minute period triggers the limit per resource limits listed in the following table. However, you can submit up to 150 unique emails every 15 minutes \(tenant limit\).

| Operation | Limit per tenant | Limit per resource \(email, URL, file\) |
| --- | --- | --- |
| POST | 150 requests per 15 minutes and 10,000 requests per 24 hours | One request per 15 minutes and 3 requests per 24 hours |

|  |
| --- |
| - [threatAssessmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/threatassessmentrequest)<br>- [threatAssessmentResult](https://learn.microsoft.com/en-us/graph/api/resources/threatassessmentresult)<br>- [mailAssessmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/mailassessmentrequest)<br>- [emailFileAssessmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/emailfileassessmentrequest)<br>- [fileAssessmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/fileassessmentrequest)<br>- [urlAssessmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/urlassessmentrequest) |

## Insights service limits

The following limits apply to any request on `me/insights` or `users/{id}/insights`.

| Limit | Applies to |
| --- | --- |
| 10,000 API requests in a 10-minute period | v1.0 and beta endpoints |
| Four concurrent requests | v1.0 and beta endpoints |

The preceding limits apply to the following resources:

- [people](https://learn.microsoft.com/en-us/graph/api/resources/insightssettings)
- [sharedInsight](https://learn.microsoft.com/en-us/graph/api/resources/insights-shared)
- [trending](https://learn.microsoft.com/en-us/graph/api/resources/insights-trending)
- [usedInsight](https://learn.microsoft.com/en-us/graph/api/resources/insights-used)

## Intune service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |
| --- |
| - [microsoftTunnelConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelconfiguration)<br>- [microsoftTunnelHealthThreshold](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelhealththreshold)<br>- [microsoftTunnelServer](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserver)<br>- [microsoftTunnelServerLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserverlogcollectionresponse)<br>- [microsoftTunnelSite](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelsite) |

#### Intune android for work service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |  |
| --- | --- |
| - [androidDeviceOwnerEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androiddeviceownerenrollmentprofile)<br>- [androidForWorkAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkappconfigurationschema)<br>- [androidForWorkEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkenrollmentprofile)<br>- [androidForWorkSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworksettings)<br>- [androidManagedStoreAccountEnterpriseSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreaccountenterprisesettings)<br>- [androidManagedStoreAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreappconfigurationschema) |  |

#### Intune applications service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |  |
| --- | --- |
| - [androidForWorkApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidforworkapp)<br>- [androidForWorkMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidforworkmobileappconfiguration)<br>- [androidLobApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidlobapp)<br>- [androidManagedStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstoreapp)<br>- [androidManagedStoreAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstoreappconfiguration)<br>- [androidManagedStoreWebApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstorewebapp)<br>- [androidStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidstoreapp)<br>- [enterpriseCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-enterprisecodesigningcertificate)<br>- [iosLobApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-ioslobapp)<br>- [iosLobAppProvisioningConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-ioslobappprovisioningconfiguration)<br>- [iosLobAppProvisioningConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-ioslobappprovisioningconfigurationassignment)<br>- [iosMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosmobileappconfiguration)<br>- [iosStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosstoreapp)<br>- [iosVppApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppapp)<br>- [iosVppAppAssignedDeviceLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneddevicelicense)<br>- [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense)<br>- [iosVppAppAssignedUserLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneduserlicense)<br>- [macOSLobApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macoslobapp)<br>- [macOSMdatpApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosmdatpapp)<br>- [macOSMicrosoftEdgeApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosmicrosoftedgeapp)<br>- [macOSOfficeSuiteApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosofficesuiteapp)<br>- [macOsVppApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppapp)<br>- [macOsVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppappassignedlicense)<br>- [managedAndroidLobApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-managedandroidlobapp)<br>- [managedAndroidStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-managedandroidstoreapp)<br>- [managedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-managedapp)<br>- [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration)<br>- [managedDeviceMobileAppConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationassignment)<br>- [managedDeviceMobileAppConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicestatus)<br>- [managedDeviceMobileAppConfigurationDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicesummary)<br>- [managedDeviceMobileAppConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationuserstatus)<br>- [managedDeviceMobileAppConfigurationUserSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationusersummary)<br>- [managedIOSLobApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-managedioslobapp) | - [managedIOSStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-managediosstoreapp)<br>- [managedMobileLobApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-managedmobilelobapp)<br>- [microsoftStoreForBusinessApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinessapp)<br>- [microsoftStoreForBusinessContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinesscontainedapp)<br>- [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp)<br>- [mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignment)<br>- [mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory)<br>- [mobileAppContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontent)<br>- [mobileAppContentFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentfile)<br>- [mobileAppDependency](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappdependency)<br>- [mobileAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappinstallstatus)<br>- [mobileAppInstallSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappinstallsummary)<br>- [mobileAppProvisioningConfigGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappprovisioningconfiggroupassignment)<br>- [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship)<br>- [mobileAppSupersedence](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappsupersedence)<br>- [mobileContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilecontainedapp)<br>- [mobileLobApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilelobapp)<br>- [officeSuiteApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-officesuiteapp)<br>- [symantecCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-symanteccodesigningcertificate)<br>- [userAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-userappinstallstatus)<br>- [webApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-webapp)<br>- [win32LobApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapp)<br>- [windowsAppX](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsappx)<br>- [windowsMicrosoftEdgeApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsmicrosoftedgeapp)<br>- [windowsMobileMSI](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsmobilemsi)<br>- [windowsPhone81AppX](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphone81appx)<br>- [windowsPhone81AppXBundle](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphone81appxbundle)<br>- [windowsPhone81StoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphone81storeapp)<br>- [windowsPhoneXAP](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphonexap)<br>- [windowsStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsstoreapp)<br>- [windowsUniversalAppX](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsuniversalappx)<br>- [windowsUniversalAppXContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsuniversalappxcontainedapp) |

#### Intune auditing service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |
| --- |
| - [auditEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-auditing-auditevent) |

#### Intune books service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |
| --- |
| - [deviceInstallState](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-deviceinstallstate)<br>- [eBookInstallSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-ebookinstallsummary)<br>- [iosVppEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-iosvppebook)<br>- [iosVppEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-iosvppebookassignment)<br>- [managedEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook)<br>- [managedEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookassignment)<br>- [managedEBookCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookcategory)<br>- [userInstallStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-userinstallstatesummary) |

#### Intune bundles service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |  |
| --- | --- |
| - assignmentFilterEvaluationStatusDetails<br>- [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter)<br>- [deviceCompliancePolicyPolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-devicecompliancepolicypolicysetitem)<br>- [deviceConfigurationPolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceconfigurationpolicysetitem)<br>- [deviceManagementConfigurationPolicyPolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-devicemanagementconfigurationpolicypolicysetitem)<br>- [deviceManagementScriptPolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-devicemanagementscriptpolicysetitem)<br>- [enrollmentRestrictionsConfigurationPolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-enrollmentrestrictionsconfigurationpolicysetitem)<br>- [iosLobAppProvisioningConfigurationPolicySetItem,](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-ioslobappprovisioningconfigurationpolicysetitem)<br>- [managedAppProtectionPolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-managedappprotectionpolicysetitem) | - [managedDeviceMobileAppConfigurationPolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-manageddevicemobileappconfigurationpolicysetitem)<br>- [mdmWindowsInformationProtectionPolicyPolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-mdmwindowsinformationprotectionpolicypolicysetitem)<br>- [mobileAppPolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-mobileapppolicysetitem)<br>- [policySet](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policyset)<br>- [policySetAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetassignment)<br>- [policySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetitem)<br>- [targetedManagedAppConfigurationPolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-targetedmanagedappconfigurationpolicysetitem)<br>- [windows10EnrollmentCompletionPageConfigurationPolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-windows10enrollmentcompletionpageconfigurationpolicysetitem)<br>- [windowsAutopilotDeploymentProfilePolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-windowsautopilotdeploymentprofilepolicysetitem) |

#### Intune chromebook sync service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |
| --- |
| - [chromeOSOnboardingSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-chromebooksync-chromeosonboardingsettings) |

#### Intune company terms service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |
| --- |
| - [termsAndConditions](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditions)<br>- [termsAndConditionsAcceptanceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsacceptancestatus)<br>- [termsAndConditionsAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsassignment)<br>- [termsAndConditionsGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsgroupassignment) |

#### Intune device config v2 service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |  |
| --- | --- |
| - [deviceManagementConfigurationCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationcategory)<br>- [deviceManagementConfigurationChoiceSettingCollectionDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationchoicesettingcollectiondefinition)<br>- [deviceManagementConfigurationChoiceSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationchoicesettingcollectiondefinition)<br>- [deviceManagementConfigurationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicy)<br>- [deviceManagementConfigurationPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicyassignment)<br>- [deviceManagementConfigurationPolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicytemplate)<br>- [deviceManagementConfigurationSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsetting) | - [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition)<br>- [deviceManagementConfigurationSettingGroupCollectionDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupcollectiondefinition)<br>- [deviceManagementConfigurationSettingGroupDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupdefinition)<br>- [deviceManagementConfigurationSettingTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingtemplate)<br>- [deviceManagementConfigurationSimpleSettingCollectionDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsimplesettingcollectiondefinition)<br>- [deviceManagementConfigurationSimpleSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsimplesettingdefinition)<br>- [deviceManagementReusablePolicySetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementreusablepolicysetting) |

#### Intune device configuration service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |  |
| --- | --- |
| - [advancedThreatProtectionOnboardingDeviceSettingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-advancedthreatprotectiononboardingdevicesettingstate)<br>- [advancedThreatProtectionOnboardingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-advancedthreatprotectiononboardingstatesummary)<br>- [androidCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidcertificateprofilebase)<br>- [androidCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidcompliancepolicy)<br>- [androidCustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidcustomconfiguration)<br>- androidDeviceComplianceLocalActionBase<br>- androidDeviceComplianceLocalActionLockDevice<br>- androidDeviceComplianceLocalActionLockDeviceWithPasscode<br>- [androidDeviceOwnerCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownercertificateprofilebase)<br>- [androidDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownercompliancepolicy)<br>- [androidDeviceOwnerDerivedCredentialAuthenticationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownerderivedcredentialauthenticationconfiguration)<br>- [androidDeviceOwnerEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownerenterprisewificonfiguration)<br>- [androidDeviceOwnerGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownergeneraldeviceconfiguration)<br>- [androidDeviceOwnerImportedPFXCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownerimportedpfxcertificateprofile)<br>- [androidDeviceOwnerPkcsCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownerpkcscertificateprofile)<br>- [androidDeviceOwnerScepCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownerscepcertificateprofile)<br>- [androidDeviceOwnerTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownertrustedrootcertificate)<br>- [androidDeviceOwnerVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownervpnconfiguration)<br>- [androidDeviceOwnerWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownerwificonfiguration)<br>- [androidEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androideasemailprofileconfiguration)<br>- [androidEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidenterprisewificonfiguration)<br>- [androidForWorkCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkcertificateprofilebase)<br>- [androidForWorkCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkcompliancepolicy)<br>- [androidForWorkCustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkcustomconfiguration)<br>- [androidForWorkEasEmailProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkeasemailprofilebase)<br>- [androidForWorkEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkenterprisewificonfiguration)<br>- [androidForWorkGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkgeneraldeviceconfiguration)<br>- [androidForWorkGmailEasConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkgmaileasconfiguration)<br>- [androidForWorkImportedPFXCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkimportedpfxcertificateprofile)<br>- [androidForWorkNineWorkEasConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworknineworkeasconfiguration)<br>- [androidForWorkPkcsCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkpkcscertificateprofile)<br>- [androidForWorkScepCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkscepcertificateprofile)<br>- [androidForWorkTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworktrustedrootcertificate)<br>- [androidForWorkVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkvpnconfiguration)<br>- [androidForWorkWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkwificonfiguration)<br>- [androidGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidgeneraldeviceconfiguration)<br>- [androidImportedPFXCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidimportedpfxcertificateprofile)<br>- [androidOmaCpConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidomacpconfiguration)<br>- [androidPkcsCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidpkcscertificateprofile)<br>- [androidScepCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidscepcertificateprofile)<br>- [androidTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidtrustedrootcertificate)<br>- [androidVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidvpnconfiguration)<br>- [androidWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidwificonfiguration)<br>- [androidWorkProfileCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilecertificateprofilebase)<br>- [androidWorkProfileCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilecompliancepolicy)<br>- [androidWorkProfileCustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilecustomconfiguration)<br>- [androidWorkProfileEasEmailProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofileeasemailprofilebase)<br>- [androidWorkProfileEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofileenterprisewificonfiguration)<br>- [androidWorkProfileGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilegeneraldeviceconfiguration)<br>- [androidWorkProfileGmailEasConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilegmaileasconfiguration)<br>- [androidWorkProfileNineWorkEasConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilenineworkeasconfiguration)<br>- [androidWorkProfilePkcsCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilepkcscertificateprofile)<br>- [androidWorkProfileScepCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilescepcertificateprofile)<br>- [androidWorkProfileTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofiletrustedrootcertificate)<br>- [androidWorkProfileVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilevpnconfiguration)<br>- [androidWorkProfileWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilewificonfiguration)<br>- [aospDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-aospdeviceownercompliancepolicy)<br>- [aospDeviceOwnerDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-aospdeviceownerdeviceconfiguration)<br>- [appleDeviceFeaturesConfigurationBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-appledevicefeaturesconfigurationbase)<br>- [appleExpeditedCheckinConfigurationBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-appleexpeditedcheckinconfigurationbase)<br>- [appleVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applevpnconfiguration)<br>- [cartToClassAssociation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-carttoclassassociation)<br>- [defaultDeviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-defaultdevicecompliancepolicy)<br>- [deviceComplianceActionItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceactionitem)<br>- [deviceComplianceDeviceOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancedeviceoverview)<br>- [deviceComplianceDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancedevicestatus)<br>- [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy)<br>- [deviceCompliancePolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicyassignment)<br>- [deviceCompliancePolicyDeviceStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicydevicestatesummary)<br>- [deviceCompliancePolicyGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicysettingstatesummary)<br>- [deviceCompliancePolicySettingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicysettingstatesummary)<br>- deviceCompliancePolicyState<br>- [deviceComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescheduledactionforrule)<br>- [deviceComplianceSettingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancesettingstate)<br>- [deviceComplianceUserOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuseroverview)<br>- [deviceComplianceUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuserstatus)<br>- [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration)<br>- [deviceConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationassignment)<br>- [deviceConfigurationConflictSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationconflictsummary)<br>- [deviceConfigurationDeviceOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdeviceoverview)<br>- [deviceConfigurationDeviceStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdevicestatesummary)<br>- [deviceConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdevicestatus)<br>- [deviceConfigurationGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationgroupassignment)<br>- deviceConfigurationState<br>- [deviceConfigurationUserOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuseroverview)<br>- [deviceConfigurationUserStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuserstatesummary)<br>- [deviceConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuserstatus)<br>- [deviceManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicemanagement)<br>- deviceSetupConfiguration<br>- [easEmailProfileConfigurationBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-easemailprofileconfigurationbase)<br>- [editionUpgradeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-editionupgradeconfiguration)<br>- [iosCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscertificateprofile)<br>- [iosCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscertificateprofilebase)<br>- [iosCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscompliancepolicy)<br>- [iosCustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscustomconfiguration) | - [iosDerivedCredentialAuthenticationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosderivedcredentialauthenticationconfiguration)<br>- [iosDeviceFeaturesConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosdevicefeaturesconfiguration)<br>- [iosEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioseasemailprofileconfiguration)<br>- [iosEducationDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioseducationdeviceconfiguration)<br>- [iosEduDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosedudeviceconfiguration)<br>- [iosEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosenterprisewificonfiguration)<br>- [iosExpeditedCheckinConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosexpeditedcheckinconfiguration)<br>- [iosGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosgeneraldeviceconfiguration)<br>- [iosikEv2VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosikev2vpnconfiguration)<br>- [iosImportedPFXCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosimportedpfxcertificateprofile)<br>- [iosPkcsCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iospkcscertificateprofile)<br>- [iosScepCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosscepcertificateprofile)<br>- [iosTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iostrustedrootcertificate)<br>- [iosUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdateconfiguration)<br>- [iosUpdateDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdatedevicestatus)<br>- [iosVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosvpnconfiguration)<br>- [iosWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioswificonfiguration)<br>- [macOSCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoscertificateprofilebase)<br>- [macOSCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoscompliancepolicy)<br>- [macOSCustomAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoscustomappconfiguration)<br>- [macOSCustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoscustomconfiguration)<br>- [macOSDeviceFeaturesConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosdevicefeaturesconfiguration)<br>- [macOSEndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosendpointprotectionconfiguration)<br>- [macOSEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosenterprisewificonfiguration)<br>- [macOSExtensionsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosextensionsconfiguration)<br>- [macOSGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosgeneraldeviceconfiguration)<br>- [macOSImportedPFXCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosimportedpfxcertificateprofile)<br>- [macOSPkcsCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macospkcscertificateprofile)<br>- [macOSScepCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosscepcertificateprofile)<br>- [macOSSoftwareUpdateAccountSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateaccountsummary)<br>- [macOSSoftwareUpdateCategorySummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatecategorysummary)<br>- [macOSSoftwareUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateconfiguration)<br>- [macOSSoftwareUpdateStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatestatesummary)<br>- [macOSTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macostrustedrootcertificate)<br>- [macOSVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosvpnconfiguration)<br>- [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration)<br>- [macOSWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswirednetworkconfiguration)<br>- [managedAllDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-managedalldevicecertificatestate)<br>- [managedDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddevicecertificatestate)<br>- [managedDeviceEncryptionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddeviceencryptionstate)<br>- managedDeviceMobileAppConfigurationState<br>- [ndesConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ndesconnector)<br>- [restrictedAppsViolation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-restrictedappsviolation)<br>- [settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingstatedevicesummary)<br>- [sharedPCConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-sharedpcconfiguration)<br>- [softwareUpdateStatusSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-softwareupdatestatussummary)<br>- [unsupportedDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-unsupporteddeviceconfiguration)<br>- [vpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnconfiguration)<br>- [windows10CertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10certificateprofilebase)<br>- [windows10CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10compliancepolicy)<br>- [windows10CustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10customconfiguration)<br>- [windows10DeviceFirmwareConfigurationInterface](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10devicefirmwareconfigurationinterface)<br>- [windows10EasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10easemailprofileconfiguration)<br>- [windows10EndpointProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10endpointprotectionconfiguration)<br>- [windows10EnterpriseModernAppManagementConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10enterprisemodernappmanagementconfiguration)<br>- [windows10GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10generalconfiguration)<br>- [windows10ImportedPFXCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10importedpfxcertificateprofile)<br>- [windows10MobileCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10mobilecompliancepolicy)<br>- [windows10NetworkBoundaryConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10networkboundaryconfiguration)<br>- [windows10PFXImportCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10pfximportcertificateprofile)<br>- [windows10PkcsCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10pkcscertificateprofile)<br>- [windows10SecureAssessmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10secureassessmentconfiguration)<br>- [windows10TeamGeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10teamgeneralconfiguration)<br>- [windows10VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10vpnconfiguration)<br>- [windows81CertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81certificateprofilebase)<br>- [windows81CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81compliancepolicy)<br>- [windows81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81generalconfiguration)<br>- [windows81SCEPCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81scepcertificateprofile)<br>- [windows81TrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81trustedrootcertificate)<br>- [windows81VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81vpnconfiguration)<br>- [windows81WifiImportConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81wifiimportconfiguration)<br>- windowsAssignedAccessProfile<br>- [windowsCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowscertificateprofilebase)<br>- [windowsDefenderAdvancedThreatProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsdefenderadvancedthreatprotectionconfiguration)<br>- [windowsDeliveryOptimizationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsdeliveryoptimizationconfiguration)<br>- [windowsDomainJoinConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsdomainjoinconfiguration)<br>- [windowsHealthMonitoringConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowshealthmonitoringconfiguration)<br>- [windowsIdentityProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsidentityprotectionconfiguration)<br>- [windowsKioskConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskconfiguration)<br>- [windowsPhone81CertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81certificateprofilebase)<br>- [windowsPhone81CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81compliancepolicy)<br>- [windowsPhone81CustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81customconfiguration)<br>- [windowsPhone81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81generalconfiguration)<br>- [windowsPhone81ImportedPFXCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81importedpfxcertificateprofile)<br>- [windowsPhone81SCEPCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81scepcertificateprofile)<br>- [windowsPhone81TrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81trustedrootcertificate)<br>- [windowsPhone81VpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81vpnconfiguration)<br>- [windowsPhoneEASEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphoneeasemailprofileconfiguration)<br>- [windowsPrivacyDataAccessControlItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsprivacydataaccesscontrolitem)<br>- [windowsUpdateForBusinessConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsupdateforbusinessconfiguration)<br>- [windowsUpdateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsupdatestate)<br>- [windowsVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsvpnconfiguration)<br>- [windowsWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswificonfiguration)<br>- [windowsWifiEnterpriseEAPConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswifienterpriseeapconfiguration) |

#### Intune device enrollment service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |  |
| --- | --- |
| - [complianceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-compliancemanagementpartner)<br>- [deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-deviceappmanagement)<br>- [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecategory)<br>- [deviceComanagementAuthorityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicecomanagementauthorityconfiguration)<br>- [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration)<br>- [deviceEnrollmentLimitConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentlimitconfiguration)<br>- [deviceEnrollmentPlatformRestrictionsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentplatformrestrictionsconfiguration)<br>- [deviceEnrollmentWindowsHelloForBusinessConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentwindowshelloforbusinessconfiguration)<br>- [deviceManagementExchangeConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeconnector) | - [deviceManagementExchangeOnPremisesPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeonpremisespolicy)<br>- [deviceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementpartner)<br>- [enrollmentConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enrollmentconfigurationassignment)<br>- [mobileThreatDefenseConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-mobilethreatdefenseconnector)<br>- [onPremisesConditionalAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-onpremisesconditionalaccesssettings)<br>- [sideLoadingKey](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-sideloadingkey)<br>- [vppToken](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptoken)<br>- [windows10EnrollmentCompletionPageConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windows10enrollmentcompletionpageconfiguration) |

#### Intune device intent service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |  |
| --- | --- |
| - [deviceManagementAbstractComplexSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementabstractcomplexsettingdefinition)<br>- [deviceManagementAbstractComplexSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementabstractcomplexsettinginstance)<br>- [deviceManagementBooleanSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementbooleansettinginstance)<br>- [deviceManagementCollectionSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementcollectionsettingdefinition)<br>- [deviceManagementCollectionSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementcollectionsettinginstance)<br>- [deviceManagementComplexSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementcomplexsettingdefinition)<br>- [deviceManagementComplexSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementcomplexsettinginstance)<br>- [deviceManagementIntegerSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintegersettinginstance)<br>- [deviceManagementIntent](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintent)<br>- [deviceManagementIntentAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentassignment)<br>- [deviceManagementIntentDeviceSettingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicesettingstatesummary)<br>- [deviceManagementIntentDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestate)<br>- [deviceManagementIntentDeviceStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestatesummary)<br>- [deviceManagementIntentSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentsettingcategory) | - [deviceManagementIntentUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentuserstate)<br>- [deviceManagementIntentUserStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentuserstatesummary)<br>- [deviceManagementSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingcategory)<br>- [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition)<br>- [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance)<br>- [deviceManagementStringSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementstringsettinginstance)<br>- [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate)<br>- [deviceManagementTemplateSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplatesettingcategory)<br>- [securityBaselineCategoryStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinecategorystatesummary)<br>- [securityBaselineDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinedevicestate)<br>- securityBaselineSettingState<br>- securityBaselineState<br>- [securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinestatesummary)<br>- [securityBaselineTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinetemplate) |

#### Intune devices service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 400 requests per 20 seconds | 200 requests per 20 seconds |
| Any | 4000 requests per 20 seconds | 2000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |  |
| --- | --- |
| - [applePushNotificationCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applepushnotificationcertificate)<br>- [appLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applogcollectionrequest)<br>- [cloudPCConnectivityIssue](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-cloudpcconnectivityissue)<br>- [comanagementEligibleDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-comanagementeligibledevice)<br>- [dataSharingConsent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-datasharingconsent)<br>- [detectedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-detectedapp)<br>- [deviceComplianceScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescript)<br>- [deviceComplianceScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescriptdevicestate)<br>- [deviceComplianceScriptRunSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescriptrunsummary)<br>- [deviceCustomAttributeShellScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecustomattributeshellscript)<br>- [deviceHealthScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscript)<br>- [deviceHealthScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptassignment)<br>- [deviceHealthScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptdevicestate)<br>- [deviceHealthScriptRunSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptrunsummary)<br>- [deviceLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelogcollectionresponse)<br>- [deviceManagementScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementscript)<br>- [deviceManagementScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptassignment)<br>- [deviceManagementScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptdevicestate)<br>- [deviceManagementScriptGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptgroupassignment)<br>- [deviceManagementScriptRunSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptrunsummary)<br>- [deviceManagementScriptUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptuserstate)<br>- [deviceShellScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceshellscript)<br>- [malwareStateForWindowsDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-malwarestateforwindowsdevice)<br>- [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice)<br>- [managedDeviceOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddeviceoverview)<br>- [remoteActionAudit](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-remoteactionaudit)<br>- [userExperienceAnalyticsAppHealthApplicationPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthapplicationperformance)<br>- [userExperienceAnalyticsAppHealthAppPerformanceByAppVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversion)<br>- [userExperienceAnalyticsAppHealthAppPerformanceByOSVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyosversion)<br>- [userExperienceAnalyticsAppHealthDeviceModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdevicemodelperformance) | - [userExperienceAnalyticsAppHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdeviceperformance)<br>- [userExperienceAnalyticsAppHealthDevicePerformanceDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdeviceperformancedetails)<br>- [userExperienceAnalyticsAppHealthOSVersionPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthosversionperformance)<br>- [userExperienceAnalyticsBaseline](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbaseline)<br>- [userExperienceAnalyticsCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticscategory)<br>- [userExperienceAnalyticsDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdeviceperformance)<br>- [userExperienceAnalyticsDeviceScores](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicescores)<br>- [userExperienceAnalyticsDeviceStartupHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartuphistory)<br>- [userExperienceAnalyticsDeviceStartupProcess](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartupprocess)<br>- [userExperienceAnalyticsDeviceStartupProcessPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartupprocessperformance)<br>- [userExperienceAnalyticsDeviceWithoutCloudIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicewithoutcloudidentity)<br>- [userExperienceAnalyticsImpactingProcess](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsimpactingprocess)<br>- [userExperienceAnalyticsMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetric)<br>- [userExperienceAnalyticsMetricHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetrichistory)<br>- [userExperienceAnalyticsNotAutopilotReadyDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsnotautopilotreadydevice)<br>- [userExperienceAnalyticsOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsoverview)<br>- [userExperienceAnalyticsRegressionSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsregressionsummary)<br>- [userExperienceAnalyticsRemoteConnection](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsremoteconnection)<br>- [userExperienceAnalyticsResourcePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsresourceperformance)<br>- [userExperienceAnalyticsScoreHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsscorehistory)<br>- [userExperienceAnalyticsWorkFromAnywhereDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheredevice)<br>- [userExperienceAnalyticsWorkFromAnywhereMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheremetric)<br>- [windowsDeviceMalwareState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsdevicemalwarestate)<br>- [windowsMalwareInformation](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmalwareinformation)<br>- [windowsManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanageddevice)<br>- [windowsManagementApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanagementapp)<br>- [windowsManagementAppHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanagementapphealthstate)<br>- windowsManagementAppHealthSummary<br>- [windowsProtectionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsprotectionstate) |

#### Intune endpoint protection service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |
| --- |
| - [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings)<br>- [deviceManagementResourceAccessProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofileassignment)<br>- [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase)<br>- [windows10XCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xcertificateprofile)<br>- [windows10XSCEPCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xscepcertificateprofile)<br>- [windows10XTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xtrustedrootcertificate)<br>- [windows10XVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xvpnconfiguration)<br>- [windows10XWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xwificonfiguration) |

#### Intune enrollment service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |  |
| --- | --- |
| - [complianceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-compliancemanagementpartner)<br>- [deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-deviceappmanagement)<br>- [deviceCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecategory)<br>- [deviceComanagementAuthorityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicecomanagementauthorityconfiguration)<br>- [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration)<br>- [deviceEnrollmentLimitConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentlimitconfiguration)<br>- [deviceEnrollmentPlatformRestrictionsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentplatformrestrictionsconfiguration)<br>- [deviceEnrollmentWindowsHelloForBusinessConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentwindowshelloforbusinessconfiguration)<br>- [deviceManagementExchangeConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeconnector) | - [deviceManagementExchangeOnPremisesPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeonpremisespolicy)<br>- [deviceManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementpartner)<br>- [enrollmentConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enrollmentconfigurationassignment)<br>- [mobileThreatDefenseConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-mobilethreatdefenseconnector)<br>- [onPremisesConditionalAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-onpremisesconditionalaccesssettings)<br>- [sideLoadingKey](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-sideloadingkey)<br>- [vppToken](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptoken)<br>- [windows10EnrollmentCompletionPageConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windows10enrollmentcompletionpageconfiguration) |

#### Intune GPAnalytics service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |
| --- |
| - [groupPolicyMigrationReport](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicymigrationreport)<br>- [groupPolicyObjectFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicyobjectfile)<br>- [groupPolicySettingMapping](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicysettingmapping)<br>- [unsupportedGroupPolicyExtension](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-unsupportedgrouppolicyextension) |

#### Intune managed applications service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |  |
| --- | --- |
| - [androidManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-androidmanagedappprotection)<br>- [androidManagedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-androidmanagedappregistration)<br>- [defaultManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-defaultmanagedappprotection)<br>- [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmanagedappprotection)<br>- [iosManagedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmanagedappregistration)<br>- [managedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappconfiguration)<br>- [managedAppOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappoperation)<br>- [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy)<br>- [managedAppPolicyDeploymentSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicydeploymentsummary)<br>- [managedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappprotection)<br>- [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration)<br>- [managedAppStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappstatus) | - [managedAppStatusRaw](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappstatusraw)<br>- [managedMobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedmobileapp)<br>- [mdmWindowsInformationProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-mdmwindowsinformationprotectionpolicy)<br>- [targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedappconfiguration)<br>- [targetedManagedAppPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedapppolicyassignment)<br>- [targetedManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedappprotection)<br>- [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection)<br>- [windowsInformationProtectionAppLockerFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapplockerfile)<br>- [windowsInformationProtectionDeviceRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectiondeviceregistration)<br>- [windowsInformationProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionpolicy)<br>- [windowsInformationProtectionWipeAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionwipeaction) |

#### Intune notifications service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |
| --- |
| - [localizedNotificationMessage](https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-localizednotificationmessage)<br>- [notificationMessageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-notificationmessagetemplate) |

#### Intune ODJ service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |
| --- |
| - [deviceManagementDomainJoinConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-odj-devicemanagementdomainjoinconnector) |

#### Intune partner integration service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |
| --- |
| - [appVulnerabilityManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-appvulnerabilitymanageddevice)<br>- [appVulnerabilityMobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-appvulnerabilitymobileapp)<br>- [appVulnerabilityTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-appvulnerabilitytask)<br>- [configManagerCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-configmanagercollection)<br>- [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask)<br>- [securityConfigurationTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-securityconfigurationtask)<br>- [unmanagedDeviceDiscoveryTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-unmanageddevicediscoverytask)<br>- [vulnerableManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-vulnerablemanageddevice) |

#### Intune rbac service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |
| --- |
| - [deviceAndAppManagementRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-deviceandappmanagementroleassignment)<br>- [deviceAndAppManagementRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-deviceandappmanagementroledefinition)<br>- [resourceOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-resourceoperation)<br>- [roleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roleassignment)<br>- [roleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roledefinition)<br>- [roleScopeTag](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetag)<br>- [roleScopeTagAutoAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetagautoassignment) |

#### Intune remote assistance service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |
| --- |
| - [remoteAssistancePartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancepartner)<br>- [remoteAssistanceSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancesettings) |

#### Intune telephony service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |
| --- |
| - [embeddedSIMActivationCodePool](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepool)<br>- [embeddedSIMActivationCodePoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepoolassignment)<br>- [embeddedSIMDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimdevicestate) |

#### Intune TEM service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |
| --- |
| - [telecomExpenseManagementPartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-tem-telecomexpensemanagementpartner) |

#### Intune troubleshooting service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |
| --- |
| - [appleVppTokenTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-applevpptokentroubleshootingevent)<br>- [deviceManagementAutopilotEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementautopilotevent)<br>- [deviceManagementAutopilotPolicyStatusDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementautopilotpolicystatusdetail)<br>- [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent)<br>- [enrollmentTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-enrollmenttroubleshootingevent)<br>- [mobileAppIntentAndState](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-mobileappintentandstate)<br>- [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapptroubleshootingevent) |

#### Intune unlock service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |
| --- |
| - [windowsDefenderApplicationControlSupplementalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicy)<br>- [windowsDefenderApplicationControlSupplementalPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicyassignment)<br>- [windowsDefenderApplicationControlSupplementalPolicyDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentstatus)<br>- [windowsDefenderApplicationControlSupplementalPolicyDeploymentSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentsummary) |

#### Intune updates service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |
| --- |
| - [windowsFeatureUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdatecatalogitem)<br>- [windowsFeatureUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofile)<br>- [windowsFeatureUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofileassignment)<br>- [windowsQualityUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecatalogitem)<br>- [windowsQualityUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdateprofile)<br>- [windowsQualityUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdateprofileassignment)<br>- [windowsUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsupdatecatalogitem) |

#### Intune wip service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |
| --- |
| - [intuneBrandingProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofile)<br>- [intuneBrandingProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofileassignment)<br>- [windowsInformationProtectionAppLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionapplearningsummary)<br>- [windowsInformationProtectionNetworkLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionnetworklearningsummary) |

## Invitation manager service limits

The following limits apply to any request on `/invitations`.

| Operation | Limit per tenant for all apps |
| --- | --- |
| Any operation | 150 requests per 5 seconds |

## Microsoft 365 reports service limits

The following limits apply to any request on `/reports`.

| Operation | Limit per app per tenant | Limit per tenant for all apps |
| --- | --- | --- |
| Any request \(CSV\) | 14 requests per 10 minutes | 40 requests per 10 minutes |
| Any request \(JSON, beta\) | 100 requests per 10 minutes | n/a |

The preceding limits apply individually to each report API. For example, a request to the Microsoft Teams user activity report API and a request to the Outlook user activity report API within 10 minutes count as one request out of 14 for each API, not two requests out of 14 for both.

The preceding limits apply to all [usage reports](https://learn.microsoft.com/en-us/graph/api/resources/report) resources.

## Microsoft Teams service limits

Microsoft Teams applies throttling limits across four independent dimensions. A request is throttled when it exceeds **any** limit that applies to it, so always design for the lowest limit that your scenario hits.

| Dimension | What it counts | When it typically applies |
| --- | --- | --- |
| **Per app** | All requests from one app \(client ID\) summed across every tenant. | Multitenant apps that serve many customers. |
| **Per app per tenant** | Requests from one app within a single tenant. | The most commonly reached limit. |
| **Per resource** | Requests against a single team, channel, or chat. | Apps that concentrate traffic on one conversation. |
| **Per user** | Requests made on behalf of a single user. | Delegated \(user\) permission scenarios. |

Limits are expressed as requests per second \(rps\) unless stated otherwise.

> Each limit is evaluated over a short burst window. A sustained limit of approximately 83 percent of the listed value is also evaluated over a longer window, so a workload that runs continuously at the listed rate can still be throttled. Size your steady-state traffic below the listed limit and use exponential backoff.

A dash \(`-`\) means that no dedicated limit is defined for that dimension. The request is still subject to the [default limits](#default-limits) and to any other limit in the same row.

### Teams

| Request | Per app | Per app per tenant | Per resource | Per user |
| --- | --- | --- | --- | --- |
| GET /teams/`{team-id}` | 1500 rps | 30 rps | 4 rps per team | - |
| GET [/me/joinedTeams or /users/`{user-id}`/joinedTeams](https://learn.microsoft.com/en-us/graph/api/user-list-joinedteams) | 300 rps | 30 rps | - | - |
| POST [/teams](https://learn.microsoft.com/en-us/graph/api/team-post) | 100 rps | 10 rps | - | - |
| PUT /groups/`{team-id}`/[team](https://learn.microsoft.com/en-us/graph/api/team-put-teams) | 150 rps | 6 rps | - | - |
| PATCH [/teams/`{team-id}`](https://learn.microsoft.com/en-us/graph/api/team-update) | 300 rps | 30 rps | 4 rps per team | - |
| POST /teams/`{team-id}`/[clone](https://learn.microsoft.com/en-us/graph/api/team-clone) | 150 rps | 6 rps | - | - |
| POST /teams/`{team-id}`/[completeMigration](https://learn.microsoft.com/en-us/graph/api/team-completemigration) | 100 rps | 10 rps | - | - |

### Channels

| Request | Per app | Per app per tenant | Per resource | Per user |
| --- | --- | --- | --- | --- |
| GET /teams/`{team-id}`/[channels](https://learn.microsoft.com/en-us/graph/api/channel-list) | 1200 rps | 60 rps | 4 rps per team | - |
| GET /teams/`{team-id}`/channels/[`{channel-id}`](https://learn.microsoft.com/en-us/graph/api/channel-get) | 600 rps | 30 rps | 1 rps per channel | - |
| GET /teams/`{team-id}`/channels/`{channel-id}`/[members](https://learn.microsoft.com/en-us/graph/api/channel-list-members) | 1200 rps | 60 rps | 1 rps per channel | - |
| POST /teams/`{team-id}`/[channels](https://learn.microsoft.com/en-us/graph/api/channel-post) | 100 rps | 10 rps | 4 rps per team | - |
| PATCH /teams/`{team-id}`/channels/[`{channel-id}`](https://learn.microsoft.com/en-us/graph/api/channel-patch) | 300 rps | 30 rps | 1 rps per channel | - |
| DELETE /teams/`{team-id}`/channels/[`{channel-id}`](https://learn.microsoft.com/en-us/graph/api/channel-delete) | 150 rps | 15 rps | 1 rps per channel | - |
| POST /teams/`{team-id}`/channels/`{channel-id}`/[completeMigration](https://learn.microsoft.com/en-us/graph/api/channel-completemigration) | 100 rps | 10 rps | - | - |

### Channel messages

| Request | Per app | Per app per tenant | Per resource | Per user |
| --- | --- | --- | --- | --- |
| GET /teams/`{team-id}`/channels/`{channel-id}`/[messages](https://learn.microsoft.com/en-us/graph/api/channel-list-messages) | 200 rps | 20 rps | 1 rps per channel | - |
| POST /teams/`{team-id}`/channels/`{channel-id}`/[messages](https://learn.microsoft.com/en-us/graph/api/channel-post-messages) | 500 rps | 50 rps | 1 rps per channel | 1 rps |
| POST /teams/`{team-id}`/channels/`{channel-id}`/messages/`{message-id}`/[replies](https://learn.microsoft.com/en-us/graph/api/chatmessage-post-replies) | 500 rps | 50 rps | 1 rps per channel | 1 rps |

The POST limits in the preceding table are shared by regular message sends and by [message import](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/import-messages/import-external-messages-to-teams). The per-user limit doesn't apply to import.

### Chats

| Request | Per app | Per app per tenant | Per resource | Per user |
| --- | --- | --- | --- | --- |
| GET [/chats](https://learn.microsoft.com/en-us/graph/api/chat-list), /me/chats, or /users/`{user-id}`/chats | 200 rps | 20 rps | - | 1 rps |
| GET [/chats/`{chat-id}`](https://learn.microsoft.com/en-us/graph/api/chat-get) | 2000 rps | 200 rps | 1 rps per chat | 5 rps |
| POST [/chats](https://learn.microsoft.com/en-us/graph/api/chat-post) | 200 rps | 20 rps | - | - |
| PATCH [/chats/`{chat-id}`](https://learn.microsoft.com/en-us/graph/api/chat-patch) | 300 rps | 30 rps | 1 rps per chat | - |
| DELETE [/chats/`{chat-id}`](https://learn.microsoft.com/en-us/graph/api/chat-delete) | 10 rps | 1 rps | 1 rps per chat | - |
| POST /chats/`{chat-id}`/[removeAllAccessForUser](https://learn.microsoft.com/en-us/graph/api/chat-removeallaccessforuser) | 300 rps | 30 rps | 1 rps per chat | 1 rps |

### Chat messages

| Request | Per app | Per app per tenant | Per resource | Per user |
| --- | --- | --- | --- | --- |
| GET /chats/`{chat-id}`/[messages](https://learn.microsoft.com/en-us/graph/api/chat-list-messages) | 200 rps | 20 rps | 1 rps per chat | - |
| POST /chats/`{chat-id}`/[messages](https://learn.microsoft.com/en-us/graph/api/chat-post-messages) | 200 rps | 20 rps | 1 rps per chat | 1 rps |
| PATCH /chats/`{chat-id}`/[messages/`{message-id}`](https://learn.microsoft.com/en-us/graph/api/chatmessage-update) | 300 rps | 30 rps | 1 rps per chat | - |
| POST /chats/`{chat-id}`/messages/`{message-id}`/[softDelete](https://learn.microsoft.com/en-us/graph/api/chatmessage-softdelete) or [undoSoftDelete](https://learn.microsoft.com/en-us/graph/api/chatmessage-undosoftdelete) | 300 rps | 30 rps | 1 rps per chat | - |
| GET /chats/`{chat-id}`/messages/`{message-id}`/[hostedContents](https://learn.microsoft.com/en-us/graph/api/chatmessagehostedcontent-get) | 500 rps | 50 rps | 1 rps per chat | - |
| GET /chats/`{chat-id}`/messages/`{message-id}`/hostedContents/`{id}`/$value | 600 rps | 60 rps | 1 rps per chat | - |

### Members

| Request | Per app | Per app per tenant | Per resource | Per user |
| --- | --- | --- | --- | --- |
| GET /teams/`{team-id}`/[members](https://learn.microsoft.com/en-us/graph/api/team-list-members) | 1200 rps | 60 rps | 4 rps per team | - |
| POST /teams/`{team-id}`/[members](https://learn.microsoft.com/en-us/graph/api/team-post-members) | 300 rps | 30 rps | 4 requests per minute per team | - |
| POST /teams/`{team-id}`/members/[add](https://learn.microsoft.com/en-us/graph/api/conversationmember-add) | 100 rps | 10 rps | 4 requests per minute per team | - |
| POST /chats/`{chat-id}`/[members](https://learn.microsoft.com/en-us/graph/api/chat-post-members) | 300 rps | 30 rps | 4 requests per minute per chat | - |
| DELETE /chats/`{chat-id}`/[members/`{membership-id}`](https://learn.microsoft.com/en-us/graph/api/chat-delete-members) | 300 rps | 30 rps | 4 requests per minute per chat | - |

### Apps, tabs, and permission grants

| Request | Per app | Per app per tenant | Per resource | Per user |
| --- | --- | --- | --- | --- |
| GET installedApps for [team](https://learn.microsoft.com/en-us/graph/api/team-list-installedapps), [chat](https://learn.microsoft.com/en-us/graph/api/chat-list-installedapps), or [user](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-installedapps) | 1500 rps | 30 rps | 1 rps per chat or channel | - |
| GET permissionGrants for [team](https://learn.microsoft.com/en-us/graph/api/team-list-permissiongrants) or [chat](https://learn.microsoft.com/en-us/graph/api/chat-list-permissiongrants) | 1500 rps | 30 rps | 1 rps per chat or channel | - |
| POST installedApps for [team](https://learn.microsoft.com/en-us/graph/api/team-post-installedapps), [chat](https://learn.microsoft.com/en-us/graph/api/chat-post-installedapps), or [user](https://learn.microsoft.com/en-us/graph/api/userteamwork-post-installedapps) | 300 rps | 30 rps | 1 rps per chat or channel | - |
| DELETE installedApps for [team](https://learn.microsoft.com/en-us/graph/api/team-delete-installedapps), [chat](https://learn.microsoft.com/en-us/graph/api/chat-delete-installedapps), or [user](https://learn.microsoft.com/en-us/graph/api/userteamwork-delete-installedapps) | 150 rps | 15 rps | 1 rps per chat or channel | - |
| GET tabs for [channel](https://learn.microsoft.com/en-us/graph/api/channel-list-tabs) or [chat](https://learn.microsoft.com/en-us/graph/api/chat-list-tabs) | 600 rps | 30 rps | 1 rps per chat or channel | - |
| POST tabs for [channel](https://learn.microsoft.com/en-us/graph/api/channel-post-tabs) or [chat](https://learn.microsoft.com/en-us/graph/api/chat-post-tabs) | 300 rps | 30 rps | 1 rps per chat or channel | - |
| PATCH [tab](https://learn.microsoft.com/en-us/graph/api/channel-patch-tabs) | 300 rps | 30 rps | 1 rps per chat or channel | - |
| DELETE tabs for [channel](https://learn.microsoft.com/en-us/graph/api/channel-delete-tabs) or [chat](https://learn.microsoft.com/en-us/graph/api/chat-delete-tabs) | 150 rps | 15 rps | 1 rps per chat or channel | - |
| GET [/appCatalogs/teamsApps](https://learn.microsoft.com/en-us/graph/api/appcatalogs-list-teamsapps) | 1500 rps | 30 rps | - | - |
| POST [/appCatalogs/teamsApps](https://learn.microsoft.com/en-us/graph/api/teamsapp-publish) | 300 rps | 30 rps | - | - |
| DELETE [/appCatalogs/teamsApps/`{app-id}`](https://learn.microsoft.com/en-us/graph/api/teamsapp-delete) | 150 rps | 15 rps | - | - |

### Activity feed notifications

| Request | Per app | Per app per tenant | Per resource | Per user |
| --- | --- | --- | --- | --- |
| POST /teams/`{team-id}`/[sendActivityNotification](https://learn.microsoft.com/en-us/graph/api/team-sendactivitynotification) | 50 rps | 5 rps | 4 rps per team | - |
| POST /chats/`{chat-id}`/[sendActivityNotification](https://learn.microsoft.com/en-us/graph/api/chat-sendactivitynotification) | 50 rps | 5 rps | 1 rps per chat | - |
| POST /users/`{user-id}`/teamwork/[sendActivityNotification](https://learn.microsoft.com/en-us/graph/api/userteamwork-sendactivitynotification) | 50 rps | 5 rps | - | - |
| POST /teamwork/[sendActivityNotificationToRecipients](https://learn.microsoft.com/en-us/graph/api/teamwork-sendactivitynotificationtorecipients) | 20 rps | 2 rps | - | - |

### Bulk message retrieval

These APIs are designed for export and compliance scenarios and have their own higher limits.

| Request | Per app | Per app per tenant | Per resource | Per user |
| --- | --- | --- | --- | --- |
| GET /teams/`{team-id}`/channels/[getAllMessages](https://learn.microsoft.com/en-us/graph/api/channel-getallmessages) or /channels/allMessages | 1000 rps | 200 rps | - | - |
| GET /users/`{user-id}`/chats/[getAllMessages](https://learn.microsoft.com/en-us/graph/api/chats-getallmessages) or /chats/allMessages | 1000 rps | 200 rps | - | - |
| GET /teams/`{team-id}`/channels/[getAllRetainedMessages](https://learn.microsoft.com/en-us/graph/api/channel-getallretainedmessages) | 1000 rps | 200 rps | - | - |
| GET /users/`{user-id}`/chats/[getAllRetainedMessages](https://learn.microsoft.com/en-us/graph/api/chat-getallretainedmessages) | 1000 rps | 200 rps | - | - |
| GET /copilot/users/`{user-id}`/interactionHistory/[getAllEnterpriseInteractions](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api-reference/aiinteractionhistory-getallenterpriseinteractions) | 1500 rps | 30 rps | - | - |

### Shifts

| Request | Per app | Per app per tenant | Per resource | Per user |
| --- | --- | --- | --- | --- |
| GET /teams/`{team-id}`/[schedule](https://learn.microsoft.com/en-us/graph/api/schedule-get) and all APIs under this path | 600 rps | 30 rps | - | - |
| POST /teams/`{team-id}`/[schedule](https://learn.microsoft.com/en-us/graph/api/schedule-share) and all APIs under this path | 300 rps | 30 rps | - | - |
| PUT /teams/`{team-id}`/[schedule](https://learn.microsoft.com/en-us/graph/api/team-put-schedule) and all APIs under this path | 300 rps | 30 rps | - | - |

### Sections

| Request | Per app | Per app per tenant | Per resource | Per user |
| --- | --- | --- | --- | --- |
| All section management APIs under /users/`{user-id}`/teamwork/[sections](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta&preserve-view=true) | - | 5 rps | - | - |

All section operations, including sections, section items, reorder actions, and delta queries, share a single limit.

### Default limits

Any Microsoft Teams request that isn't listed in the preceding tables uses these limits.

| Request type | Per app | Per app per tenant | Per resource | Per user |
| --- | --- | --- | --- | --- |
| GET | 1500 rps | 30 rps | 1 rps per chat or channel | 1 rps |
| POST, PUT, and PATCH | 300 rps | 30 rps | 1 rps per chat or channel | 1 rps |
| DELETE | 150 rps | 15 rps | 1 rps per chat or channel | 1 rps |

### Related resources

See also [Microsoft Teams limits](https://learn.microsoft.com/en-us/graph/api/resources/teams-api-overview#microsoft-teams-limits) and [polling requirements](https://learn.microsoft.com/en-us/graph/api/resources/teams-api-overview#polling-requirements).

The preceding limits apply to the following resources:

|  |  |
| --- | --- |
| - [aadUserConversationMember](https://learn.microsoft.com/en-us/graph/api/resources/aadUserConversationMember)<br>- [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changeTrackedEntity)  <br><br>- [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel)  <br><br>- [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatMessage)  <br><br>- [chatMessageHostedContent](https://learn.microsoft.com/en-us/graph/api/resources/chatMessageHostedContent)  <br><br>- [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationMember)  <br><br>- [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offerShiftRequest)  <br><br>- [openShift](https://learn.microsoft.com/en-us/graph/api/resources/openShift)  <br><br>- [openShiftChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/openShiftChangeRequest)  <br><br>- [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule)  <br><br>- [schedulingGroup](https://learn.microsoft.com/en-us/graph/api/resources/schedulingGroup)  <br><br>- [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift)  <br><br>- [shiftPreferences](https://learn.microsoft.com/en-us/graph/api/resources/shiftPreferences) | - [swapShiftsChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/swapShiftsChangeRequest)  <br><br>- [team](https://learn.microsoft.com/en-us/graph/api/resources/team)  <br><br>- [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsApp)  <br><br>- [teamsAppDefinition](https://learn.microsoft.com/en-us/graph/api/resources/teamsAppDefinition)  <br><br>- [teamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/teamsAppInstallation)  <br><br>- [teamsAsyncOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamsAsyncOperation)  <br><br>- [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamsTab)  <br><br>- [teamsTemplate](https://learn.microsoft.com/en-us/graph/api/resources/teamsTemplate)  <br><br>- [teamwork](https://learn.microsoft.com/en-us/graph/api/resources/teamwork)  <br><br>- [teamworkSection](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta&preserve-view=true)  <br><br>- [teamworkSectionItem](https://learn.microsoft.com/en-us/graph/api/resources/teamworksectionitem?view=graph-rest-beta&preserve-view=true)  <br><br>- [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeOff)  <br><br>- [timeOffReason](https://learn.microsoft.com/en-us/graph/api/resources/timeOffReason)  <br><br>- [timeOffRequest](https://learn.microsoft.com/en-us/graph/api/resources/timeOffRequest)  <br><br>- [userSettings](https://learn.microsoft.com/en-us/graph/api/resources/userSettings)  <br><br>- [workforceIntegration](https://learn.microsoft.com/en-us/graph/api/resources/workforceIntegration) |

## Multitenant management service limits

| Request type | Limit per tenant for all apps | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 200 requests per 20 seconds | 100 requests per 20 seconds |
| Any | 2000 requests per 20 seconds | 1000 requests per 20 seconds |

The preceding limits apply to the following resources:

|  |  |
| --- | --- |
| - [aggregatedPolicyCompliance](https://learn.microsoft.com/en-us/graph/api/resources/managedTenants-aggregatedpolicycompliance)<br>- [cloudPcConnection](https://learn.microsoft.com/en-us/graph/api/resources/managedTenants-cloudpcconnection)<br>- [cloudPcDevice](https://learn.microsoft.com/en-us/graph/api/resources/managedTenants-cloudpcdevice)<br>- [cloudPcOverview](https://learn.microsoft.com/en-us/graph/api/resources/managedTenants-cloudpcoverview)<br>- [conditionalAccessPolicyCoverage](https://learn.microsoft.com/en-us/graph/api/resources/managedTenants-conditionalaccesspolicycoverage)<br>- [credentialUserRegistrationsSummary](https://learn.microsoft.com/en-us/graph/api/resources/managedTenants-credentialuserregistrationssummary)<br>- [deviceCompliancePolicySettingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/managedTenants-devicecompliancepolicysettingstatesummary)<br>- [managedDeviceCompliance](https://learn.microsoft.com/en-us/graph/api/resources/managedTenants-manageddevicecompliance)<br>- [managedDeviceComplianceTrend](https://learn.microsoft.com/en-us/graph/api/resources/managedTenants-manageddevicecompliancetrend)<br>- [managedTenant](https://learn.microsoft.com/en-us/graph/api/resources/managedTenants-managedtenant)<br>- [managementAction](https://learn.microsoft.com/en-us/graph/api/resources/managedTenants-managementaction)<br>- [managementActionTenantDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/managedTenants-managementactiontenantdeploymentstatus) | - [managementIntent](https://learn.microsoft.com/en-us/graph/api/resources/managedTenants-managementintent)<br>- [managementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/managedTenants-managementtemplate)<br>- [riskyUser](https://learn.microsoft.com/en-us/graph/api/resources/riskyuser)<br>- [tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedTenants-tenant)<br>- [tenantCustomizedInformation](https://learn.microsoft.com/en-us/graph/api/resources/managedTenants-tenantcustomizedinformation)<br>- [tenantDetailedInformation](https://learn.microsoft.com/en-us/graph/api/resources/managedTenants-tenantdetailedinformation)<br>- [tenantGroup](https://learn.microsoft.com/en-us/graph/api/resources/managedTenants-tenantgroup)<br>- [tenantRelationship](https://learn.microsoft.com/en-us/graph/api/resources/tenantrelationship)<br>- [tenantTag](https://learn.microsoft.com/en-us/graph/api/resources/managedTenants-tenanttag)<br>- [windowsDeviceMalwareState](https://learn.microsoft.com/en-us/graph/api/resources/managedTenants-windowsdevicemalwarestate)<br>- [windowsProtectionState](https://learn.microsoft.com/en-us/graph/api/resources/managedTenants-windowsprotectionstate) |

## OneNote service limits

| Limit type | Limit per app per user \(delegated context\) | Limit per app \(app-only context\) |
| --- | --- | --- |
| Requests rate | 120 requests per 1 minute and 400 per 1 hour | 240 requests per 1 minute and 800 per 1 hour |
| Concurrent requests | Five concurrent requests | 20 concurrent requests |

The preceding limits apply to the following resources:

|  |
| --- |
| - [notebook](https://learn.microsoft.com/en-us/graph/api/resources/notebook)<br>- [onenote](https://learn.microsoft.com/en-us/graph/api/resources/onenote)<br>- [onenoteOperation](https://learn.microsoft.com/en-us/graph/api/resources/onenoteresource)<br>- [onenotePage](https://learn.microsoft.com/en-us/graph/api/resources/onenotepage)<br>- [onenoteResource](https://learn.microsoft.com/en-us/graph/api/resources/onenoteresource)<br>- [onenoteSection](https://learn.microsoft.com/en-us/graph/api/resources/onenotesection)<br>- [sectionGroup](https://learn.microsoft.com/en-us/graph/api/resources/sectiongroup) |

You can find additional information about best practices in [OneNote API throttling and how to avoid it](https://developer.microsoft.com/en-us/office/blogs/onenote-api-throttling-and-how-to-avoid-it/).

Note

The resources listed earlier don't return a `Retry-After` header on `429 Too Many Requests` responses.

## Open and schema extensions service limits

| Request type | Limit per app per tenant |
| --- | --- |
| Any | 455 requests per 10 seconds |

The preceding limits apply to the following resources:

|  |  |
| --- | --- |
| - [administrativeUnit](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit)<br>- [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact)<br>- [device](https://learn.microsoft.com/en-us/graph/api/resources/device)<br>- [event](https://learn.microsoft.com/en-us/graph/api/resources/event)<br>- [group](https://learn.microsoft.com/en-us/graph/api/resources/group)<br>- [message](https://learn.microsoft.com/en-us/graph/api/resources/message) | - [openTypeExtension](https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension)<br>- [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization)<br>- [post](https://learn.microsoft.com/en-us/graph/api/resources/post)<br>- [schemaExtension](https://learn.microsoft.com/en-us/graph/api/resources/schemaextension)<br>- [user](https://learn.microsoft.com/en-us/graph/api/resources/user) |

## Outlook service limits

Outlook service limits apply to the public cloud and [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

### Limits per mailbox

The Outlook service applies limits to each app ID and mailbox combination - that is, a specific app accessing a specific user or group mailbox. Exceeding the limit for one mailbox doesn't affect the ability of the application to access another mailbox.

| Limit | Applies to |
| --- | --- |
| 10,000 API requests in a 10-minute period | v1.0 and beta endpoints |
| Four concurrent requests | v1.0 and beta endpoints |
| 150 megabytes \(MB\) upload \(PATCH, POST, PUT\) in a 5-minute period | v1.0 and beta endpoints |

### Outlook service resources

| API | Resources |
| --- | --- |
| Search API \(preview\) | <li><a href="https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem" data-linktype="absolute-path">External item (Microsoft Search)</a></li> |
| Profile API | <li><a href="https://learn.microsoft.com/en-us/graph/api/resources/profilephoto" data-linktype="absolute-path">Photo</a></li> |
| Calendar API | <li><a href="https://learn.microsoft.com/en-us/graph/api/resources/event" data-linktype="absolute-path">event</a> </li><br><br><li> <a href="https://learn.microsoft.com/en-us/graph/api/resources/eventmessage" data-linktype="absolute-path">eventMessage</a> </li><br><br><li> <a href="https://learn.microsoft.com/en-us/graph/api/resources/calendar" data-linktype="absolute-path">calendar</a> </li><br><br><li>  <a href="https://learn.microsoft.com/en-us/graph/api/resources/calendargroup" data-linktype="absolute-path">calendarGroup</a> </li><br><br><li> <a href="https://learn.microsoft.com/en-us/graph/api/resources/outlookcategory" data-linktype="absolute-path">outlookCategory</a> </li><br><br><li> <a href="https://learn.microsoft.com/en-us/graph/api/resources/attachment" data-linktype="absolute-path">attachment</a> </li><br><br><li> <a href="https://learn.microsoft.com/en-us/graph/api/resources/place" data-linktype="absolute-path">place (preview)</a></li> |
| Mail API | <li>  <a href="https://learn.microsoft.com/en-us/graph/api/resources/message" data-linktype="absolute-path">message</a> </li><br><br><li> <a href="https://learn.microsoft.com/en-us/graph/api/resources/mailfolder" data-linktype="absolute-path">mailFolder</a> </li><br><br><li> <a href="https://learn.microsoft.com/en-us/graph/api/resources/mailsearchfolder" data-linktype="absolute-path">mailSearchFolder</a> </li><br><br><li> <a href="https://learn.microsoft.com/en-us/graph/api/resources/messagerule" data-linktype="absolute-path">messageRule</a> </li><br><br><li> <a href="https://learn.microsoft.com/en-us/graph/api/resources/outlookcategory" data-linktype="absolute-path">outlookCategory</a> </li><br><br><li> <a href="https://learn.microsoft.com/en-us/graph/api/resources/attachment" data-linktype="absolute-path">attachment</a></li> |
| Mailbox import and export API | <li><a href="https://learn.microsoft.com/en-us/graph/api/resources/mailbox" data-linktype="absolute-path">mailbox</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem" data-linktype="absolute-path">mailboxItem</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder" data-linktype="absolute-path">mailboxFolder</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/resources/exchangeSettings" data-linktype="absolute-path">exchangeSettings</a></li> |
| Personal contacts API | <li><a href="https://learn.microsoft.com/en-us/graph/api/resources/contact" data-linktype="absolute-path">contact</a> </li><br><br><li> <a href="https://learn.microsoft.com/en-us/graph/api/resources/contactfolder" data-linktype="absolute-path">contactFolder</a> </li><br><br><li> <a href="https://learn.microsoft.com/en-us/graph/api/resources/outlookcategory" data-linktype="absolute-path">outlookCategory</a></li> |
| Social and workplace intelligence | <li><a href="https://learn.microsoft.com/en-us/graph/api/resources/person" data-linktype="absolute-path">person</a></li> |
| To-do tasks API \(preview\) | <li><a href="https://learn.microsoft.com/en-us/graph/api/resources/outlooktask" data-linktype="absolute-path">outlookTask</a> </li><br><br><li> <a href="https://learn.microsoft.com/en-us/graph/api/resources/outlooktaskfolder" data-linktype="absolute-path">outlookTaskFolder</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/resources/outlooktaskgroup" data-linktype="absolute-path">outlookTaskGroup</a> </li><br><br><li> <a href="https://learn.microsoft.com/en-us/graph/api/resources/outlookcategory" data-linktype="absolute-path">outlookCategory</a> </li><br><br><li> <a href="https://learn.microsoft.com/en-us/graph/api/resources/attachment" data-linktype="absolute-path">attachment</a></li> |

### Outlook service limits for JSON batching

When an app makes a [JSON batch](https://learn.microsoft.com/en-us/graph/json-batching) request that consists of multiple, *unordered* individual requests to the Outlook service, by default, Microsoft Graph sends the Outlook service up to four individual requests from the batch at a time, regardless of the target mailboxes of those requests. The Outlook service can execute these requests in parallel at any point, also irrespective of the target mailbox. Since Microsoft Graph sends only up to four requests to run in parallel, the execution of that batch stays within [Outlook's concurrency limits for the same mailbox](#limits-per-mailbox), regardless of the app used.

Alternatively, an app can use the [dependsOn](https://learn.microsoft.com/en-us/graph/json-batching#sequencing-requests-with-the-dependson-property) property to order requests within a batch. Microsoft Graph sends the Outlook service one request from the batch at a time following the specified order, and Outlook executes each individual request in the batch sequentially.

In other words, when targeting the *same mailbox*, apps that allow multiple batch requests to run in parallel can use either of the following approaches:

- If the individual requests don't have to be ordered, have individual requests from a single batch run concurrently.
- Use the `dependsOn` property to order requests in a batch, and have up to four such batch requests run concurrently.

## Places service limits

The following Places APIs have a throttling limit of three calls per second:

- [Get operation](https://learn.microsoft.com/en-us/graph/api/place-getoperation?view=graph-rest-beta&preserve-view=true)
- [List operations](https://learn.microsoft.com/en-us/graph/api/place-listoperations?view=graph-rest-beta&preserve-view=true)
- [Upsert places](https://learn.microsoft.com/en-us/graph/api/place-patch-places?view=graph-rest-beta&preserve-view=true)

## Project Rome service limits

| Request type | Limit per user for all apps |
| --- | --- |
| GET | 400 requests per 5 minutes and 12,000 requests per one day |
| POST, PUT, PATCH, DELETE | 100 requests per 5 minutes and 8,000 requests per one day |

The preceding limits apply to the following resources:

- [activityHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/projectrome-historyitem)
- [userActivity](https://learn.microsoft.com/en-us/graph/api/resources/projectrome-activity)

## Security audit log query service limits

The Microsoft Purview Audit Search API applies tenant-level limits to audit log queries submitted through Microsoft Graph. Each tenant receives a baseline allocation. Tenants with more eligible licenses can receive higher limits, up to the maximum capacity allocated by the service. The calculation used to determine a tenant's allocation isn't published.

The following baseline limits apply.

| Limit | Baseline allocation | Scope and behavior |
| --- | ---: | --- |
| Query submissions | At least 200 submissions per day | The limit applies across the tenant and is calculated as a rolling window of 24 hours. When the tenant reaches its daily allocation, the service doesn't accept new queries until the 24-hour rolling usage drops below the limit. |
| Queued or running queries | At least 50 queries | The limit applies across the tenant. Only queries in a nonterminal state, such as queued or running, count toward the limit. New queries can be accepted as existing queries reach a terminal state. |
| Records generated by one query | At least 1,000,000 records | The limit applies separately to each query. If a query exceeds its record-count limit, record generation stops at the applicable threshold and the query completes successfully with information indicating that the limit was exceeded. |

### Handle throttled query submissions

When a query submission is throttled, Microsoft Graph returns `429 Too Many Requests`. If the response includes a `Retry-After` header, wait for the specified interval before retrying the request. Don't retry the request immediately.

For a daily submission limit, retry after the tenant's usage in the 24-hour rolling window drops below the limit. For a concurrent-query limit, retry after one or more queued or running queries reach a terminal state. If a `Retry-After` header isn't provided, use an exponential backoff strategy.

For general guidance, see [Microsoft Graph throttling guidance](https://learn.microsoft.com/en-us/graph/throttling).

### Identify a query that exceeded its record-count limit

Exceeding the per-query record-count limit isn't an error. The query can have a `succeeded` status even when the service stopped generating additional records.

When the information is available, use the following `auditLogQuery` properties:

| Property | Description |
| --- | --- |
| `isRecordCountLimitExceeded` | Indicates whether the query exceeded its per-query record-count limit. Treat this property as the authoritative indicator. |
| `recordCountLimit` | The record-count threshold applied to the query. |
| `approximateReturnedRecordCount` | The approximate number of records generated by the query. This value can be higher or lower than `recordCountLimit` because record counting is distributed. |

Don't determine whether the limit was exceeded by comparing `approximateReturnedRecordCount` with `recordCountLimit`. Use `isRecordCountLimitExceeded`.

## Security detections and incidents service limits

The following limits apply to any request on `/security`.

| Operation | Limit per app per tenant |
| --- | --- |
| Any operation on `alert`, `securityActions`, `secureScore` | 150 requests per minute |
| Any operation on `tiIndicator` | 1,000 requests per minute |
| Any operation on `secureScore` or `secureScorecontrolProfile` | 10,000 API requests in a 10-minute period |
| Any operation on `secureScore` or `secureScorecontrolProfile` | Four concurrent requests |

## Security eDiscovery service limits

The following limits apply to any request on `/security/eDiscoveryCases`.

| Operation | Limit per app per tenant |
| --- | --- |
| Any | Five requests per minute |

## Service Communications service limits

The following limits apply to any type of requests for service communications under `/admin/serviceAnnouncement/`.

| Request type | Limit per app per tenant |
| --- | --- |
| Any | 240 requests per 60 seconds |
| Any | 800 requests per hour |

## Subscription service limits

| Request type | Limit per app for all tenants | Limit per app per tenant |
| --- | --- | --- |
| POST, PUT, DELETE, PATCH | 2000 requests per 20 seconds | 500 requests per 20 seconds |
| POST /reauthorize subscription by ID | 4000 requests per 20 seconds | 1000 requests per 20 seconds |
| GET Subscription by Id | 2000 requests per 20 seconds | 500 requests per 20 seconds |
| GET Subscription List | 40 requests per 20 seconds | 25 requests per 20 seconds |

The preceding limits apply to the [subscription](https://learn.microsoft.com/en-us/graph/api/resources/subscription) resource.

## Tasks and plans service limits

Service limits for Planner aren't available.

The preceding information applies to the following resources:

|  |  |
| --- | --- |
| - [planner](https://learn.microsoft.com/en-us/graph/api/resources/planner)<br>- [plannerAssignedToTaskBoardTaskFormat](https://learn.microsoft.com/en-us/graph/api/resources/plannerassignedtotaskboardtaskformat)<br>- [plannerBucket](https://learn.microsoft.com/en-us/graph/api/resources/plannerbucket)<br>- [plannerBucketTaskBoardTaskFormat](https://learn.microsoft.com/en-us/graph/api/resources/plannerbuckettaskboardtaskformat)<br>- [plannerGroup](https://learn.microsoft.com/en-us/graph/api/resources/plannergroup)<br>- [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan) | - [plannerPlanDetails](https://learn.microsoft.com/en-us/graph/api/resources/plannerplandetails)<br>- [plannerProgressTaskBoardTaskFormat](https://learn.microsoft.com/en-us/graph/api/resources/plannerprogresstaskboardtaskformat)<br>- [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask)<br>- [plannerTaskDetails](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskdetails)<br>- [plannerUser](https://learn.microsoft.com/en-us/graph/api/resources/planneruser) |

## Viva Engage service limits

Viva Engage API calls are subject to rate limiting, allowing 10 requests per user, per app, within a 30-second time period. When you exceed the rate limit, all subsequent requests return a `429 Too Many Requests` response code.

## Windows 365 service limits

| Request type | Limit per tenant for all apps or users | Limit per app or user per tenant |
| :--- | :--- | :--- |
| List Cloud PCs | 180 requests per 60 seconds | 162 requests per 60 seconds |
| Get Cloud PC | 540 requests per 60 seconds | 486 requests per 60 seconds |

Starting September 30, 2025, the per-app/per-user per-tenant throttling limit will be reduced to half of the total per-tenant limit to prevent a single user or app from consuming all the quota within a tenant.

| Request type | Limit per tenant for all apps or users | Limit per app or user per tenant |
| :--- | :--- | :--- |
| List Cloud PCs | 180 requests per 60 seconds | 90 requests per 60 seconds |
| Get Cloud PC | 540 requests per 60 seconds | 270 requests per 60 seconds |

## Related content

- [Best practices for working with Microsoft Graph](https://learn.microsoft.com/en-us/graph/best-practices-concept)
