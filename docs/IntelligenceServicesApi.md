# IntelligenceServicesApi

All URIs are relative to *https://spider.noctisnet.com*

|Method | HTTP request | Description|
|------------- | ------------- | -------------|
|[**getDomainIntelligence**](#getdomainintelligence) | **GET** /intelligence/v1/domain/{domain} | Get comprehensive domain intelligence with streaming support|
|[**getIpIntelligence**](#getipintelligence) | **GET** /intelligence/v1/ip/{address} | Get comprehensive IP address intelligence with streaming support|

# **getDomainIntelligence**
> DomainIntelligenceResponse getDomainIntelligence()

Analyzes a domain name and returns comprehensive intelligence data from multiple sources.  **🚀 Response Modes:** - **Batch Mode** (Default): Complete JSON response in 2-5 seconds - **Streaming Mode**: Server-Sent Events with 200ms time-to-first-byte   - Accept: `application/json` for batch mode   - Accept: `text/event-stream` for streaming mode  **Key Features:** - WHOIS registration data with ownership history - Complete DNS record enumeration (A, AAAA, MX, NS, TXT, CNAME, SOA) - Subdomain discovery and enumeration - Link analysis showing connected domains - IP intelligence for all resolved addresses - Trademark and brand protection status - Infrastructure relationships and shared hosting  **Streaming Example:** ```bash curl -N -H \'Accept: text/event-stream\' \\      -H \'Authorization: Bearer {token}\' \\      https://api.example.com/intelligence/v1/domain/example.com ```  **Streaming Events:** - `whois`: Domain registration info - `dns`: DNS records - `subdomains`: Discovered subdomains - `ip_intelligence`: Intelligence for each resolved IP - `complete`: Final aggregated data  **Input Processing:** - Automatically strips protocols (http://, https://) - Removes www prefix if present - Validates domain format before processing  **Note:** Swagger UI only displays batch mode. Use curl or EventSource for streaming.

### Example

```typescript
import {
    IntelligenceServicesApi,
    Configuration
} from './api';

const configuration = new Configuration();
const apiInstance = new IntelligenceServicesApi(configuration);

let domain: string; //Domain name to analyze. Can be a root domain or subdomain. Protocol and www prefix are automatically removed. (default to undefined)

const { status, data } = await apiInstance.getDomainIntelligence(
    domain
);
```

### Parameters

|Name | Type | Description  | Notes|
|------------- | ------------- | ------------- | -------------|
| **domain** | [**string**] | Domain name to analyze. Can be a root domain or subdomain. Protocol and www prefix are automatically removed. | defaults to undefined|


### Return type

**DomainIntelligenceResponse**

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
|**200** | Domain intelligence data successfully retrieved |  * X-RateLimit-Limit - Number of requests allowed per hour <br>  |
|**400** | Invalid domain name format |  -  |
|**401** | Authentication required |  -  |
|**404** | Domain not found or unregistered |  -  |
|**429** | Rate limit exceeded |  -  |
|**500** | Internal server error during intelligence aggregation |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **getIpIntelligence**
> IpIntelligenceResponse getIpIntelligence()

Analyzes an IP address and returns comprehensive intelligence data aggregated from multiple sources.  **🚀 Response Modes:** - **Batch Mode** (Default): Complete JSON response in 2-3 seconds - **Streaming Mode**: Server-Sent Events with 150ms time-to-first-byte   - Accept: `application/json` for batch mode   - Accept: `text/event-stream` for streaming mode  **Key Features:** - Geolocation with city-level precision and confidence scores - Network topology including ASN, BGP prefixes, and routing visibility - ISP and organization identification - DNS relationships showing associated domains - Risk scoring based on threat intelligence feeds - RPKI validation and routing security assessment - Historical routing data and stability metrics  **Streaming Example:** ```bash curl -N -H \'Accept: text/event-stream\' \\      -H \'Authorization: Bearer {token}\' \\      https://api.example.com/intelligence/v1/ip/8.8.8.8 ```  **Note:** Swagger UI only displays batch mode. Use curl or EventSource for streaming.

### Example

```typescript
import {
    IntelligenceServicesApi,
    Configuration
} from './api';

const configuration = new Configuration();
const apiInstance = new IntelligenceServicesApi(configuration);

let address: string; //IPv4 or IPv6 address to analyze. Supports standard notation (e.g., 192.168.1.1 or 2001:db8::1) (default to undefined)

const { status, data } = await apiInstance.getIpIntelligence(
    address
);
```

### Parameters

|Name | Type | Description  | Notes|
|------------- | ------------- | ------------- | -------------|
| **address** | [**string**] | IPv4 or IPv6 address to analyze. Supports standard notation (e.g., 192.168.1.1 or 2001:db8::1) | defaults to undefined|


### Return type

**IpIntelligenceResponse**

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
|**200** | IP intelligence data successfully retrieved |  * X-RateLimit-Limit - Number of requests allowed per hour <br>  * X-RateLimit-Remaining - Number of requests remaining <br>  |
|**400** | Invalid IP address format |  -  |
|**401** | Authentication required |  -  |
|**404** | IP address not found or private/reserved |  -  |
|**429** | Rate limit exceeded |  * Retry-After - Number of seconds to wait before retrying <br>  |
|**500** | Internal server error during intelligence aggregation |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

