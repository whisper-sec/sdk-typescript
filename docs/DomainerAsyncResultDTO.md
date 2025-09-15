# DomainerAsyncResultDTO

Results and status information for an asynchronous domain search request (similarity or free-text)

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**requestId** | **string** | Unique identifier for the request | [readonly] [default to undefined]
**domainName** | **string** | Domain name that was searched | [optional] [readonly] [default to undefined]
**similarityType** | [**DomainerSimilarityType**](DomainerSimilarityType.md) |  | [optional] [default to undefined]
**queryString** | **string** | Query string used for the search (only for SEARCH requests) | [optional] [readonly] [default to undefined]
**operator** | **string** | Default operator used between query terms (only for SEARCH requests) | [optional] [readonly] [default to undefined]
**level** | **string** | Absolute domain level filter applied (only for SEARCH requests) | [optional] [readonly] [default to undefined]
**limit** | **number** | Maximum number of results requested | [readonly] [default to undefined]
**createdAt** | **string** | Time when the request was created | [readonly] [default to undefined]
**completedAt** | **string** | Time when the request was completed (null if still processing) | [optional] [readonly] [default to undefined]
**status** | **string** | Request status | [readonly] [default to undefined]
**results** | **Array&lt;string&gt;** | List of similar domains found (null if still processing) | [optional] [readonly] [default to undefined]
**resultCount** | **number** | Total number of results found | [optional] [readonly] [default to undefined]
**processingTimeMs** | **number** | Time taken to process the request in milliseconds (-1 if still processing) | [optional] [readonly] [default to undefined]

## Example

```typescript
import { DomainerAsyncResultDTO } from './api';

const instance: DomainerAsyncResultDTO = {
    requestId,
    domainName,
    similarityType,
    queryString,
    operator,
    level,
    limit,
    createdAt,
    completedAt,
    status,
    results,
    resultCount,
    processingTimeMs,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
