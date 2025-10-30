# DomainReputationScores

Domain reputation calculated from infrastructure IP scores

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**overall_score** | **number** | Overall reputation score (0-100, higher &#x3D; more suspicious) | [optional] [default to undefined]
**risk_level** | **string** | Risk classification based on overall score | [optional] [default to undefined]
**domain_ip_score** | **number** | Average IP reputation score for domain\&#39;s A records | [optional] [default to undefined]
**nameserver_ip_score** | **number** | Average IP reputation score for nameserver IPs | [optional] [default to undefined]
**mailserver_ip_score** | **number** | Average IP reputation score for mail server IPs | [optional] [default to undefined]
**details** | [**DomainReputationDetails**](DomainReputationDetails.md) |  | [optional] [default to undefined]
**scoring_method** | **string** | Scoring methodology used | [optional] [default to undefined]
**weights** | **{ [key: string]: number; }** | Weighting strategy applied to infrastructure components | [optional] [default to undefined]

## Example

```typescript
import { DomainReputationScores } from '@whisper-security/whisper-api-sdk';

const instance: DomainReputationScores = {
    overall_score,
    risk_level,
    domain_ip_score,
    nameserver_ip_score,
    mailserver_ip_score,
    details,
    scoring_method,
    weights,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
