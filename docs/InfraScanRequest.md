# InfraScanRequest

Configuration for performing infrastructure discovery and security scanning

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**target** | **string** | The target to scan (IP, CIDR, domain, or ASN) | [default to undefined]
**target_type** | **string** | Type of target being scanned | [default to undefined]
**scan_types** | **Set&lt;string&gt;** | Types of scans to perform | [optional] [default to undefined]
**scan_depth** | **string** | Scan depth level | [optional] [default to ScanDepthEnum_Medium]
**timeout** | **number** | Maximum scan duration in seconds | [optional] [default to 300]
**_options** | [**ScanOptions**](ScanOptions.md) |  | [optional] [default to undefined]

## Example

```typescript
import { InfraScanRequest } from '@whisper-security/whisper-api-sdk';

const instance: InfraScanRequest = {
    target,
    target_type,
    scan_types,
    scan_depth,
    timeout,
    _options,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
