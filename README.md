# Whisper API SDK - Node.js

[![CI/CD](https://github.com/whisper-sec/sdk-typescript/actions/workflows/ci.yml/badge.svg)](https://github.com/whisper-sec/sdk-typescript/actions/workflows/ci.yml)
[![Publish](https://github.com/whisper-sec/sdk-typescript/actions/workflows/publish.yml/badge.svg)](https://github.com/whisper-sec/sdk-typescript/actions/workflows/publish.yml)
[![npm version](https://badge.fury.io/js/@whisper-security%2Fwhisper-api-sdk.svg)](https://badge.fury.io/js/@whisper-security%2Fwhisper-api-sdk)
[![npm downloads](https://img.shields.io/npm/dm/@whisper-security/whisper-api-sdk.svg)](https://www.npmjs.com/package/@whisper-security/whisper-api-sdk)
[![TypeScript](https://img.shields.io/badge/TypeScript-Ready-blue.svg)](https://www.typescriptlang.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)

## Whisper API v1 - TypeScript/JavaScript SDK

**The Foundational Intelligence Layer for the Internet**

The Whisper API provides comprehensive, real-time intelligence on any internet asset. By connecting billions of data points across live internet routing, historical registration records, and deep resolution data, our API moves beyond simple enrichment to deliver predictive, context-rich insights.

This TypeScript/JavaScript SDK provides a fully-typed, Promise-based client for the Whisper API v1, designed for both Node.js and browser environments.

---

## 🚀 Quick Start

### 1. Installation

```bash
npm install @whisper-security/whisper-api-sdk
# or
yarn add @whisper-security/whisper-api-sdk
```

### 2. Get Your API Key

Sign up at [dash.whisper.security](https://dash.whisper.security) to get your API key.

### 3. Make Your First Request

**TypeScript:**
```typescript
import { Configuration, IndicatorsApi } from '@whisper-security/whisper-api-sdk';

// Configure Bearer token authentication
const configuration = new Configuration({
  basePath: 'https://api.whisper.security',
  accessToken: 'YOUR_API_KEY'  // Replace with your actual API key
});

const api = new IndicatorsApi(configuration);

// Enrich an IP address
async function enrichIp() {
  try {
    const response = await api.getIndicator('ip', '8.8.8.8');
    console.log(`Organization: ${response.data.summary?.organization}`);
    console.log(`Location: ${response.data.summary?.location}`);
    console.log(`Risk Score: ${response.data.reputation?.risk_score}`);
  } catch (error) {
    console.error('API Error:', error);
  }
}

enrichIp();
```

**JavaScript (CommonJS):**
```javascript
const { Configuration, IndicatorsApi } = require('@whisper-security/whisper-api-sdk');

const configuration = new Configuration({
  basePath: 'https://api.whisper.security',
  accessToken: 'YOUR_API_KEY'
});

const api = new IndicatorsApi(configuration);

api.getIndicator('ip', '8.8.8.8')
  .then(response => {
    console.log(`Organization: ${response.data.summary?.organization}`);
  })
  .catch(error => {
    console.error('API Error:', error);
  });
```

---

## 🎯 Key Features

- **Unified & Simple**: Small set of powerful, resource-oriented endpoints
- **Performant by Design**: Asynchronous-first with strategic caching (<500ms typical response)
- **Workflow-Oriented**: Built for real-world security operations, not just data dumps
- **Comprehensive**: IP, Domain, DNS, WHOIS, Routing, Geolocation, Screenshots, Monitoring
- **Fully Typed**: Complete TypeScript definitions for IDE autocomplete
- **Promise-Based**: Modern async/await support
- **Universal**: Works in Node.js and browsers

---

## ⚡ Performance Targets

| Endpoint Type | Response Time | Use Case |
|---------------|---------------|----------|
| Geolocation | <150ms | Real-time fraud detection |
| Single Indicator | <500ms | Incident response enrichment |
| With Routing Data | <2s (cached: 200ms) | Deep network analysis |
| Bulk Operations | 5-30s | Batch log enrichment |
| Search/Discovery | 10-60s | Threat hunting |

---

## 📋 Common Use Cases

### IP Address Enrichment
```typescript
// The include parameter accepts a single value
const ipData = await api.getIndicator('ip', '8.8.8.8', 'routing');
// Available values: 'routing', 'rpki', 'whois', 'dns_details', 'ip_intelligence'
```

### Domain Analysis
```typescript
// Request WHOIS data for a domain
const domainData = await api.getIndicator('domain', 'example.com', 'whois');
// Available values: 'whois', 'dns_details', 'ip_intelligence'
```

### Bulk Lookups (Asynchronous)
```typescript
import { OperationsApi, BulkRequest, BulkRequestIncludeEnum } from '@whisper-security/whisper-api-sdk';

const opsApi = new OperationsApi(configuration);

const bulkRequest: BulkRequest = {
  indicators: ['8.8.8.8', 'example.com'],
  include: new Set([
    BulkRequestIncludeEnum.Routing,
    BulkRequestIncludeEnum.Whois
  ])
};

const jobResponse = await api.bulkEnrichment(bulkRequest);
console.log(`Job ID: ${jobResponse.data.job_id}`);

// Poll for results
const result = await opsApi.getJob(jobResponse.data.job_id);
```

### Geolocation Lookup

> **Note:** The LocationApi currently has incomplete TypeScript type definitions. The API returns data, but TypeScript types show `void`. Full type support is coming soon.

```typescript
import { LocationApi } from '@whisper-security/whisper-api-sdk';

const locationApi = new LocationApi(configuration);
// TypeScript types show void, but API returns location data
const location = await locationApi.getIpLocation('8.8.8.8');
// In practice, you may access properties like:
// console.log(`Country: ${location.data?.country}`);
// console.log(`City: ${location.data?.city}`);
```

---

## 📝 Include Parameters Reference

When enriching indicators, you can request additional data modules using the `include` parameter.

### Single Indicator Enrichment

The `getIndicator()` method accepts a single include value as a string:

```typescript
// Valid single values:
await api.getIndicator('ip', '8.8.8.8', 'routing')        // BGP routing information
await api.getIndicator('ip', '8.8.8.8', 'rpki')           // RPKI validation status
await api.getIndicator('ip', '8.8.8.8', 'whois')          // WHOIS registration data
await api.getIndicator('ip', '8.8.8.8', 'dns_details')    // Detailed DNS records
await api.getIndicator('ip', '8.8.8.8', 'ip_intelligence') // IP intelligence and reputation
```

**Available String Values:**
- `'routing'` - BGP routing information
- `'rpki'` - RPKI validation status
- `'whois'` - WHOIS registration data
- `'dns_details'` - Detailed DNS records
- `'ip_intelligence'` - IP intelligence and reputation

### Bulk Enrichment

The bulk enrichment API accepts multiple include values using a `Set` with enum values:

```typescript
import { BulkRequest, BulkRequestIncludeEnum } from '@whisper-security/whisper-api-sdk';

const bulkRequest: BulkRequest = {
  indicators: ['8.8.8.8', 'example.com'],
  include: new Set([
    BulkRequestIncludeEnum.Routing,       // 'routing'
    BulkRequestIncludeEnum.Rpki,          // 'rpki'
    BulkRequestIncludeEnum.Whois,         // 'whois'
    BulkRequestIncludeEnum.DnsDetails,    // 'dns_details'
    BulkRequestIncludeEnum.IpIntelligence // 'ip_intelligence'
  ])
};
```

**Available Enum Values:**
- `BulkRequestIncludeEnum.Routing` - BGP routing information
- `BulkRequestIncludeEnum.Rpki` - RPKI validation status
- `BulkRequestIncludeEnum.Whois` - WHOIS registration data
- `BulkRequestIncludeEnum.DnsDetails` - Detailed DNS records
- `BulkRequestIncludeEnum.IpIntelligence` - IP intelligence and reputation

---

## 🔐 Authentication

All API endpoints require Bearer token authentication. Set your API key when creating the Configuration:

```typescript
const configuration = new Configuration({
  basePath: 'https://api.whisper.security',
  accessToken: 'YOUR_API_KEY'
});
```

### Using Environment Variables

```typescript
const configuration = new Configuration({
  basePath: 'https://api.whisper.security',
  accessToken: process.env.WHISPER_API_KEY
});
```

### Custom Headers

```typescript
const configuration = new Configuration({
  basePath: 'https://api.whisper.security',
  accessToken: 'YOUR_API_KEY',
  baseOptions: {
    headers: {
      'User-Agent': 'MyApp/1.0'
    }
  }
});
```

---

## 🌐 Browser Usage

The SDK works in browsers with some configuration:

```html
<script type="module">
  import { Configuration, IndicatorsApi } from './node_modules/@whisper-security/whisper-api-sdk/dist/index.js';

  const config = new Configuration({
    basePath: 'https://api.whisper.security',
    accessToken: 'YOUR_API_KEY'
  });

  const api = new IndicatorsApi(config);

  api.getIndicator('ip', '8.8.8.8')
    .then(response => console.log(response.data));
</script>
```

**Note**: Never expose your API key in client-side code. Use a backend proxy for production applications.

---

## 📚 SDK Documentation

### Package Structure

```
@whisper-security/whisper-api-sdk/
├── api/
│   ├── indicators-api.ts      # Indicator enrichment endpoints
│   ├── location-api.ts         # Geolocation endpoints
│   └── operations-api.ts       # Async job management
├── models/                     # TypeScript interfaces and types
├── configuration.ts            # SDK configuration
├── base.ts                     # Base API functionality
└── index.ts                    # Main exports
```

### API Classes

The SDK provides three main API classes with full TypeScript support:

#### IndicatorsApi
Comprehensive indicator enrichment for IPs and domains.

**Methods:**
- `getIndicator(type, value, include?)` - Enrich a single indicator
- `getIndicatorHistory(type, value, limit?)` - Get historical data
- `getIndicatorGraph(type, value)` - Get relationship graph
- `getSubdomains(domain, limit?)` - Get domain subdomains
- `generateSimilarDomainsGet(domain, type?, limit?)` - Generate similar domains (GET)
- `generateSimilarDomainsPost(domain, similarDomainsRequest)` - Generate similar domains (POST)
- `bulkEnrichment(bulkRequest)` - Bulk enrichment (async job)
- `searchIndicators(searchRequest)` - Search indicators (async job)

**Example:**
```typescript
import { IndicatorsApi } from '@whisper-security/whisper-api-sdk';

const api = new IndicatorsApi(configuration);
const response = await api.getIndicator('ip', '8.8.8.8', 'routing');
console.log(response.data);
```

[View Full IndicatorsApi Documentation](docs/IndicatorsApi.md)

#### LocationApi
Geolocation lookups and searches.

**Methods:**
- `getIpLocation(ip)` - Get IP geolocation
- `searchLocation(field, value, limit?)` - Search by location attributes

**Example:**
```typescript
import { LocationApi } from '@whisper-security/whisper-api-sdk';

const api = new LocationApi(configuration);
const location = await api.getIpLocation('8.8.8.8');
console.log(`Country: ${location.data.country}, City: ${location.data.city}`);
```

[View Full LocationApi Documentation](docs/LocationApi.md)

#### OperationsApi
Manage asynchronous jobs and operations.

**Methods:**
- `getJob(jobId)` - Get job status and results
- `listJobs(status?, limit?)` - List user jobs
- `createScreenshot(screenshotRequest)` - Capture screenshot (async job)
- `createScan(infraScanRequest)` - Infrastructure scan (async job)

**Example:**
```typescript
import { OperationsApi } from '@whisper-security/whisper-api-sdk';

const api = new OperationsApi(configuration);
const job = await api.getJob('job-uuid-here');
console.log(`Status: ${job.data.status}, Progress: ${job.data.progress}`);
```

[View Full OperationsApi Documentation](docs/OperationsApi.md)

---

## 📦 Data Models & Types

The SDK includes comprehensive TypeScript interfaces for all API responses and requests with:
- Full TypeScript type definitions
- IDE autocomplete support
- Compile-time type checking
- JSDoc documentation

### Core Response Types

#### IndicatorResponse
Comprehensive intelligence for an IP or domain.

**Properties:**
- `query` (QueryInfo) - Query metadata
- `summary` (SummaryInfo) - Quick summary
- `geolocation` (object) - Geographic data
- `network` (object) - Network information
- `isp` (object) - ISP details
- `registration` (object) - WHOIS registration
- `dns` (DnsInfo) - DNS records
- `relationships` (RelationshipInfo) - Related infrastructure
- `reputation` (ReputationInfo) - Risk and reputation scores
- `security` (object) - Security context
- `metadata` (MetadataInfo) - Response metadata

[View Full Type Documentation](docs/IndicatorResponse.md)

#### LocationResponse
Geolocation data for an IP address.

**Properties:**
- `ip` (string) - IP address
- `country` (string) - Country name
- `countryCode` (string) - ISO country code
- `city` (string) - City name
- `latitude` (number) - Latitude
- `longitude` (number) - Longitude
- `timezone` (string) - Timezone
- `isp` (string) - ISP name
- `asn` (number) - Autonomous System Number

[View Full Type Documentation](docs/LocationResponse.md)

#### JobResponse vs Job

The API uses two different job-related types:

**JobResponse** - Returned from POST operations (job submission):
- `job_id` (string) - Unique job identifier
- `status` (string) - Initial job status
- `status_url` (string) - URL to poll for status
- `message` (string) - Status message

**Job** - Returned from GET /v1/ops/jobs/{jobId} (job polling):
- `id` (string) - Job identifier (note: `id` not `job_id`)
- `status` (string) - Current status (PENDING, PROCESSING, COMPLETED, FAILED)
- `progress` (JobProgress) - Progress information with `percentage`, `current`, `total`
- `result` (any) - Job results (when completed)
- `error` (JobError) - Error details (when failed)
- `createdAt` (string) - Creation timestamp (camelCase)
- `updatedAt` (string) - Last update timestamp (camelCase)
- `completedAt` (string) - Completion timestamp (camelCase)

[View Full Type Documentation](docs/JobResponse.md) | [View Job Type](docs/Job.md)

### Request Types

#### BulkRequest
Request for bulk indicator enrichment.

**Properties:**
- `indicators` (string[]) - List of IPs/domains (max 100)
- `include` (string[]) - Data modules to include
- `options` (BulkOptions) - Processing options

[View Full Type Documentation](docs/BulkRequest.md)

#### SearchRequest
Request for indicator search.

**Properties:**
- `query` (string) - Search query
- `field` (string) - Field to search (registrantName, registrarName, etc.)
- `limit` (number) - Maximum results (default: 100)

[View Full Type Documentation](docs/SearchRequest.md)

#### ScreenshotRequest
Request for website screenshot.

**Properties:**
- `url` (string) - Target URL
- `options` (ScreenshotOptions) - Capture options (fullPage, format, etc.)

[View Full Type Documentation](docs/ScreenshotRequest.md)

#### InfraScanRequest
Request for infrastructure scanning.

**Properties:**
- `domain` (string) - Target domain
- `type` (string) - Scan type (subdomains, ports, dns)
- `config` (object) - Type-specific configuration

[View Full Type Documentation](docs/InfraScanRequest.md)

### Complete Type Reference

For a complete list of all TypeScript interfaces and types, see:

**Core Types:**
- [IndicatorResponse](docs/IndicatorResponse.md) - Main enrichment response
- [LocationResponse](docs/LocationResponse.md) - Geolocation data
- [JobResponse](docs/JobResponse.md) - Async job status
- [HistoryResponse](docs/HistoryResponse.md) - Historical data

**Request Types:**
- [BulkRequest](docs/BulkRequest.md) - Bulk enrichment
- [SearchRequest](docs/SearchRequest.md) - Search parameters
- [ScreenshotRequest](docs/ScreenshotRequest.md) - Screenshot options
- [InfraScanRequest](docs/InfraScanRequest.md) - Scan configuration
- [SimilarDomainsRequest](docs/SimilarDomainsRequest.md) - Similar domain generation

**Nested Types:**
- [QueryInfo](docs/QueryInfo.md) - Query metadata
- [SummaryInfo](docs/SummaryInfo.md) - Quick summary
- [DnsInfo](docs/DnsInfo.md) - DNS records
- [RelationshipInfo](docs/RelationshipInfo.md) - Infrastructure relationships
- [ReputationInfo](docs/ReputationInfo.md) - Reputation scores
- [MetadataInfo](docs/MetadataInfo.md) - Response metadata
- [JobProgress](docs/JobProgress.md) - Job progress details
- [JobError](docs/JobError.md) - Job error information

**Configuration Types:**
- [BulkOptions](docs/BulkOptions.md) - Bulk processing options
- [ScreenshotOptions](docs/ScreenshotOptions.md) - Screenshot settings
- [DnsEnumConfig](docs/DnsEnumConfig.md) - DNS enumeration config
- [PortScanConfig](docs/PortScanConfig.md) - Port scanning config
- [SubdomainEnumConfig](docs/SubdomainEnumConfig.md) - Subdomain enumeration config

**Security Types:**
- [BlacklistScores](docs/BlacklistScores.md) - Blacklist check results
- [DomainReputationScores](docs/DomainReputationScores.md) - Domain reputation
- [DomainReputationDetails](docs/DomainReputationDetails.md) - Detailed reputation data

**View All Types:** See the [docs/](docs/) directory for complete type documentation.

---

## 🔧 Advanced Usage

### Error Handling

```typescript
import { IndicatorsApi } from '@whisper-security/whisper-api-sdk';
import { AxiosError } from 'axios';

const api = new IndicatorsApi(configuration);

try {
  const response = await api.getIndicator('ip', '8.8.8.8');
  console.log(response.data);
} catch (error) {
  const axiosError = error as AxiosError;
  if (axiosError.response) {
    console.error('Status:', axiosError.response.status);
    console.error('Error:', axiosError.response.data);
  }
}
```

### Custom Configuration

```typescript
import { Configuration } from '@whisper-security/whisper-api-sdk';
import axios from 'axios';

const configuration = new Configuration({
  basePath: 'https://api.whisper.security',
  accessToken: process.env.WHISPER_API_KEY,
  baseOptions: {
    timeout: 60000,
    headers: {
      'User-Agent': 'MyApp/1.0'
    }
  }
});
```

### Working with Async Jobs

> **Note:** The API uses two different job types:
> - `JobResponse` - Returned from POST operations (has `job_id`, `status_url`)
> - `Job` - Returned from GET /v1/ops/jobs/{jobId} (has `progress`, `result`, full details)

```typescript
import {
  Configuration,
  IndicatorsApi,
  OperationsApi,
  BulkRequest,
  BulkRequestIncludeEnum,
  Job
} from '@whisper-security/whisper-api-sdk';

const indicatorsApi = new IndicatorsApi(configuration);
const opsApi = new OperationsApi(configuration);

// Submit bulk job
const bulkRequest: BulkRequest = {
  indicators: ['8.8.8.8', '1.1.1.1', 'example.com'],
  include: new Set([
    BulkRequestIncludeEnum.Routing,
    BulkRequestIncludeEnum.Whois
  ])
};

const jobResponse = await indicatorsApi.bulkEnrichment(bulkRequest);
console.log(`Job submitted: ${jobResponse.data.job_id}`);

// Poll for completion with progress tracking
async function pollJob(jobId: string, maxAttempts = 60): Promise<Job> {
  let attempt = 0;
  let delay = 1000; // Start with 1 second

  while (attempt < maxAttempts) {
    const response = await opsApi.getJob(jobId);
    const job = response.data as Job;

    console.log(`Attempt ${attempt + 1}: ${job.status}`);

    // Job type has progress property
    if (job.progress) {
      console.log(`Progress: ${job.progress.current}/${job.progress.total} (${job.progress.percentage}%)`);
      if (job.progress.message) {
        console.log(`Message: ${job.progress.message}`);
      }
    }

    if (job.status === 'COMPLETED') {
      console.log('Job completed successfully!');
      return job;
    }

    if (job.status === 'FAILED') {
      console.error('Job failed:', job.error);
      throw new Error(`Job failed: ${job.error?.message}`);
    }

    // Exponential backoff: 1s, 2s, 4s, 8s, max 10s
    await new Promise(resolve => setTimeout(resolve, delay));
    delay = Math.min(delay * 2, 10000);
    attempt++;
  }

  throw new Error('Job polling timeout');
}

// Execute and get results
const result = await pollJob(jobResponse.data.job_id!);
console.log('Job Results:', result.result);
```

### Type-Safe Response Handling

```typescript
import { IndicatorResponse, ReputationInfo } from '@whisper-security/whisper-api-sdk';

async function analyzeIndicator(ip: string): Promise<void> {
  const response = await api.getIndicator('ip', ip);
  const data: IndicatorResponse = response.data;

  // TypeScript provides full type checking
  if (data.reputation?.risk_score) {
    const risk: number = data.reputation.risk_score;
    if (risk > 50) {
      console.log(`High risk IP: ${ip}`);
    }
  }

  // Access nested properties with full autocomplete
  const country = data.geolocation?.country;
  const asn = data.network?.asn;
}
```

### Axios Interceptors

```typescript
import axios from 'axios';

// Add request interceptor for logging
axios.interceptors.request.use(request => {
  console.log('Starting Request:', request.url);
  return request;
});

// Add response interceptor for error handling
axios.interceptors.response.use(
  response => response,
  error => {
    console.error('API Error:', error.response?.data);
    return Promise.reject(error);
  }
);
```

---

## 📚 External Documentation

For detailed API documentation, visit:
- **Full Documentation**: [docs.whisper.security](https://docs.whisper.security)
- **API Reference**: [docs.whisper.security/api](https://docs.whisper.security/api)
- **Quick Start Guide**: [docs.whisper.security/quickstart](https://docs.whisper.security/quickstart)

---

## 📊 Rate Limits

| Category | Limit |
|----------|-------|
| Standard Enrichment | 100 req/min |
| Bulk Operations | 10 req/min |
| Search/Discovery | 5 req/min |
| Screenshots | 10 req/min |

Rate limits return HTTP 429. Retry after the time specified in the `Retry-After` header.

---

## 🆘 Support

- **Email**: api-support@whisper.security
- **Documentation**: https://docs.whisper.security
- **Issues**: https://github.com/whisper-sec/sdk-typescript/issues

---

## 📄 License

Proprietary - https://whisper.security/terms

---

*Generated with ❤️ by Whisper Security*
