# TechniqueConfig

Detailed configuration for each domain variation technique

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**typosquatting** | [**TyposquattingConfig**](TyposquattingConfig.md) |  | [optional] [default to undefined]
**homoglyph** | [**HomoglyphConfig**](HomoglyphConfig.md) |  | [optional] [default to undefined]
**bitsquatting** | [**BitsquattingConfig**](BitsquattingConfig.md) |  | [optional] [default to undefined]
**tld_variation** | [**TldVariationConfig**](TldVariationConfig.md) |  | [optional] [default to undefined]

## Example

```typescript
import { TechniqueConfig } from '@whisper-security/whisper-api-sdk';

const instance: TechniqueConfig = {
    typosquatting,
    homoglyph,
    bitsquatting,
    tld_variation,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
