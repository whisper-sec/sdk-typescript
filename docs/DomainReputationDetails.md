# DomainReputationDetails

Detailed infrastructure and individual IP scores

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**domain_ips** | **Array&lt;string&gt;** | Domain\&#39;s A record IP addresses | [optional] [default to undefined]
**domain_ip_scores** | **{ [key: string]: number; }** | Individual scores for each domain IP | [optional] [default to undefined]
**nameserver_domains** | **Array&lt;string&gt;** | Nameserver domain names | [optional] [default to undefined]
**nameserver_ips** | **Array&lt;string&gt;** | IP addresses of nameservers | [optional] [default to undefined]
**nameserver_ip_scores** | **{ [key: string]: number; }** | Individual scores for each nameserver IP | [optional] [default to undefined]
**mailserver_domains** | **Array&lt;string&gt;** | Mail server domain names | [optional] [default to undefined]
**mailserver_ips** | **Array&lt;string&gt;** | IP addresses of mail servers | [optional] [default to undefined]
**mailserver_ip_scores** | **{ [key: string]: number; }** | Individual scores for each mail server IP | [optional] [default to undefined]

## Example

```typescript
import { DomainReputationDetails } from '@whisper-security/whisper-api-sdk';

const instance: DomainReputationDetails = {
    domain_ips,
    domain_ip_scores,
    nameserver_domains,
    nameserver_ips,
    nameserver_ip_scores,
    mailserver_domains,
    mailserver_ips,
    mailserver_ip_scores,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
