<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/test-launch/session-origin-naming -->
<!-- Sitemap-Last-Modified: 2024-12-12 -->

# Session origin naming for the Microsoft 365 Document Collaboration Partner Program

The Microsoft 365 Document Collaboration Partner Program \(MDCPP\) enables your users to view and edit Excel, PowerPoint, and Word documents directly in your collaboration application. The program provides a DocumentInfo API where you can optionally pass in session origin details. It's strongly recommended that you send that information because it helps with segmenting data for telemetry, investigation, and reporting. Consider the following naming guidance when passing information to the [DocumentInfo.sessionOrigin property](https://learn.microsoft.com/en-us/javascript/api/@microsoft/document-collaboration-sdk/documentinfo#@microsoft-document-collaboration-sdk-documentinfo-sessionorigin).

## Nomenclature

The text you provide to the sessionOrigin parameter should be comprised of three parts separated by a dot in the following form.

{APPLICATION}.{SOURCE}.{SCENARIO}

The following is a brief explanation of what each part represents.

1. **Application** \(required\). The application a session originates from.
2. **Source** \(required\). The application part, page, or feature that initiated the document boot.
3. **Scenario** \(optional\). The scenario that initiated the document boot. This can be a subpart of the Source and omitted if it isn't needed.

Next are example values for each part. *Contoso* is used to represent a partner company in the program. In your case, it will be a host value that represents your company and was onboarded to the program.

***Application part***

| {APPLICATION} | Example values |
| :--- | :--- |
| Contoso Desktop | CONTOSO-DESKTOP |
| Contoso Web | CONTOSO-WEB |

***Source part***

| {SOURCE} | Example values |
| :--- | :--- |
| Opening document | CONTENT |

***Scenario part***

| {SCENARIO} | Example values |
| :--- | :--- |
| Teams channel | TEAMS-CHANNEL |
| Teams chat | TEAMS-CHAT |

Using these example values, the text passed to sessionOrigin could look like the following:

CONTOSO-DESKTOP.CONTENT.TEAMS-CHANNEL

**Note**: These values are examples and aren't prescriptive. Feel free to use values that are more appropriate for your scenarios. However, the format **{APPLICATION}.{SOURCE}.{SCENARIO}** is prescriptive.

## Host name

The host name you pass as part of the {APPLICATION} value must meet the following requirements.

- The name that was onboarded to the MDCPP service.
- The same value passed to the [HostInfo.hostName](https://learn.microsoft.com/en-us/javascript/api/@microsoft/document-collaboration-sdk/hostinfo#@microsoft-document-collaboration-sdk-hostinfo-hostname) property in the MDCPP API.
