# ErrorResponse

Standard error response returned when an API request fails

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**status** | **number** | The HTTP status code of the error | [default to undefined]
**error** | **string** | A short, machine-readable error code | [default to undefined]
**message** | **string** | A human-readable error message providing more detail | [default to undefined]
**details** | **object** | Additional details about the error, including field-specific validation errors | [optional] [default to undefined]
**timestamp** | **string** | The timestamp when the error occurred | [default to undefined]
**trace_id** | **string** | A unique trace ID for this request, useful for debugging | [optional] [default to undefined]
**path** | **string** | The API path that generated this error | [optional] [default to undefined]

## Example

```typescript
import { ErrorResponse } from '@whisper-security/whisper-api-sdk';

const instance: ErrorResponse = {
    status,
    error,
    message,
    details,
    timestamp,
    trace_id,
    path,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
