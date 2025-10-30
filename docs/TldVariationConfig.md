# TldVariationConfig

Configuration for top-level domain variations

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**common_tlds** | **boolean** | Include common TLD variations (.com, .net, .org, etc.) | [optional] [default to true]
**country_tlds** | **boolean** | Include country-code TLDs | [optional] [default to false]
**new_gtlds** | **boolean** | Include new generic TLDs (.app, .dev, .cloud, etc.) | [optional] [default to true]
**custom_tlds** | **Set&lt;string&gt;** | Custom TLDs to check | [optional] [default to undefined]

## Example

```typescript
import { TldVariationConfig } from '@whisper-security/whisper-api-sdk';

const instance: TldVariationConfig = {
    common_tlds,
    country_tlds,
    new_gtlds,
    custom_tlds,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
