# DomainManagementApi

All URIs are relative to *https://spider.noctisnet.com*

|Method | HTTP request | Description|
|------------- | ------------- | -------------|
|[**findSubdomains**](#findsubdomains) | **GET** /domainer/api/domains/subdomains/{baseDomain} | Find subdomains|

# **findSubdomains**
> DomainerStringListResponse findSubdomains()

Finds domains that are subdomains of the given base domain (e.g., finding \'www.example.com\' for base \'example.com\'). Allows filtering by absolute domain level (dot count). NOTE: This differs from relative depth filtering.

### Example

```typescript
import {
    DomainManagementApi,
    Configuration
} from './api';

const configuration = new Configuration();
const apiInstance = new DomainManagementApi(configuration);

let baseDomain: string; //Base domain name (e.g., example.com) (default to undefined)
let limit: number; //Maximum number of results (optional) (default to 100)
let level: 'ALL' | 'IMMEDIATE' | 'MAX_DEPTH'; //Level of subdomains to find relative to the base domain (ALL, IMMEDIATE=one level deeper, MAX_DEPTH=deepest found relative to base). (optional) (default to undefined)

const { status, data } = await apiInstance.findSubdomains(
    baseDomain,
    limit,
    level
);
```

### Parameters

|Name | Type | Description  | Notes|
|------------- | ------------- | ------------- | -------------|
| **baseDomain** | [**string**] | Base domain name (e.g., example.com) | defaults to undefined|
| **limit** | [**number**] | Maximum number of results | (optional) defaults to 100|
| **level** | [**&#39;ALL&#39; | &#39;IMMEDIATE&#39; | &#39;MAX_DEPTH&#39;**]**Array<&#39;ALL&#39; &#124; &#39;IMMEDIATE&#39; &#124; &#39;MAX_DEPTH&#39;>** | Level of subdomains to find relative to the base domain (ALL, IMMEDIATE&#x3D;one level deeper, MAX_DEPTH&#x3D;deepest found relative to base). | (optional) defaults to undefined|


### Return type

**DomainerStringListResponse**

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
|**200** | Subdomains found |  -  |
|**400** | Invalid base domain name |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

