<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/ -->
<!-- Sitemap-Last-Modified: 2025-01-29 -->

# Use the WOPI protocol to integrate with Microsoft 365 for the web

You can use the Web Application Open Platform Interface \(WOPI\) protocol to integrate Microsoft 365 for the web with your application. The WOPI protocol lets Microsoft 365 for the web access and change files that are stored in your service.

To integrate your application with Microsoft 365 for the web, do the following:

1. Be a member of the Microsoft 365 - Cloud Storage Partner Program. Currently, integration with the Microsoft 365 for the web cloud service is available to cloud storage partners. You can learn more about the program, as well as how to apply, at [https://developer.microsoft.com/office/cloud-storage-partner-program](https://aka.ms/cspp-apply).

   Important

   The Microsoft 365 - Cloud Storage Partner Program is for independent software vendors whose business is cloud storage. It's not open to Microsoft 365 customers directly.
2. Set up the WOPI protocol - a set of REST endpoints that expose information about the documents that you want to view or edit in Microsoft 365 for the web. The set of WOPI operations that must be supported is described in the section titled [WOPI implementation requirements on Microsoft 365 for the web integration](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/wopi-requirements).
3. Read some XML from an Microsoft 365 for the web URL that provides information about the capabilities that Microsoft 365 for the web applications expose, and information on how to invoke them. This process is called [WOPI discovery](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery).
4. Provide an HTML page \(or pages\) that host the Microsoft 365 for the web iframe. This is called the [host page](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#host-page) and is the page your users visit when they open or edit Microsoft 365 documents in Microsoft 365 for the web.
5. Optionally integrate your own UI elements with Microsoft 365 for the web. For example, when users choose `Share` in Microsoft 365 for the web, you can show your own sharing UI. These interaction points are described in the section titled [Using PostMessage to interact with the Microsoft 365 for the web application iframe](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/postmessage).

### How to read this documentation

This documentation contains complete information on how to integrate with Microsoft 365 for the web, including:

- How to implement the WOPI protocol
- How Microsoft 365 for the web uses the protocol
- How to test your integration
- The [process for shipping your integration](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/shipping), and much more.

It can be difficult to know where to begin. The following guidelines can direct you to the specific sections of the most help to you.

**If you want to know why Microsoft 365 integration might be useful to you,** and what capabilities it provides, read the following sections:

- [Integrate with Microsoft 365 for the web](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/overview) - A high level overview of the scenarios enabled by Microsoft 365 for the web integration, as well as a brief description of some of the key technical elements in a successful integration.
- [Use the WOPI protocol to integrate with Microsoft 365 for the web](#use-the-wopi-protocol-to-integrate-with-office-for-the-web) - A brief description of the technical pieces that you must implement to integrate with Microsoft 365 for the web.

**If you are an engineer** about to begin implementing a WOPI host, read the [Key concepts](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#key-concepts-to-understand-for-wopi-integration) section first. When designing your WOPI implementation, you must keep in mind the expectations around [file IDs](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#file-id), [access tokens](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token), and [locks](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#lock). These concepts are critical to a successful integration with Microsoft 365 for the web.

And also be sure to read the following sections:

- [WOPI Validator](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/validator)
- [Troubleshooting interactions with Microsoft 365 for the web](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/troubleshooting)
- [Microsoft 365 for the web environments](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/environments)

**If you are a back-end engineer,** begin with the following sections in addition to the [Key concepts](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#key-concepts-to-understand-for-wopi-integration) section and other general sections listed above:

- [WOPI discovery](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery)
- [WOPI REST endpoints](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/endpoints)
- [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo)
- [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/lock)

Once you have read these sections, any of the other core WOPI operations are useful to read through, such as [GetFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getfile#getfile), [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile), [PutRelativeFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putrelativefile), [UnlockAndRelock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlockandrelock#unlockandrelock), and so on.

**If you are a front-end engineer,** begin with the following sections in addition to the [Key concepts](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#key-concepts-to-understand-for-wopi-integration) section and other general sections listed above:

- [Building a host page](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/hostpage)
- [Using PostMessage to interact with the Office for the web application iframe](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/postmessage)
- [WOPI discovery](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery), specifically the [WOPI actions](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#wopi-actions) section

Finally, **if you are looking for more details about the process for shipping your integration,** see the [Shipping your Microsoft 365 for the web integration](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/shipping) section.
