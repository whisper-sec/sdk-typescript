# PortScanConfig

Configuration for port scanning

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**ports** | **string** | Ports to scan (comma-separated or range) | [optional] [default to 'top-1000']
**technique** | **string** | Scan technique | [optional] [default to TechniqueEnum_Syn]
**threads** | **number** | Number of parallel threads | [optional] [default to 10]
**port_timeout** | **number** | Timeout per port in milliseconds | [optional] [default to 1000]

## Example

```typescript
import { PortScanConfig } from '@whisper-security/whisper-api-sdk';

const instance: PortScanConfig = {
    ports,
    technique,
    threads,
    port_timeout,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
