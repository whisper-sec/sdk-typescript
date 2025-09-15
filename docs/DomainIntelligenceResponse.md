# DomainIntelligenceResponse

Comprehensive domain intelligence response containing registration, DNS, relationships, and IP data

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**query** | [**DomainIntelligenceResponseQuery**](DomainIntelligenceResponseQuery.md) |  | [optional] [default to undefined]
**summary** | [**DomainIntelligenceResponseSummary**](DomainIntelligenceResponseSummary.md) |  | [optional] [default to undefined]
**registration** | **object** | WHOIS registration details | [optional] [default to undefined]
**dns** | **object** | DNS records (A, AAAA, MX, NS, TXT, etc.) | [optional] [default to undefined]
**relationships** | **object** | Related domains and infrastructure | [optional] [default to undefined]
**trademark** | **object** | Trademark information | [optional] [default to undefined]
**ip_intelligence** | **object** | Intelligence for resolved IP addresses | [optional] [default to undefined]
**metadata** | **object** | Response metadata and data sources | [optional] [default to undefined]

## Example

```typescript
import { DomainIntelligenceResponse } from './api';

const instance: DomainIntelligenceResponse = {
    query,
    summary,
    registration,
    dns,
    relationships,
    trademark,
    ip_intelligence,
    metadata,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
