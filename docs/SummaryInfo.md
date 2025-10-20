# SummaryInfo

Executive summary with the most important facts for quick decision-making

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**organization** | **string** | Primary organization name | [optional] [default to undefined]
**location** | **string** | Primary location | [optional] [default to undefined]
**network** | **string** | Network range or CIDR | [optional] [default to undefined]
**registrar** | **string** | Domain registrar | [optional] [default to undefined]
**status** | **string** | Domain status | [optional] [default to undefined]
**asn_primary** | **string** | Primary ASN | [optional] [default to undefined]
**risk_score** | **number** | Composite risk score (0-10, higher is riskier) | [optional] [default to undefined]
**ip_type** | **string** | IP classification | [optional] [default to undefined]
**total_domains** | **number** | Total number of domains resolving to this IP | [optional] [default to undefined]
**domain_name** | **string** | The domain name | [optional] [default to undefined]
**registration_date** | **string** | Domain registration date | [optional] [default to undefined]
**expiration_date** | **string** | Domain expiration date | [optional] [default to undefined]
**dns_provider** | **string** | Primary DNS provider | [optional] [default to undefined]
**total_links_in** | **number** | Number of incoming links/backlinks | [optional] [default to undefined]
**total_links_out** | **number** | Number of outgoing links | [optional] [default to undefined]

## Example

```typescript
import { SummaryInfo } from '@whisper-security/whisper-api-sdk';

const instance: SummaryInfo = {
    organization,
    location,
    network,
    registrar,
    status,
    asn_primary,
    risk_score,
    ip_type,
    total_domains,
    domain_name,
    registration_date,
    expiration_date,
    dns_provider,
    total_links_in,
    total_links_out,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
