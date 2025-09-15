# IpIntelligenceResponseSummary

Executive summary of IP intelligence

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**organization** | **string** | Organization name | [optional] [default to undefined]
**location** | **string** | Geographic location | [optional] [default to undefined]
**network** | **string** | Network prefix | [optional] [default to undefined]
**asn_primary** | **string** | Primary ASN | [optional] [default to undefined]
**risk_score** | **number** | Risk score (0-1) | [optional] [default to undefined]
**ip_type** | **string** | IP type classification | [optional] [default to undefined]
**total_domains** | **number** | Number of associated domains | [optional] [default to undefined]
**total_dns_records** | **number** | Number of DNS records | [optional] [default to undefined]

## Example

```typescript
import { IpIntelligenceResponseSummary } from './api';

const instance: IpIntelligenceResponseSummary = {
    organization,
    location,
    network,
    asn_primary,
    risk_score,
    ip_type,
    total_domains,
    total_dns_records,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
