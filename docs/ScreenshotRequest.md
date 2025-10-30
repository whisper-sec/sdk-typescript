# ScreenshotRequest

Request parameters for capturing a website screenshot

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**url** | **string** | The URL of the website to capture | [default to undefined]
**_options** | [**ScreenshotOptions**](ScreenshotOptions.md) |  | [optional] [default to undefined]
**schedule** | [**ScheduleConfig**](ScheduleConfig.md) |  | [optional] [default to undefined]

## Example

```typescript
import { ScreenshotRequest } from '@whisper-security/whisper-api-sdk';

const instance: ScreenshotRequest = {
    url,
    _options,
    schedule,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
