# BulkRequest

Request payload for bulk enrichment of multiple IP addresses and domains

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**indicators** | **Array&lt;string&gt;** | List of indicators (IP addresses or domains) to enrich. Mix of IPs and domains is supported. | [default to undefined]
**include** | **Set&lt;string&gt;** | Additional data modules to include for each indicator. Same options as single indicator endpoint. | [optional] [default to undefined]
**_options** | [**BulkOptions**](BulkOptions.md) |  | [optional] [default to undefined]

## Example

```typescript
import { BulkRequest } from '@whisper-security/whisper-api-sdk';

const instance: BulkRequest = {
    indicators,
    include,
    _options,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
