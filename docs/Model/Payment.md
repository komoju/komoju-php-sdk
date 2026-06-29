# Payment
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** | A unique 25-character alphanumeric payment identifier. |
**resource** | **string** | Resource name. Will always be &#x60;payment&#x60;. |
**status** | [**\Komoju\Model\PaymentStatus**](PaymentStatus.md) |  |
**amount** | **int** | The payment amount before tax, greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**tax** | **int** | The tax amount, greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**customer** | **string** | Customer UUID if associated with a customer, otherwise null. |
**payment_deadline** | **\DateTime** | Deadline by which the payment must be completed, or null. |
**payment_details** | [**\Komoju\Model\ResponsePaymentDetailsAll**](ResponsePaymentDetailsAll.md) |  |
**payment_method_fee** | **int** | Amount greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**total** | **int** | Amount greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**currency** | [**\Komoju\Model\Currency**](Currency.md) |  |
**description** | **string** | A description for this payment. May be null if it&#39;s not set. |
**captured_at** | **\DateTime** | Timestamp when the payment was captured, or null if not yet captured. |
**external_order_num** | **string** | Merchant-assigned external order number for this payment. |
**metadata** | **object** | Arbitrary key-value metadata attached at payment creation time. |
**created_at** | **\DateTime** | Timestamp when the payment was created. |
**amount_refunded** | **int** | Amount greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**locale** | [**\Komoju\Model\Locale**](Locale.md) |  |
**session** | **string** | A unique 25-character alphanumeric resource identifier. |
**customer_family_name** | **string** | Customer&#39;s family name. |
**customer_given_name** | **string** | Customer&#39;s given name. |
**mcc** | **string** | Merchant Category Code used for this payment. |
**statement_descriptor** | [**\Komoju\Model\StatementDescriptor**](StatementDescriptor.md) |  |
**platform_details** | [**\Komoju\Model\PlatformDetails**](PlatformDetails.md) |  | [optional]
**refunds** | [**\Komoju\Model\Refund[]**](Refund.md) | An array of refunds. Will be an empty array if there are no refunds. |
**refund_requests** | [**\Komoju\Model\RefundRequest[]**](RefundRequest.md) | An array of refund requests. Will be an empty array if there are no refund requests. |
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
