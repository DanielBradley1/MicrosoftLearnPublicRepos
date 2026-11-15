<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/resource-policy-known-issues -->
<!-- Sitemap-Last-Modified: 2026-11-12 -->

# Microsoft Entra resource policy known issues \(preview\)

Use this article with [Test and troubleshoot a resource policy](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/resource-policy-test-troubleshoot) when policy management or request-time behavior differs from your expectations.

## Assignment changes aren't immediately reflected in requests

Assignment changes can take up to 10 minutes to affect incoming requests. Use `evaluateAssignedPolicies` to test saved settings without that delay, then wait for [assignment propagation](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/resource-policy-evaluation#assignment-propagation) before testing real requests again.

## Report an unexpected result

Collect the operation, approximate time, request correlation information, assignment reference, policy version, enforcement mode, and available evaluation error details. Remove secrets and unnecessary personal data before sharing diagnostic information.

## Related content

- [How resource policy evaluation works](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/resource-policy-evaluation).
- [Analyze resource policy evaluation audit logs](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/resource-policy-logs).
- [Resource policy service limits](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/resource-policy-service-limits).
