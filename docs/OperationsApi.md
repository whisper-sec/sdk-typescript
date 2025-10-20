# OperationsApi

All URIs are relative to *https://api.whisper.security*

|Method | HTTP request | Description|
|------------- | ------------- | -------------|
|[**createInfrastructureMap**](#createinfrastructuremap) | **POST** /v1/ops/map | Map Infrastructure Relationships (Asynchronous)|
|[**createInfrastructureScan**](#createinfrastructurescan) | **POST** /v1/ops/scan | Infrastructure Security Scan (Asynchronous)|
|[**createMonitoringAlert**](#createmonitoringalert) | **POST** /v1/ops/monitor/{target}/alert | Configure Monitoring Alerts (Asynchronous)|
|[**createScreenshot**](#createscreenshot) | **POST** /v1/ops/screenshot | Capture a Website Screenshot (Asynchronous)|
|[**getChangeDetection**](#getchangedetection) | **GET** /v1/ops/changes/{target} | Get Infrastructure Change History|
|[**getJob**](#getjob) | **GET** /v1/ops/jobs/{jobId} | Get Asynchronous Job Status and Results|
|[**getMonitoringStatus**](#getmonitoringstatus) | **GET** /v1/ops/monitor/{target} | Get Monitoring Status and Metrics|
|[**getScreenshotHistory**](#getscreenshothistory) | **GET** /v1/ops/screenshot/history | Get Screenshot History|
|[**scheduleScreenshot**](#schedulescreenshot) | **POST** /v1/ops/screenshot/schedule | Schedule Recurring Screenshots (Asynchronous)|

# **createInfrastructureMap**
> JobResponse createInfrastructureMap(body)

<p>Creates a comprehensive map of infrastructure relationships starting from a domain or IP. Discovers connected assets through shared hosting, DNS, certificates, and network relationships.</p> <h4>Mapping Depth Levels:</h4> <ul>     <li><b>Depth 1:</b> Direct relationships only (~30 seconds, 10-50 assets)</li>     <li><b>Depth 2:</b> 2 hops out (~2-5 minutes, 50-500 assets)</li>     <li><b>Depth 3:</b> 3 hops out (~10-30 minutes, 500-5000 assets)</li> </ul> <h4>Relationship Types Discovered:</h4> <ul>     <li>Domains on same IP</li>     <li>Domains sharing nameservers</li>     <li>Domains with same SSL certificate</li>     <li>IPs in same ASN</li>     <li>Domains with same registrant</li> </ul> <h4>Output Format:</h4> <p>Results returned as graph data compatible with visualization libraries (nodes and edges).</p> <h4>Use Cases:</h4> <ul>     <li>Threat actor infrastructure mapping</li>     <li>Discovering related phishing domains</li>     <li>Finding shadow IT and forgotten assets</li> </ul> 

### Example

```typescript
import {
    OperationsApi,
    Configuration
} from '@whisper-security/whisper-api-sdk';

const configuration = new Configuration();
const apiInstance = new OperationsApi(configuration);

let body: object; //Mapping configuration. Example: ```json {   \"startPoint\": \"example.com\",   \"depth\": 2 } ``` 

const { status, data } = await apiInstance.createInfrastructureMap(
    body
);
```

### Parameters

|Name | Type | Description  | Notes|
|------------- | ------------- | ------------- | -------------|
| **body** | **object**| Mapping configuration. Example: &#x60;&#x60;&#x60;json {   \&quot;startPoint\&quot;: \&quot;example.com\&quot;,   \&quot;depth\&quot;: 2 } &#x60;&#x60;&#x60;  | |


### Return type

**JobResponse**

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
|**400** | Invalid starting point or depth (must be 1-3). |  -  |
|**202** | Mapping job successfully accepted. Poll &#x60;/v1/ops/jobs/{jobId}&#x60; for results. |  -  |
|**401** | Authentication failed. Missing or invalid API key. |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **createInfrastructureScan**
> JobResponse createInfrastructureScan(infraScanRequest)

<p>Initiates a comprehensive security scan of a domain\'s infrastructure. Performs reconnaissance, port scanning, service detection, and vulnerability assessment.</p> <h4>Scan Types:</h4> <ul>     <li><b>comprehensive:</b> Full scan including all modules (recommended for complete assessment)</li>     <li><b>subdomains:</b> Subdomain enumeration only</li>     <li><b>ports:</b> Port scanning and service detection</li>     <li><b>technologies:</b> Technology stack detection</li>     <li><b>vulnerabilities:</b> Known vulnerability checks</li>     <li><b>ssl:</b> SSL/TLS configuration and certificate analysis</li>     <li><b>dns:</b> DNS configuration and zone transfer tests</li>     <li><b>whois:</b> Registration and ownership information</li> </ul> <h4>Performance:</h4> <ul>     <li><b>Quick scans:</b> 30-60 seconds (subdomains, dns, whois)</li>     <li><b>Comprehensive scan:</b> 5-15 minutes depending on infrastructure size</li> </ul> <h4>Use Cases:</h4> <ul>     <li>Pre-engagement reconnaissance for penetration testing</li>     <li>Attack surface assessment</li>     <li>Infrastructure inventory and mapping</li>     <li>Vulnerability management</li> </ul> 

### Example

```typescript
import {
    OperationsApi,
    Configuration,
    InfraScanRequest
} from '@whisper-security/whisper-api-sdk';

const configuration = new Configuration();
const apiInstance = new OperationsApi(configuration);

let infraScanRequest: InfraScanRequest; //Scan configuration including target domain and scan type.

const { status, data } = await apiInstance.createInfrastructureScan(
    infraScanRequest
);
```

### Parameters

|Name | Type | Description  | Notes|
|------------- | ------------- | ------------- | -------------|
| **infraScanRequest** | **InfraScanRequest**| Scan configuration including target domain and scan type. | |


### Return type

**JobResponse**

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
|**202** | Scan job successfully accepted. Poll &#x60;/v1/ops/jobs/{jobId}&#x60; for results. |  -  |
|**400** | Invalid domain or scan type. |  -  |
|**401** | Authentication failed. Missing or invalid API key. |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **createMonitoringAlert**
> JobResponse createMonitoringAlert(body)

<p>Create alert rules for a monitored asset. Get notified via webhook, email, or Slack when specific conditions are met.</p> <h4>Alert Types:</h4> <ul>     <li><b>downtime:</b> Site becomes unreachable</li>     <li><b>dns_change:</b> DNS records modified</li>     <li><b>whois_change:</b> Registration details updated</li>     <li><b>ssl_expiring:</b> Certificate expires soon (7, 14, 30 days)</li>     <li><b>content_change:</b> Page content modified</li>     <li><b>technology_change:</b> Tech stack changes detected</li> </ul> <h4>Notification Channels:</h4> <ul>     <li>Webhook (POST to your endpoint)</li>     <li>Email</li>     <li>Slack</li>     <li>PagerDuty</li> </ul> <h4>Example Configuration:</h4> <pre><code>{   \"type\": \"ssl_expiring\",   \"threshold_days\": 14,   \"channels\": [\"email\", \"slack\"],   \"email\": \"alerts@example.com\",   \"slack_webhook\": \"https://hooks.slack.com/...\" }</code></pre> 

### Example

```typescript
import {
    OperationsApi,
    Configuration
} from '@whisper-security/whisper-api-sdk';

const configuration = new Configuration();
const apiInstance = new OperationsApi(configuration);

let target: string; //The domain or IP address to configure alerts for. (default to undefined)
let body: object; //Alert configuration including type, thresholds, and notification channels.

const { status, data } = await apiInstance.createMonitoringAlert(
    target,
    body
);
```

### Parameters

|Name | Type | Description  | Notes|
|------------- | ------------- | ------------- | -------------|
| **body** | **object**| Alert configuration including type, thresholds, and notification channels. | |
| **target** | [**string**] | The domain or IP address to configure alerts for. | defaults to undefined|


### Return type

**JobResponse**

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
|**202** | Alert configuration job accepted. Poll &#x60;/v1/ops/jobs/{jobId}&#x60; for status. |  -  |
|**400** | Invalid alert configuration. |  -  |
|**401** | Authentication failed. Missing or invalid API key. |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **createScreenshot**
> JobResponse createScreenshot(screenshotRequest)

<p>Initiates an asynchronous job to capture a screenshot of a website. Supports various viewport sizes, full-page captures, and JavaScript rendering.</p> <p><b>Performance Note:</b> A typical screenshot capture takes 10-30 seconds. Poll the `/v1/ops/jobs/{jobId}` endpoint to retrieve the URL of the final image.</p> <p><b>Output:</b> The job result will contain a URL to download the screenshot image in the specified format (PNG, JPEG, or WebP).</p> 

### Example

```typescript
import {
    OperationsApi,
    Configuration,
    ScreenshotRequest
} from '@whisper-security/whisper-api-sdk';

const configuration = new Configuration();
const apiInstance = new OperationsApi(configuration);

let screenshotRequest: ScreenshotRequest; //The URL and options for the screenshot capture.

const { status, data } = await apiInstance.createScreenshot(
    screenshotRequest
);
```

### Parameters

|Name | Type | Description  | Notes|
|------------- | ------------- | ------------- | -------------|
| **screenshotRequest** | **ScreenshotRequest**| The URL and options for the screenshot capture. | |


### Return type

**JobResponse**

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
|**202** | Screenshot job successfully accepted. |  -  |
|**429** | Rate limit exceeded. |  -  |
|**400** | Invalid URL or options provided. |  -  |
|**401** | Authentication failed. Missing or invalid API key. |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **getChangeDetection**
> getChangeDetection()

<p>Retrieves detected changes in infrastructure configuration for a domain or IP over time. Essential for security monitoring and compliance auditing.</p> <h4>Change Types Tracked:</h4> <ul>     <li><b>dns:</b> A, AAAA, MX, NS, TXT record changes</li>     <li><b>whois:</b> Registrant, registrar, nameserver changes</li>     <li><b>ssl:</b> Certificate replacements and expirations</li>     <li><b>ip:</b> IP address changes for domains</li>     <li><b>content:</b> Homepage content modifications</li>     <li><b>technology:</b> Tech stack changes</li> </ul> <h4>Response Format:</h4> <p>Timeline of changes with before/after values:</p> <pre><code>{   \"changes\": [     {       \"timestamp\": \"2025-01-15T10:30:00Z\",       \"type\": \"dns\",       \"field\": \"A_RECORD\",       \"old_value\": \"8.8.8.8\",       \"new_value\": \"1.1.1.1\"     }   ] }</code></pre> <h4>Use Cases:</h4> <ul>     <li>Security incident investigation</li>     <li>Compliance and audit trails</li>     <li>Detecting unauthorized changes</li>     <li>Infrastructure change management</li> </ul> 

### Example

```typescript
import {
    OperationsApi,
    Configuration
} from '@whisper-security/whisper-api-sdk';

const configuration = new Configuration();
const apiInstance = new OperationsApi(configuration);

let target: string; //The domain or IP address to check for changes. (default to undefined)
let type: 'all' | 'dns' | 'whois' | 'ssl' | 'ip' | 'content' | 'technology'; //Type of changes to retrieve. (optional) (default to undefined)
let since: string; //ISO 8601 timestamp to retrieve changes from. Omit to get all changes. (optional) (default to undefined)

const { status, data } = await apiInstance.getChangeDetection(
    target,
    type,
    since
);
```

### Parameters

|Name | Type | Description  | Notes|
|------------- | ------------- | ------------- | -------------|
| **target** | [**string**] | The domain or IP address to check for changes. | defaults to undefined|
| **type** | [**&#39;all&#39; | &#39;dns&#39; | &#39;whois&#39; | &#39;ssl&#39; | &#39;ip&#39; | &#39;content&#39; | &#39;technology&#39;**]**Array<&#39;all&#39; &#124; &#39;dns&#39; &#124; &#39;whois&#39; &#124; &#39;ssl&#39; &#124; &#39;ip&#39; &#124; &#39;content&#39; &#124; &#39;technology&#39;>** | Type of changes to retrieve. | (optional) defaults to undefined|
| **since** | [**string**] | ISO 8601 timestamp to retrieve changes from. Omit to get all changes. | (optional) defaults to undefined|


### Return type

void (empty response body)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
|**400** | Invalid change type or date format. |  -  |
|**200** | Successfully retrieved change history. |  -  |
|**404** | No changes found for the specified target. |  -  |
|**401** | Authentication failed. Missing or invalid API key. |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **getJob**
> Job getJob()

<p>Retrieves the current status and results of an asynchronous job. Poll this endpoint to check job progress.</p> <h4>Polling Recommendations:</h4> <ul>     <li>For fast jobs (e.g., similar domains), poll every 1-2 seconds.</li>     <li>For slow jobs (e.g., WHOIS search, screenshots), poll every 5-10 seconds.</li>     <li>Implement an exponential backoff strategy for very long-running jobs.</li>     <li>Stop polling when the status is `COMPLETED`, `FAILED`, or `CANCELLED`.</li> </ul> <h4>Job Statuses:</h4> <ul>     <li><b>PENDING:</b> Job is queued and waiting to start.</li>     <li><b>PROCESSING:</b> Job is actively being processed.</li>     <li><b>COMPLETED:</b> Job finished successfully, results are available.</li>     <li><b>FAILED:</b> Job failed with an error.</li>     <li><b>CANCELLED:</b> Job was cancelled by user or system.</li> </ul> 

### Example

```typescript
import {
    OperationsApi,
    Configuration
} from '@whisper-security/whisper-api-sdk';

const configuration = new Configuration();
const apiInstance = new OperationsApi(configuration);

let jobId: string; //The unique ID of the job, returned from a `POST` operation. (default to undefined)

const { status, data } = await apiInstance.getJob(
    jobId
);
```

### Parameters

|Name | Type | Description  | Notes|
|------------- | ------------- | ------------- | -------------|
| **jobId** | [**string**] | The unique ID of the job, returned from a &#x60;POST&#x60; operation. | defaults to undefined|


### Return type

**Job**

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
|**404** | Job ID not found. |  -  |
|**200** | Job status and results retrieved successfully. |  -  |
|**401** | Authentication failed. Missing or invalid API key. |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **getMonitoringStatus**
> getMonitoringStatus()

<p>Retrieves current monitoring configuration and historical metrics for a domain or IP address.</p> <h4>Status Information:</h4> <ul>     <li><b>Monitoring State:</b> Active, paused, or not monitored</li>     <li><b>Check Frequency:</b> How often checks are performed</li>     <li><b>Active Alerts:</b> Currently triggered alert conditions</li>     <li><b>Last Check:</b> Timestamp of most recent check</li> </ul> <h4>Metrics Included:</h4> <ul>     <li>Uptime percentage (last 30 days)</li>     <li>Average response time</li>     <li>SSL certificate expiration countdown</li>     <li>DNS change events</li>     <li>WHOIS change events</li> </ul> 

### Example

```typescript
import {
    OperationsApi,
    Configuration
} from '@whisper-security/whisper-api-sdk';

const configuration = new Configuration();
const apiInstance = new OperationsApi(configuration);

let target: string; //The domain or IP address to check monitoring status for. (default to undefined)

const { status, data } = await apiInstance.getMonitoringStatus(
    target
);
```

### Parameters

|Name | Type | Description  | Notes|
|------------- | ------------- | ------------- | -------------|
| **target** | [**string**] | The domain or IP address to check monitoring status for. | defaults to undefined|


### Return type

void (empty response body)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
|**404** | Target is not being monitored. |  -  |
|**200** | Successfully retrieved monitoring status. |  -  |
|**401** | Authentication failed. Missing or invalid API key. |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **getScreenshotHistory**
> getScreenshotHistory()

<p>Retrieve all previously captured screenshots for a specific URL, ordered by capture time (newest first). Includes download URLs and metadata for each capture.</p> <h4>Response Includes:</h4> <ul>     <li><b>Download URL:</b> Direct link to screenshot image</li>     <li><b>Capture Time:</b> Timestamp when screenshot was taken</li>     <li><b>Dimensions:</b> Image width and height</li>     <li><b>Format:</b> Image format (PNG, JPEG, WebP)</li>     <li><b>File Size:</b> Size in bytes</li> </ul> <h4>Use Cases:</h4> <ul>     <li>Review website evolution over time</li>     <li>Compare screenshots for change detection</li>     <li>Download historical screenshots for reporting</li> </ul> 

### Example

```typescript
import {
    OperationsApi,
    Configuration
} from '@whisper-security/whisper-api-sdk';

const configuration = new Configuration();
const apiInstance = new OperationsApi(configuration);

let url: string; //The URL to retrieve screenshot history for. (default to undefined)
let limit: number; //Maximum number of screenshots to return. (optional) (default to 10)

const { status, data } = await apiInstance.getScreenshotHistory(
    url,
    limit
);
```

### Parameters

|Name | Type | Description  | Notes|
|------------- | ------------- | ------------- | -------------|
| **url** | [**string**] | The URL to retrieve screenshot history for. | defaults to undefined|
| **limit** | [**number**] | Maximum number of screenshots to return. | (optional) defaults to 10|


### Return type

void (empty response body)

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
|**404** | No screenshots found for the specified URL. |  -  |
|**200** | Successfully retrieved screenshot history. |  -  |
|**401** | Authentication failed. Missing or invalid API key. |  -  |
|**400** | Invalid URL parameter. |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **scheduleScreenshot**
> JobResponse scheduleScreenshot(screenshotRequest)

<p>Create a recurring job to capture website screenshots at regular intervals. Essential for monitoring website changes, detecting defacements, and tracking competitor updates.</p> <h4>Schedule Options:</h4> <ul>     <li><b>Cron Expression:</b> Full cron syntax support (e.g., `0 0 * * * *` = hourly)</li>     <li><b>Frequency Presets:</b> hourly, daily, weekly, monthly</li>     <li><b>Timezone:</b> Specify timezone for accurate scheduling</li>     <li><b>Retention:</b> Auto-cleanup old screenshots (default: keep last 30)</li> </ul> <h4>Performance:</h4> <ul>     <li><b>Setup Time:</b> ~2 seconds to create schedule</li>     <li><b>Screenshot Time:</b> 10-30 seconds per capture</li> </ul> <h4>Use Cases:</h4> <ul>     <li>Automated defacement detection</li>     <li>Compliance monitoring and archival</li>     <li>Competitor website tracking</li>     <li>Visual regression testing</li> </ul> 

### Example

```typescript
import {
    OperationsApi,
    Configuration,
    ScreenshotRequest
} from '@whisper-security/whisper-api-sdk';

const configuration = new Configuration();
const apiInstance = new OperationsApi(configuration);

let screenshotRequest: ScreenshotRequest; //Schedule configuration including URL, schedule timing, and screenshot options.

const { status, data } = await apiInstance.scheduleScreenshot(
    screenshotRequest
);
```

### Parameters

|Name | Type | Description  | Notes|
|------------- | ------------- | ------------- | -------------|
| **screenshotRequest** | **ScreenshotRequest**| Schedule configuration including URL, schedule timing, and screenshot options. | |


### Return type

**JobResponse**

### Authorization

[bearerAuth](../README.md#bearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
|**400** | Invalid schedule configuration or missing required fields. |  -  |
|**202** | Schedule successfully created. Poll &#x60;/v1/ops/jobs/{jobId}&#x60; for status. |  -  |
|**401** | Authentication failed. Missing or invalid API key. |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

