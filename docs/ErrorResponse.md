# ErrorResponse


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**error** | **string** | Error code for programmatic handling | [default to undefined]
**message** | **string** | Human-readable error message | [default to undefined]
**timestamp** | **string** | Timestamp when the error occurred | [default to undefined]
**path** | **string** | Request path that caused the error | [optional] [default to undefined]

## Example

```typescript
import { ErrorResponse } from './api';

const instance: ErrorResponse = {
    error,
    message,
    timestamp,
    path,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
