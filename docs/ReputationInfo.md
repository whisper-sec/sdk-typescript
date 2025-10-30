# ReputationInfo

Reputation scoring and blacklist information for threat assessment

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**risk_score** | **number** | Composite risk score (0-10, higher &#x3D; riskier) | [optional] [default to undefined]
**blacklists** | [**BlacklistScores**](BlacklistScores.md) |  | [optional] [default to undefined]
**domain_reputation** | [**DomainReputationScores**](DomainReputationScores.md) |  | [optional] [default to undefined]

## Example

```typescript
import { ReputationInfo } from '@whisper-security/whisper-api-sdk';

const instance: ReputationInfo = {
    risk_score,
    blacklists,
    domain_reputation,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
