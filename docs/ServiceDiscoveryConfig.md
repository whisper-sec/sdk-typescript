# ServiceDiscoveryConfig

Configuration for service and version detection

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**version_detection** | **boolean** | Enable service version detection | [optional] [default to true]
**os_detection** | **boolean** | Enable OS fingerprinting | [optional] [default to false]
**intensity** | **number** | Aggressiveness of service detection (1-9) | [optional] [default to 5]
**script_scan** | **boolean** | Enable script scanning | [optional] [default to false]

## Example

```typescript
import { ServiceDiscoveryConfig } from '@whisper-security/whisper-api-sdk';

const instance: ServiceDiscoveryConfig = {
    version_detection,
    os_detection,
    intensity,
    script_scan,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
