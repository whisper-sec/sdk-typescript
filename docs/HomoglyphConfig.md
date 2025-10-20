# HomoglyphConfig

Configuration for homoglyph (look-alike character) variations

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**cyrillic** | **boolean** | Include Cyrillic character substitutions | [optional] [default to true]
**greek** | **boolean** | Include Greek character substitutions | [optional] [default to true]
**latin** | **boolean** | Include Latin character substitutions | [optional] [default to true]
**max_substitutions** | **number** | Maximum number of character substitutions per domain | [optional] [default to 2]

## Example

```typescript
import { HomoglyphConfig } from '@whisper-security/whisper-api-sdk';

const instance: HomoglyphConfig = {
    cyrillic,
    greek,
    latin,
    max_substitutions,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
