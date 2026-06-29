# CreateSubscriptionRequest
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**customer** | **string** | A unique 25-character alphanumeric resource identifier. |
**amount** | **int** | Amount greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**currency** | [**\Komoju\Model\Currency**](Currency.md) |  |
**period** | [**\Komoju\Model\SubscriptionPeriod**](SubscriptionPeriod.md) |  |
**metadata** | **object** | Store any additional data you want to associate with the subscription. The object&#39;s keys and values must be strings. Keys have a maximum length of 30 characters. Values have a maximum length of 2000 characters. | [optional]
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
