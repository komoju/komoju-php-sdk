# PaymentMethodApplicationWithSubmittedFields
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**merchant_id** | **string** | A unique 25-character alphanumeric resource identifier. |
**status** | [**\Komoju\Model\PaymentMethodApplicationStatus**](PaymentMethodApplicationStatus.md) |  |
**payments_enabled** | **bool** | Whether payments have been enabled following payment-method review. |
**payouts_enabled** | **bool** | Whether payouts have been enabled following payment-method review. |
**requested_fields** | [**\Komoju\Model\Field[]**](Field.md) | Fields currently required to be submitted for this payment method. |
**newly_requested_fields** | [**\Komoju\Model\Field[]**](Field.md) | Fields newly added to the required list since last submission. |
**errored_fields** | [**\Komoju\Model\ErroredField[]**](ErroredField.md) | Fields that were submitted but failed validation. |
**submitted_fields** | [**\Komoju\Model\SubmittedField[]**](SubmittedField.md) |  |
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
