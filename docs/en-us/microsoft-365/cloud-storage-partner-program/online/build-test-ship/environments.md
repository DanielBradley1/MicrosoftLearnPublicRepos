<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/environments -->
<!-- Sitemap-Last-Modified: 2025-01-29 -->

# Microsoft 365 for the web environments

Microsoft 365 for the web provides two environments that cloud storage partners can use. The [WOPI discovery URLs](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/environments#wopi-discovery-urls) for each environment are provided below.

Initially you're given access to the test environment \(also called *Dogfood*\), that you use when building and testing your integration.

Once you are ready to release your integration, you can start the [Launch process](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/shipping). As part of that process, your application is given access to the production environment.

## Test environment

The test environment is updated frequently - usually at least once per day - and all initial testing should be done against it. Initially, this is the only environment you can access.

The test environment runs the most recent Microsoft 365 for the web code available. This means that you might see features there that aren't yet available in production. However, the WOPI interactions between Microsoft 365 for the web and your WOPI host should not differ dramatically between test and production.

Because builds are deployed frequently to this environment, you might see regressions in behavior. However, the deployment cadence supports pushing changes quickly, so contact Microsoft if you experience any strange or unexpected behavior when using the test environment.

Important

End users shouldn't access the test environment. If you're making Microsoft 365 for the web integration available to your end-users, you must be in the production environment.

## Production environment

The production environment is updated weekly.

### Primary requirements for production environment

Note

This is not an exhaustive list.

- Hosts must use HTTPS in the production Microsoft 365 for the web environment. HTTP isn't supported.
- Domains on the [WOPI domain allow list](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/settings#wopi-domain-allow-list) must be a WOPI-dedicated subdomain in production.
- Domains must be owned by the partner.
- Production changes can take **4-5 weeks** to fully roll out; this includes domain changes.

## WOPI discovery URLs

| Environment | Discovery URL |
| --- | --- |
| Production | [https://onenote.officeapps.live.com/hosting/discovery](https://onenote.officeapps.live.com/hosting/discovery) |
| Test/Dogfood | [https://ffc-onenote.officeapps.live.com/hosting/discovery](https://ffc-onenote.officeapps.live.com/hosting/discovery) |

Tip

These URLs are publicly accessible. However, you won't be able to invoke any [**WOPI actions**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#wopi-actions) successfully unless your WOPI domain is added to the [**WOPI domain allow list**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/settings#wopi-domain-allow-list).
