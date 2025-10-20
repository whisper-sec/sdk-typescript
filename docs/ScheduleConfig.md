# ScheduleConfig

Configuration for scheduling recurring screenshot captures

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**cron** | **string** | Cron expression for scheduling | [optional] [default to undefined]
**frequency** | **string** | Frequency of captures | [optional] [default to undefined]
**timezone** | **string** | Timezone for scheduled captures | [optional] [default to 'UTC']
**retention_count** | **number** | Maximum number of captures to retain | [optional] [default to 30]
**enabled** | **boolean** | Enable/disable the schedule | [optional] [default to true]

## Example

```typescript
import { ScheduleConfig } from '@whisper-security/whisper-api-sdk';

const instance: ScheduleConfig = {
    cron,
    frequency,
    timezone,
    retention_count,
    enabled,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
