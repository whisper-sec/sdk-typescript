# DomainerAsyncResponseDTO

Response object for an asynchronous domain similarity search request submission

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**requestId** | **string** | Unique identifier for tracking the request | [readonly] [default to undefined]
**domainName** | **string** | Domain name being searched | [readonly] [default to undefined]
**queryString** | **string** | Query string submitted for free-text search (if applicable) | [optional] [readonly] [default to undefined]
**message** | **string** | Status message providing information about the request | [readonly] [default to undefined]
**statusUrl** | **string** | URL to check for results (can be polled to monitor progress and get results) | [readonly] [default to undefined]

## Example

```typescript
import { DomainerAsyncResponseDTO } from './api';

const instance: DomainerAsyncResponseDTO = {
    requestId,
    domainName,
    queryString,
    message,
    statusUrl,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
