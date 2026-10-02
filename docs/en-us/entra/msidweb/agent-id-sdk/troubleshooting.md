<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/troubleshooting -->
<!-- Sitemap-Last-Modified: 2026-04-19 -->

# Troubleshooting: Common Microsoft Entra ID Auth SDK \(sidecar\) issues

Solutions for common SDK deployment and operational issues.

## Quick diagnostics

### Check SDK health

```bash
# Check if SDK is running
kubectl get pods -l app=myapp

# Check SDK logs
kubectl logs <pod-name> -c sidecar

# Test health endpoint
kubectl exec <pod-name> -c sidecar -- curl http://localhost:5000/healthz
```

### Check configuration

```bash
# View SDK environment variables
kubectl exec <pod-name> -c sidecar -- env | grep AzureAd

# Check ConfigMap
kubectl get configmap sidecar-config -o yaml

# Check Secrets
kubectl get secret sidecar-secrets -o yaml
```

## Common issues

### Container Won't start

#### Symptom

Pod shows `CrashLoopBackOff` or `Error` status.

#### Possible causes

**Missing Required Configuration**

```bash
# Check logs for configuration errors
kubectl logs <pod-name> -c sidecar

# Look for messages like:
# "AzureAd:TenantId is required"
# "AzureAd:ClientId is required"
```

**Solution**:

```yaml
# Ensure all required configuration is set
env:
- name: AzureAd__TenantId
  value: "<your-tenant-id>"
- name: AzureAd__ClientId
  value: "<your-client-id>"
```

**Invalid Credential Configuration**

```bash
# Check for credential errors in logs
kubectl logs <pod-name> -c sidecar | grep -i "credential"
```

**Solution**: Verify credential configuration and access to Key Vault or secrets.

**Port Conflict**

```bash
# Check if port 5000 is already in use
kubectl exec <pod-name> -c sidecar -- netstat -tuln | grep 5000
```

**Solution**: Change SDK port if needed:

```yaml
env:
- name: ASPNETCORE_URLS
  value: "http://+:5001"
```

### 401 Unauthorized errors

#### Symptom

Requests to SDK return 401 Unauthorized.

#### Possible causes

**Missing Authorization Header**

```bash
# Test with curl
curl -v http://localhost:5000/AuthorizationHeader/Graph
# Should show 401 because no Authorization header
```

**Solution**: Include Authorization header:

```bash
curl -H "Authorization: Bearer <token>" \
  http://localhost:5000/AuthorizationHeader/Graph
```

**Invalid or Expired Token**

```bash
# Check token claims
kubectl exec <pod-name> -c sidecar -- curl -H "Authorization: Bearer <token>" \
  http://localhost:5000/Validate
```

**Solution**: Obtain a new token from Microsoft Entra ID.

**Audience Mismatch**

```bash
# Check logs for audience validation errors
kubectl logs <pod-name> -c sidecar | grep -i "audience"
```

**Solution**: Verify audience configuration matches token:

```yaml
env:
- name: AzureAd__Audience
  value: "api://<your-api-id>"
```

Note

The expected audience value depends on your app registration's [**requestedAccessTokenVersion**](https://learn.microsoft.com/en-us/entra/identity-platform/reference-app-manifest#requestedaccesstokenversion-attribute):

- **Version 2**: Use the `{ClientId}` value directly
- **Version 1** or **null**: Use the App ID URI \(typically `api://{ClientId}` unless you customized it\)

**Scope Validation Failure**

```bash
# Check logs for scope errors
kubectl logs <pod-name> -c sidecar | grep -i "scope"
```

**Solution**: Ensure token contains required scopes:

```yaml
env:
- name: AzureAd__Scopes
  value: "access_as_user"  # Or remove to disable scope validation
```

**PoP validation failure**

A PoP request to `/Validate` returns `401 Unauthorized` with the following challenge when SHR validation fails:

```http
WWW-Authenticate: PoP error="invalid_token"
```

The response can also include the Bearer challenge because `/Validate` accepts both authentication schemes.

Verify that:

- The `Authorization` header uses `PoP <signed-http-request>`.
- `original-method` and `original-uri` are present and match the externally visible request line used to sign the SHR credential.
- The embedded access token is an app-only token.
- Current time hasn't passed the `ts` claim plus `Sidecar:PopValidation:SignedHttpRequestLifetime`, which defaults to `00:05:00`.
- The SHR signature and request-bound `m`, `u`, and `p` claims match. If query validation is enabled, verify the `q` claim as well.

