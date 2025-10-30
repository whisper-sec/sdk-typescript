# MetadataInfo

Response metadata including data sources and any errors encountered

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**data_sources** | **Array&lt;string&gt;** | List of data sources used to build this response | [optional] [default to undefined]
**errors** | **Array&lt;string&gt;** | Any non-fatal errors encountered during data collection. Empty if all sources succeeded. | [optional] [default to undefined]

## Example

```typescript
import { MetadataInfo } from '@whisper-security/whisper-api-sdk';

const instance: MetadataInfo = {
    data_sources,
    errors,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
