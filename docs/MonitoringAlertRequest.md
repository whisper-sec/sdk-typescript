# MonitoringAlertRequest

Configuration for creating monitoring alert rules with notification channels

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**type** | **string** | Type of alert condition to monitor | [default to undefined]
**threshold_days** | **number** | Threshold in days (for ssl_expiring alerts). Alert triggers when SSL cert expires within this many days. | [optional] [default to undefined]
**channels** | **Set&lt;string&gt;** | Notification channels to use for alerts | [optional] [default to undefined]
**email** | **string** | Email address for alert notifications | [optional] [default to undefined]
**slack_webhook** | **string** | Slack webhook URL for notifications | [optional] [default to undefined]
**webhook_url** | **string** | Custom webhook URL for notifications (will receive POST with alert data) | [optional] [default to undefined]
**pagerduty_key** | **string** | PagerDuty integration key for incident creation | [optional] [default to undefined]

## Example

```typescript
import { MonitoringAlertRequest } from '@whisper-security/whisper-api-sdk';

const instance: MonitoringAlertRequest = {
    type,
    threshold_days,
    channels,
    email,
    slack_webhook,
    webhook_url,
    pagerduty_key,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
