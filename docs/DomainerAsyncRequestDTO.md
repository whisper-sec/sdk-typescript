# DomainerAsyncRequestDTO

Parameters for an asynchronous domain search (either similarity or free-text)

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**domainName** | **string** | (Required for SIMILARITY requests) Domain name to search for similar domains | [optional] [default to undefined]
**similarityType** | **string** | (Required for SIMILARITY requests) Type of similarity to use: CONTAINS, SOUNDING, PREFIX, SUFFIX, TYPO, UTFVARS | [optional] [default to undefined]
**queryString** | **string** | (Required for SEARCH requests) Query string (supports standard query syntax) | [optional] [default to undefined]
**operator** | **string** | (Optional for SEARCH requests) Default operator between query terms if not specified | [optional] [default to OperatorEnum_And]
**level** | **string** | (Optional for SEARCH requests) Filter results by absolute domain level (dot count) | [optional] [default to LevelEnum_All]
**findAvailable** | **boolean** | Set to true to find AVAILABLE similar domains (typo/sounding) instead of existing ones. Requires domainName, ignores similarityType/queryString/operator/level. | [optional] [default to false]
**limit** | **number** | Maximum number of results to return (use a reasonable limit to prevent excessive processing) | [optional] [default to 100]
**callbackUrl** | **string** | URL to call with results when the search is complete (must be accessible from the server) | [default to undefined]

## Example

```typescript
import { DomainerAsyncRequestDTO } from './api';

const instance: DomainerAsyncRequestDTO = {
    domainName,
    similarityType,
    queryString,
    operator,
    level,
    findAvailable,
    limit,
    callbackUrl,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
