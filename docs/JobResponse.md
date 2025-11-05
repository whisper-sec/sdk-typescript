# JobResponse

Response returned when an asynchronous job is created. Contains the job ID and status URL for polling.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**jobId** | **string** | Unique identifier for the job. Use this ID to poll for job status and results. | [default to undefined]
**status** | **string** | Current status of the job | [default to undefined]
**statusUrl** | **string** | URL endpoint to poll for job status and results. Typically &#x60;/v1/ops/jobs/{jobId}&#x60;. | [default to undefined]
**message** | **string** | Human-readable message describing the job acceptance or current state | [optional] [default to undefined]

## Example

```typescript
import { JobResponse } from '@whisper-security/whisper-api-sdk';

const instance: JobResponse = {
    jobId,
    status,
    statusUrl,
    message,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
