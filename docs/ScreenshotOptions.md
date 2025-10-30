# ScreenshotOptions

Configuration options for screenshot capture

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**width** | **number** | Viewport width in pixels | [optional] [default to 1920]
**height** | **number** | Viewport height in pixels | [optional] [default to 1080]
**full_page** | **boolean** | Capture the full page height (scrolling screenshot) | [optional] [default to false]
**wait_time** | **number** | Wait time in milliseconds before taking screenshot | [optional] [default to 2000]
**format** | **string** | Image format for the screenshot | [optional] [default to FormatEnum_Png]
**quality** | **number** | Image quality (1-100, only for jpeg/webp) | [optional] [default to 90]
**user_agent** | **string** | User agent string to use for the request | [optional] [default to undefined]
**javascript** | **boolean** | Enable JavaScript execution | [optional] [default to true]
**block_ads** | **boolean** | Block ads and trackers | [optional] [default to false]
**accept_cookies** | **boolean** | Accept cookies consent if prompted | [optional] [default to true]

## Example

```typescript
import { ScreenshotOptions } from '@whisper-security/whisper-api-sdk';

const instance: ScreenshotOptions = {
    width,
    height,
    full_page,
    wait_time,
    format,
    quality,
    user_agent,
    javascript,
    block_ads,
    accept_cookies,
};
```

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)
