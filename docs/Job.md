# Job


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** |  | [optional] [default to undefined]
**status** | **string** |  | [optional] [default to undefined]
**type** | **string** |  | [optional] [default to undefined]
**params** | **object** |  | [optional] [default to undefined]
**result** | **object** |  | [optional] [default to undefined]
**error** | [**JobError**](JobError.md) |  | [optional] [default to undefined]
**progress** | [**JobProgress**](JobProgress.md) |  | [optional] [default to undefined]
**createdAt** | **string** |  | [optional] [default to undefined]
**updatedAt** | **string** |  | [optional] [default to undefined]
**completedAt** | **string** |  | [optional] [default to undefined]
**metadata** | **{ [key: string]: string; }** |  | [optional] [default to undefined]
**username** | **string** |  | [optional] [default to undefined]

## Example

```typescript
import { Job } from '@whisper-security/whisper-api-sdk';

const instance: Job = {
    id,
    status,
    type,
    params,
    result,
    error,
    progress,
    createdAt,
    updatedAt,
    completedAt,
    metadata,
    username,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
