# CreateRefundRequestRequest
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**amount** | **int** | The payment amount before tax, greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**customer_name** | **string** | Customer&#39;s name in half-width katakana, as registered at the bank. |
**bank_name** | **string** | Name of the customer&#39;s bank. |
**bank_code** | **string** | Optional 4-digit Zengin bank code. | [optional]
**branch_name** | **string** | Name of the customer&#39;s bank branch. | [optional]
**branch_number** | **string** | 3-digit branch number. |
**account_type** | **string** | Type of the customer&#39;s bank account. |
**account_number** | **int** | 7-digit bank account number to deposit the refund into. |
**include_payment_method_fee** | **bool** | Whether the refund should include the original payment method fee. |
**description** | **string** | Optional description or reason for this refund request. | [optional]
**platform_details** | [**\Komoju\Model\PlatformDetails**](PlatformDetails.md) |  | [optional]
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
