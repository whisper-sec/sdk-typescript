# ScanOptions

Advanced configuration options for infrastructure scanning

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**port_scan** | [**PortScanConfig**](PortScanConfig.md) |  | [optional] [default to undefined]
**service_discovery** | [**ServiceDiscoveryConfig**](ServiceDiscoveryConfig.md) |  | [optional] [default to undefined]
**vulnerability** | [**VulnerabilityConfig**](VulnerabilityConfig.md) |  | [optional] [default to undefined]
**dns_enum** | [**DnsEnumConfig**](DnsEnumConfig.md) |  | [optional] [default to undefined]

## Example

```typescript
import { ScanOptions } from '@whisper-security/whisper-api-sdk';

const instance: ScanOptions = {
    port_scan,
    service_discovery,
    vulnerability,
    dns_enum,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
