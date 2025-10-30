# DnsInfo

DNS records and resolution data for the domain

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**arecords** | **Array&lt;string&gt;** |  | [optional] [default to undefined]
**a_records** | **Array&lt;string&gt;** | A records (IPv4 addresses) | [optional] [default to undefined]
**aaaa_records** | **Array&lt;string&gt;** | AAAA records (IPv6 addresses) | [optional] [default to undefined]
**mx_records** | **Array&lt;object&gt;** | MX records (mail servers) with priority and hostname | [optional] [default to undefined]
**ns_records** | **Array&lt;string&gt;** | NS records (name servers) | [optional] [default to undefined]
**txt_records** | **Array&lt;string&gt;** | TXT records (text records for SPF, DKIM, etc.) | [optional] [default to undefined]
**cname_records** | **Array&lt;string&gt;** | CNAME records (canonical name aliases) | [optional] [default to undefined]

## Example

```typescript
import { DnsInfo } from '@whisper-security/whisper-api-sdk';

const instance: DnsInfo = {
    arecords,
    a_records,
    aaaa_records,
    mx_records,
    ns_records,
    txt_records,
    cname_records,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
