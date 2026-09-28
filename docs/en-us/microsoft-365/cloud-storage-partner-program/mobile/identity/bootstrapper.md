<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/identity/bootstrapper -->
<!-- Sitemap-Last-Modified: 2023-05-02 -->

# Bootstrap OAuth2

The first step for the OAuth2 flow from Microsoft 365 for mobile to your application is an **unauthenticated** request to the bootstrapper endpoint.

**Unauthenticated** means that no access token is attached in the [Authorization](https://tools.ietf.org/html/rfc7235#section-4.2) HTTP header, or that an expired or otherwise invalid token is attached.

Important

The bootstrapper URL must be an HTTPS endpoint, and connections to the bootstrapper must be made using TLS.

Important

The bootstrapper URL must be supplied as the `BootstrapUrl` property of the onboarding information described in the section titled [**Onboarding information**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/onboarding/onboarding).

The file and the bootstrapper can be at a different host and/or a different path, as long as they conform to the requirement that the endpoint is `/wopibootstrapper` and otherwise meets the requirements for the request/response. Additionally, it's important to note that the resource specified by the bootstrapper must be in a trusted domain configured as part of [provisioning your service entry with Microsoft](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/onboarding/onboarding).

For full details, see the [Unauthenticated response](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap#unauthenticated-response) page.
