# ChargebackPayment
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** | A unique 25-character alphanumeric resource identifier. |
**amount** | **int** | Amount greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**currency** | [**\Komoju\Model\Currency**](Currency.md) |  |
**created_at** | **\DateTime** | Timestamp when the payment was created. |
**captured_at** | **\DateTime** | Timestamp when the payment was captured, or null. |
**payment_method** | [**\Komoju\Model\ChargebackPaymentMethod**](ChargebackPaymentMethod.md) |  |
**masked_card_number** | **string** | Masked card number, or null if not applicable. |
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
