# SimilarDomainRequest

Configuration for generating similar domain variations for brand protection and threat hunting

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**techniques** | **Set&lt;string&gt;** | Types of domain variations to generate | [optional] [default to undefined]
**limit** | **number** | Maximum number of similar domains to generate | [optional] [default to 100]
**check_registration** | **boolean** | Check if generated domains are registered | [optional] [default to false]
**include_dns** | **boolean** | Include DNS resolution data for registered domains | [optional] [default to false]
**include_risk_score** | **boolean** | Calculate risk scores for each variation | [optional] [default to true]
**technique_config** | [**TechniqueConfig**](TechniqueConfig.md) |  | [optional] [default to undefined]

## Example

```typescript
import { SimilarDomainRequest } from '@whisper-security/whisper-api-sdk';

const instance: SimilarDomainRequest = {
    techniques,
    limit,
    check_registration,
    include_dns,
    include_risk_score,
    technique_config,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
