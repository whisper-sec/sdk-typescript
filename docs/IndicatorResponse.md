# IndicatorResponse

Comprehensive intelligence response for an IP address or domain indicator

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**query** | [**QueryInfo**](QueryInfo.md) |  | [optional] [default to undefined]
**summary** | [**SummaryInfo**](SummaryInfo.md) |  | [optional] [default to undefined]
**geolocation** | **object** |  | [optional] [default to undefined]
**network** | **object** |  | [optional] [default to undefined]
**isp** | **object** |  | [optional] [default to undefined]
**registration** | **object** |  | [optional] [default to undefined]
**dns** | [**DnsInfo**](DnsInfo.md) |  | [optional] [default to undefined]
**relationships** | [**RelationshipInfo**](RelationshipInfo.md) |  | [optional] [default to undefined]
**reputation** | [**ReputationInfo**](ReputationInfo.md) |  | [optional] [default to undefined]
**security** | **object** |  | [optional] [default to undefined]
**ip_intelligence** | **{ [key: string]: object; }** | When domain is queried with include&#x3D;ip_intelligence, contains full intelligence for each resolved IP | [optional] [default to undefined]
**metadata** | [**MetadataInfo**](MetadataInfo.md) |  | [optional] [default to undefined]

## Example

```typescript
import { IndicatorResponse } from '@whisper-security/whisper-api-sdk';

const instance: IndicatorResponse = {
    query,
    summary,
    geolocation,
    network,
    isp,
    registration,
    dns,
    relationships,
    reputation,
    security,
    ip_intelligence,
    metadata,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
