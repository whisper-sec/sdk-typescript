# TyposquattingConfig

Configuration for typosquatting variations

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**character_omission** | **boolean** | Include character omission variations | [optional] [default to true]
**character_swap** | **boolean** | Include character swap variations | [optional] [default to true]
**double_character** | **boolean** | Include double character variations | [optional] [default to true]
**keyboard_proximity** | **boolean** | Include keyboard proximity variations | [optional] [default to true]

## Example

```typescript
import { TyposquattingConfig } from '@whisper-security/whisper-api-sdk';

const instance: TyposquattingConfig = {
    character_omission,
    character_swap,
    double_character,
    keyboard_proximity,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
