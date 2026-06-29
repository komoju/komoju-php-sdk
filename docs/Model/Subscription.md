# Subscription
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** | A unique 25-character alphanumeric resource identifier. |
**resource** | **string** | Resource type name, always \&quot;subscription\&quot;. |
**status** | **string** | Current status of the subscription (e.g. \&quot;active\&quot;, \&quot;cancelled\&quot;). |
**amount** | **int** | Amount greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**currency** | [**\Komoju\Model\Currency**](Currency.md) |  |
**customer** | [**\Komoju\Model\SubscriptionCustomer**](SubscriptionCustomer.md) |  |
**period** | [**\Komoju\Model\SubscriptionPeriod**](SubscriptionPeriod.md) |  |
**day** | **int** | Day of the period on which the subscription is charged. |
**payment_details** | [**\Komoju\Model\SubscriptionPaymentDetails**](SubscriptionPaymentDetails.md) |  |
**retry_count** | **int** | Number of times payment has been retried after failure. |
**retry_at** | **\DateTime** | Timestamp of the next scheduled payment retry, or null. |
**next_capture_at** | **\DateTime** | Timestamp of the next scheduled subscription charge. |
**created_at** | **\DateTime** | Timestamp when the subscription was created. |
**ended_at** | **\DateTime** | Timestamp when the subscription ended, or null if still active. |
**metadata** | **object** | Arbitrary key-value metadata attached to the subscription. |
**payments** | **string[]** | Array of payment UUIDs associated with this subscription. |
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
