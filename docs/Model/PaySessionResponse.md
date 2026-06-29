# PaySessionResponse
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**redirect_url** | **string** | URL to redirect the customer to after submitting payment details, or null if no redirect is required. |
**status** | [**\Komoju\Model\SessionStatus**](SessionStatus.md) |  |
**payment** | [**\Komoju\Model\Payment**](Payment.md) |  | [optional]
**app_url** | **string** | URL for the payment app. Only present for offsite payments with a QR/app URL. | [optional]
**customer** | [**\Komoju\Model\SubscriptionCustomer**](SubscriptionCustomer.md) |  | [optional]
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
