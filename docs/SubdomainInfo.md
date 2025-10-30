# SubdomainInfo

Detailed information about a discovered subdomain

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**subdomain** | **string** | The full subdomain name | [default to undefined]
**ip_addresses** | **Array&lt;string&gt;** | IP addresses associated with the subdomain | [optional] [default to undefined]
**first_seen** | **string** | First time this subdomain was observed | [optional] [default to undefined]
**last_seen** | **string** | Last time this subdomain was observed | [optional] [default to undefined]
**record_type** | **string** | Type of subdomain record | [optional] [default to undefined]
**status** | **string** | Current status of the subdomain | [optional] [default to undefined]
**technologies** | **Array&lt;string&gt;** | Technology stack detected on this subdomain | [optional] [default to undefined]
**risk_score** | **number** | Risk score for this subdomain (0-100) | [optional] [default to undefined]

## Example

```typescript
import { SubdomainInfo } from '@whisper-security/whisper-api-sdk';

const instance: SubdomainInfo = {
    subdomain,
    ip_addresses,
    first_seen,
    last_seen,
    record_type,
    status,
    technologies,
    risk_score,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
