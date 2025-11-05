# RelationshipInfo

Connections and relationships to other infrastructure and domains

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**incoming_links** | [**LinksInfo**](LinksInfo.md) |  | [optional] [default to undefined]
**outgoing_links** | [**LinksInfo**](LinksInfo.md) |  | [optional] [default to undefined]
**related_domains** | **Array&lt;string&gt;** | Related domains (same owner, same network, similar content) | [optional] [default to undefined]
**shared_infrastructure** | **Array&lt;string&gt;** | Other assets sharing the same infrastructure (IP, ASN, nameservers) | [optional] [default to undefined]

## Example

```typescript
import { RelationshipInfo } from '@whisper-security/whisper-api-sdk';

const instance: RelationshipInfo = {
    incoming_links,
    outgoing_links,
    related_domains,
    shared_infrastructure,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
