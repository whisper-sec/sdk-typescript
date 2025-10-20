# BulkOptions

Advanced configuration options for bulk processing behavior

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**parallel_processing** | **boolean** | Enable parallel processing of indicators for faster results | [optional] [default to true]
**batch_size** | **number** | Number of indicators to process in each batch. Smaller batches &#x3D; more frequent progress updates | [optional] [default to 10]
**timeout_per_indicator** | **number** | Maximum time in milliseconds to wait for each indicator before timing out | [optional] [default to 5000]
**continue_on_error** | **boolean** | Continue processing remaining indicators if one fails. Recommended for large batches. | [optional] [default to true]
**include_failed** | **boolean** | Include failed indicators in the response with error details | [optional] [default to false]

## Example

```typescript
import { BulkOptions } from '@whisper-security/whisper-api-sdk';

const instance: BulkOptions = {
    parallel_processing,
    batch_size,
    timeout_per_indicator,
    continue_on_error,
    include_failed,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