For configuration and integration examples, see [Validate an authorization header](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/validate-authorization-header).

To understand the detailed errors, you might need to increase the log level:

```bash
Logging__LogLevel__Default=Debug 
Logging__LogLevel__Microsoft.Identity.Web=Debug 
Logging__LogLevel__Microsoft.AspNetCore=Debug 
```

### 400 bad request - agent Identity validation

#### Symptom

Requests with agent identity parameters return 400 Bad Request.

#### Error: AgentUsername without AgentIdentity

**Request**:

```bash
curl -H "Authorization: Bearer <token>" \
  "http://localhost:5000/AuthorizationHeader/Graph?AgentUsername=user@contoso.com"
```

**Error Response**:

```json
{
  "status": 400,
  "detail": "AgentUsername requires AgentIdentity to be specified"
}
```

**Solution**: Include AgentIdentity parameter:

```bash
curl -H "Authorization: Bearer <token>" \
  "http://localhost:5000/AuthorizationHeader/Graph?AgentIdentity=<client-id>&AgentUsername=user@contoso.com"
```

#### Error: AgentUsername and AgentUserId both specified

**Request**:

```bash
curl -H "Authorization: Bearer <token>" \
  "http://localhost:5000/AuthorizationHeader/Graph?AgentIdentity=<id>&AgentUsername=user@contoso.com&AgentUserId=<oid>"
```

**Error Response**:

```json
{
  "status": 400,
  "detail": "AgentUsername and AgentUserId are mutually exclusive"
}
```

**Solution**: Use only one:

```bash
# Use AgentUsername
curl -H "Authorization: Bearer <token>" \
  "http://localhost:5000/AuthorizationHeader/Graph?AgentIdentity=<id>&AgentUsername=user@contoso.com"

# OR use AgentUserId
curl -H "Authorization: Bearer <token>" \
  "http://localhost:5000/AuthorizationHeader/Graph?AgentIdentity=<id>&AgentUserId=<oid>"
```

#### Error: Invalid AgentUserId format

**Request**:

```bash
curl -H "Authorization: Bearer <token>" \
  "http://localhost:5000/AuthorizationHeader/Graph?AgentIdentity=<id>&AgentUserId=invalid-guid"
```

**Error Response**:

```json
{
  "status": 400,
  "detail": "AgentUserId must be a valid GUID"
}
```

**Solution**: Provide a valid GUID:

```bash
curl -H "Authorization: Bearer <token>" \
  "http://localhost:5000/AuthorizationHeader/Graph?AgentIdentity=<id>&AgentUserId=12345678-1234-1234-1234-123456789012"
```

### 404 not found - service not configured

#### Symptom

```json
{
  "status": 404,
  "detail": "Downstream API 'UnknownService' not configured"
}
```

#### Possible causes

**Service Name Typo**

```bash
# Wrong service name in URL
curl -H "Authorization: Bearer <token>" \
  http://localhost:5000/AuthorizationHeader/Grafh
# Should be "Graph"
```

**Solution**: Use correct service name from configuration.

**Missing DownstreamApis Configuration**

**Solution**: Add service configuration:

```yaml
env:
- name: DownstreamApis__Graph__BaseUrl
  value: "https://graph.microsoft.com/v1.0"
- name: DownstreamApis__Graph__Scopes
  value: "User.Read"
```

### Token acquisition failures

#### Symptom

500 Internal Server Error when acquiring tokens.

#### AADSTS error codes

**AADSTS50076: Multi-Factor Authentication Required**

```text
AADSTS50076: Due to a configuration change made by your administrator,
or because you moved to a new location, you must use multi-factor authentication.
```

**Solution**: User must complete MFA. This is expected behavior for conditional access policies.

**AADSTS65001: User Consent Required**

```text
AADSTS65001: The user or administrator has not consented to use the application.
```

**Solution**:

1. Request admin consent for the application
2. Ensure delegated permissions are properly configured

**AADSTS700016: Application Not Found**

```text
AADSTS700016: Application with identifier '<client-id>' was not found.
```

**Solution**: Verify ClientId is correct and application exists in tenant.

**AADSTS7000215: Invalid Client Secret**

```text
AADSTS7000215: Invalid client secret is provided.
```

**Solution**:

1. Verify client secret is correct
2. Check if secret has expired
3. Generate new secret and update configuration

