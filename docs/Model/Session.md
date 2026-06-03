# # Session
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** | A unique 25-character alphanumeric resource identifier. |
**resource** | **string** | Resource type name, always \&quot;session\&quot;. |
**mode** | [**\Komoju\Model\SessionMode**](SessionMode.md) |  |
**amount** | **int** | Amount greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**currency** | [**\Komoju\Model\Currency**](Currency.md) |  |
**session_url** | **string** | URL to redirect the customer to for completing the session. |
**return_url** | **string** | URL the customer is redirected to after completing or cancelling the session. |
**default_locale** | [**\Komoju\Model\Locale**](Locale.md) |  |
**payment_methods** | [**\Komoju\Model\PaymentMethod[]**](PaymentMethod.md) | List of payment methods available for this session. |
**created_at** | **\DateTime** | Timestamp when the session was created. |
**cancelled_at** | **\DateTime** | Timestamp when the session was cancelled, or null if not cancelled. |
**completed_at** | **\DateTime** | Timestamp when the session was completed, or null if not completed. |
**status** | [**\Komoju\Model\SessionStatus**](SessionStatus.md) |  |
**expired** | **bool** | Whether the session has expired. |
**merchant** | [**\Komoju\Model\MerchantData**](MerchantData.md) |  |
**metadata** | **object** | Arbitrary key-value metadata attached to this session at creation time. |
**payment** | [**\Komoju\Model\Payment**](Payment.md) |  | [optional]
**payment_data** | [**\Komoju\Model\PaymentData**](PaymentData.md) |  | [optional]
**customer_id** | **string** | Subscription customer UUID. Only present when mode includes \&quot;customer\&quot;. | [optional]
**secure_token** | [**\Komoju\Model\SecureToken**](SecureToken.md) |  | [optional]
**line_items** | [**\Komoju\Model\LineItem[]**](LineItem.md) | Line items for this session. Only present when line items were provided on create. | [optional]
**merchant_id** | **string** | Merchant UUID. Only present for Platform Model seller merchants. | [optional]
**email** | **string** | Customer email. Only present when an email was provided. | [optional]
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
