# # PlatformPayment
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** | A unique 25-character alphanumeric resource identifier. |
**resource** | **string** | Resource type name, always \&quot;payment\&quot;. |
**status** | [**\Komoju\Model\PaymentStatus**](PaymentStatus.md) |  |
**amount** | **int** | Amount greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**tax** | **int** | Amount greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**customer** | **string** | Customer UUID if associated with a customer, otherwise null. |
**payment_deadline** | **string** | Deadline by which the payment must be completed, or null. |
**payment_details** | **string** | Serialized payment method details for this payment. |
**payment_method_fee** | **int** | Amount greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**total** | **int** | Amount greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**currency** | [**\Komoju\Model\Currency**](Currency.md) |  |
**description** | **string** | Optional description for the payment. |
**captured_at** | **\DateTime** | Timestamp when the payment was captured, or null if not yet captured. |
**external_order_num** | **string** | External order reference from the merchant&#39;s system. |
**metadata** | **object** | Arbitrary key-value metadata attached to the payment. |
**created_at** | **\DateTime** | Timestamp when the payment was created. |
**amount_refunded** | **int** | Amount greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**locale** | [**\Komoju\Model\Locale**](Locale.md) |  |
**session** | **string** | A unique 25-character alphanumeric resource identifier. |
**customer_family_name** | **string** | Customer&#39;s family name. |
**customer_given_name** | **string** | Customer&#39;s given name. |
**platform_details** | [**\Komoju\Model\PlatformDetails**](PlatformDetails.md) |  |
**mcc** | **string** | Merchant Category Code used for this payment. |
**statement_descriptor** | **string** | Statement descriptor shown to the customer on their bank statement. |
**refunds** | **object[]** | Array of refund objects associated with this payment. |
**refund_requests** | **object[]** | Array of refund request objects associated with this payment. |
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