**AADSTS700027: Certificate or Private Key Not Configured**

```text
AADSTS700027: The certificate with identifier '<thumbprint>' was not found.
```

**Solution**:

1. Verify certificate is registered in app registration
2. Check certificate configuration in the SDK
3. Ensure certificate is accessible from container

#### Token cache issues

**Solution**: Clear token cache and restart:

```bash
kubectl rollout restart deployment <deployment-name>
```

For distributed cache \(Redis\):

```bash
# Clear Redis cache
redis-cli FLUSHDB
```

### Network connectivity issues

#### Cannot reach Microsoft Entra ID

**Symptom**: Timeout errors when acquiring tokens.

**Diagnostics**:

```bash
# Test connectivity from SDK container
kubectl exec <pod-name> -c sidecar -- curl -v https://login.microsoftonline.com

# Check DNS resolution
kubectl exec <pod-name> -c sidecar -- nslookup login.microsoftonline.com
```

**Solution**:

- Check network policies
- Verify firewall rules allow HTTPS to login.microsoftonline.com
- Ensure DNS is working correctly

#### Cannot reach downstream APIs

**Diagnostics**:

```bash
# Test connectivity to downstream API
kubectl exec <pod-name> -c sidecar -- curl -v https://graph.microsoft.com

# Check configuration
kubectl exec <pod-name> -c sidecar -- env | grep DownstreamApis__Graph__BaseUrl
```

**Solution**:

- Verify downstream API URL is correct
- Check network egress rules
- Ensure API is accessible from cluster

### Application cannot reach the SDK

#### Symptom

Application shows connection errors when calling the SDK.

**Diagnostics**:

```bash
# Test from application container
kubectl exec <pod-name> -c app -- curl -v http://localhost:5000/healthz

# Check if sidecar is listening
kubectl exec <pod-name> -c sidecar -- netstat -tuln | grep 5000
```

**Solution**:

- Verify SIDECAR\_URL environment variable
- Check the SDK is running: `kubectl get pods`
- Ensure port 5000 is not blocked

### Performance issues

#### Slow token acquisition

**Diagnostics**:

```bash
# Enable detailed logging
# Add to SDK configuration:
# - name: Logging__LogLevel__Microsoft.Identity.Web
#   value: "Debug"

# Check logs for timing information
kubectl logs <pod-name> -c sidecar | grep "Token acquisition"
```

**Solutions**:

1. **Check Token Cache**: Ensure caching is enabled and working
2. **Increase Resources**: Allocate more CPU/memory to the SDK
3. **Network Latency**: Check latency to Microsoft Entra ID
4. **Connection Pooling**: Verify HTTP connection reuse

#### High memory usage

**Diagnostics**:

```bash
# Check resource usage
kubectl top pod <pod-name> --containers

# Check for memory leaks in logs
kubectl logs <pod-name> -c sidecar | grep -i "memory"
```

**Solutions**:

1. Increase memory limits
2. Check for token cache size issues
3. Review application usage patterns
4. Consider distributed cache for multiple replicas

### Certificate issues

#### Certificate not found

**Symptom**:

```
Certificate with thumbprint '<thumbprint>' not found in certificate store.
```

**Solution**:

- Verify certificate is mounted correctly
- Check certificate store path
- Ensure certificate permissions are correct

#### Certificate expired

**Symptom**:

```
The certificate has expired.
```

**Solution**:

1. Generate new certificate
2. Register in Microsoft Entra ID
3. Update SDK configuration
4. Redeploy containers

#### Key Vault access denied

**Symptom**:

```
Access denied to Key Vault '<vault-name>'.
```

**Solution**:

- Verify managed identity has access policy to Key Vault
- Check Key Vault firewall rules
- Ensure certificate exists in Key Vault

### Outbound signed HTTP request \(SHR\) issues

#### Invalid PoP token

**Symptom**: Downstream API rejects PoP token.

**Diagnostics**:

```bash
# Check if PoP token is being requested
kubectl logs <pod-name> -c sidecar | grep -i "pop"

# Verify PopPublicKey is configured correctly
kubectl exec <pod-name> -c sidecar -- env | grep PopPublicKey
```

**Solution**:

- Verify public key is correctly base64 encoded
- Ensure downstream API supports PoP tokens
- Check PoP token format

#### Missing private key

**Symptom**: Cannot sign HTTP request.

**Solution**: Ensure private key is available to application for signing requests.

