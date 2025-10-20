# BlacklistScores

Blacklist scores at different network levels

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**ip_score** | **number** | IP-level blacklist score | [optional] [default to undefined]
**prefix_score** | **number** | Network prefix blacklist score | [optional] [default to undefined]
**asn_score** | **number** | ASN-level blacklist score | [optional] [default to undefined]

## Example

```typescript
import { BlacklistScores } from '@whisper-security/whisper-api-sdk';

const instance: BlacklistScores = {
    ip_score,
    prefix_score,
    asn_score,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
