# SimilarDomainsOpsRequest

Request for generating similar/lookalike domains for brand protection

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**domain** | **string** | The target domain to generate variations for | [default to undefined]
**_options** | [**SimilarDomainRequest**](SimilarDomainRequest.md) |  | [optional] [default to undefined]

## Example

```typescript
import { SimilarDomainsOpsRequest } from '@whisper-security/whisper-api-sdk';

const instance: SimilarDomainsOpsRequest = {
    domain,
    _options,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
