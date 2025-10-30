# DnsEnumConfig

Configuration for DNS enumeration and subdomain discovery

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**subdomain_enum** | **boolean** | Enable subdomain enumeration | [optional] [default to true]
**zone_transfer** | **boolean** | Enable DNS zone transfer attempts | [optional] [default to false]
**reverse_dns** | **boolean** | Enable reverse DNS lookups | [optional] [default to true]
**wordlist_size** | **string** | Wordlist size for subdomain brute-forcing | [optional] [default to WordlistSizeEnum_Medium]

## Example

```typescript
import { DnsEnumConfig } from '@whisper-security/whisper-api-sdk';

const instance: DnsEnumConfig = {
    subdomain_enum,
    zone_transfer,
    reverse_dns,
    wordlist_size,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
