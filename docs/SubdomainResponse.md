# SubdomainResponse

Response containing discovered subdomains and related metadata

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**domain** | **string** | The root domain that was queried | [default to undefined]
**total_count** | **number** | Total number of subdomains discovered | [default to undefined]
**subdomains** | [**Array&lt;SubdomainInfo&gt;**](SubdomainInfo.md) | List of discovered subdomains | [default to undefined]
**timestamp** | **string** | Timestamp of when the data was retrieved | [default to undefined]
**sources** | **Array&lt;string&gt;** | Data sources used for subdomain discovery | [optional] [default to undefined]

## Example

```typescript
import { SubdomainResponse } from '@whisper-security/whisper-api-sdk';

const instance: SubdomainResponse = {
    domain,
    total_count,
    subdomains,
    timestamp,
    sources,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
