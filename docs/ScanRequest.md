# ScanRequest

Request for initiating a domain infrastructure scan

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**domain** | **string** | The target domain to scan | [default to undefined]
**type** | **string** | Type of scan to perform. Determines the depth and modules used in the scan. | [optional] [default to TypeEnum_Comprehensive]

## Example

```typescript
import { ScanRequest } from '@whisper-security/whisper-api-sdk';

const instance: ScanRequest = {
    domain,
    type,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
