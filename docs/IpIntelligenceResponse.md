# IpIntelligenceResponse

Comprehensive IP intelligence response containing geolocation, network, security, and relationship data

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**query** | [**IpIntelligenceResponseQuery**](IpIntelligenceResponseQuery.md) |  | [optional] [default to undefined]
**summary** | [**IpIntelligenceResponseSummary**](IpIntelligenceResponseSummary.md) |  | [optional] [default to undefined]
**geolocation** | [**IpIntelligenceResponseGeolocation**](IpIntelligenceResponseGeolocation.md) |  | [optional] [default to undefined]
**network** | **object** | Network and routing information | [optional] [default to undefined]
**isp** | **object** | ISP and organization details | [optional] [default to undefined]
**relationships** | **object** | DNS and infrastructure relationships | [optional] [default to undefined]
**reputation** | **object** | Reputation and threat intelligence | [optional] [default to undefined]
**security** | **object** | Security assessment and RPKI status | [optional] [default to undefined]
**validation** | **object** | IP validation details | [optional] [default to undefined]
**history** | **object** | Historical routing data | [optional] [default to undefined]
**asn_details** | **object** | ASN ownership and prefix details | [optional] [default to undefined]
**metadata** | **object** | Response metadata and data sources | [optional] [default to undefined]

## Example

```typescript
import { IpIntelligenceResponse } from './api';

const instance: IpIntelligenceResponse = {
    query,
    summary,
    geolocation,
    network,
    isp,
    relationships,
    reputation,
    security,
    validation,
    history,
    asn_details,
    metadata,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
