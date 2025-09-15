# DomainIntelligenceResponseSummary


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**domain_name** | **string** | Domain name | [optional] [default to undefined]
**registrar** | **string** | Domain registrar | [optional] [default to undefined]
**registration_date** | **string** | Registration date | [optional] [default to undefined]
**expiration_date** | **string** | Expiration date | [optional] [default to undefined]
**status** | **string** | Domain status | [optional] [default to undefined]
**has_trademark** | **boolean** | Trademark status | [optional] [default to undefined]
**dns_provider** | **string** | Primary DNS provider | [optional] [default to undefined]
**total_links_in** | **number** | Incoming links | [optional] [default to undefined]
**total_links_out** | **number** | Outgoing links | [optional] [default to undefined]

## Example

```typescript
import { DomainIntelligenceResponseSummary } from './api';

const instance: DomainIntelligenceResponseSummary = {
    domain_name,
    registrar,
    registration_date,
    expiration_date,
    status,
    has_trademark,
    dns_provider,
    total_links_in,
    total_links_out,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