## Error reference table

| Error Code | Message | Cause | Solution |
| --- | --- | --- | --- |
| 400 | AgentUsername requires AgentIdentity | AgentUsername without AgentIdentity | Add AgentIdentity parameter |
| 400 | AgentUsername and AgentUserId are mutually exclusive | Both parameters specified | Use only one parameter |
| 400 | AgentUserId must be a valid GUID | Invalid GUID format | Provide valid GUID |
| 400 | Service name is required | Missing service name in path | Include service name in URL |
| 401 | Unauthorized | Missing or malformed Authorization header | Include a valid Bearer or PoP credential |
| 401 | Unauthorized | Invalid or expired Bearer token | Obtain a new token |
| 401 | PoP error="invalid\_token" | SHR signature, request binding, timestamp, original-request headers, or embedded app-only token validation failed | Verify the PoP credential, original method and URI, timestamp, and embedded token |
| 403 | Forbidden | Missing required scopes | Request token with correct scopes |
| 404 | Downstream API not configured | Service not in configuration | Add DownstreamApis configuration |
| 500 | Failed to acquire token | Various MSAL errors | Check logs for specific AADSTS error |
| 503 | Service Unavailable | Health check failure | Check SDK status and configuration |

## Debugging tools

### Enable detailed logging

```yaml
env:
- name: Logging__LogLevel__Default
  value: "Debug"
- name: Logging__LogLevel__Microsoft.Identity.Web
  value: "Trace"
- name: Logging__LogLevel__Microsoft.AspNetCore
  value: "Debug"
```

**Warning**: Debug/Trace logging may log sensitive information. Use only in development or temporarily in production.

### Test token validation

```bash
# Validate token
curl -H "Authorization: Bearer <token>" \
  http://localhost:5000/Validate | jq .

# Check claims
curl -H "Authorization: Bearer <token>" \
  http://localhost:5000/Validate | jq '.claims'

# Validate an app-only SHR PoP credential
curl -i \
  -H "Authorization: PoP <signed-http-request>" \
  -H "original-method: GET" \
  -H "original-uri: https://api.contoso.com/data" \
  http://localhost:5000/Validate
```

### Test token acquisition

```bash
# Get authorization header
curl -H "Authorization: Bearer <token>" \
  http://localhost:5000/AuthorizationHeader/Graph | jq .

# Extract and decode token
curl -H "Authorization: Bearer <token>" \
  http://localhost:5000/AuthorizationHeader/Graph | \
  jq -r '.authorizationHeader' | \
  cut -d' ' -f2 | \
  jwt decode -
```

### Monitor with Application Insights

If configured:

```bash
# Query Application Insights
az monitor app-insights query \
  --app <app-insights-name> \
  --analytics-query "traces | where message contains 'token acquisition' | take 100"
```

## Getting help

### Collect diagnostic information

When opening an issue, include:

1. **SDK Version**:

   ```bash
   kubectl describe pod <pod-name> | grep -A 5 "sidecar:"
   ```

2. **Configuration** \(redact sensitive data\):

   ```bash
   kubectl get configmap sidecar-config -o yaml
   ```

3. **Logs** \(last 100 lines\):

   ```bash
   kubectl logs <pod-name> -c sidecar --tail=100
   ```

4. **Error Messages**: Full error response from the SDK
5. **Request Details**: HTTP method, endpoint, parameters used

### Support resources

- **GitHub Issues**: [microsoft-identity-web/issues](https://github.com/AzureAD/microsoft-identity-web/issues)
- **Microsoft Q&A**: [Microsoft Identity Platform](https://learn.microsoft.com/en-us/answers/topics/azure-active-directory.html)
- **Stack Overflow**: Tag `[microsoft-identity-web]`

## Best practices for troubleshooting

1. **Start with Health Check**: Always verify the SDK is healthy first
2. **Check Logs**: SDK logs contain valuable diagnostic information
3. **Verify Configuration**: Ensure all required settings are present and correct
4. **Test Incrementally**: Start with simple requests, add complexity gradually
5. **Use Correlation IDs**: Include correlation IDs for tracing across services
6. **Monitor Continuously**: Set up alerts for authentication failures
7. **Document Issues**: Keep notes on issues and resolutions for future reference

### Related resources

- [Installation Guide](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/installation)
- [Configuration Reference](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/configuration)
- [Security Best Practices](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/security)
- [FAQ](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/faq)
