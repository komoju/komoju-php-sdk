# ChargebackRequestListItem
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** | A unique 25-character alphanumeric resource identifier. |
**payment_id** | **string** | A unique 25-character alphanumeric resource identifier. |
**amount** | **int** | Amount greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**currency** | [**\Komoju\Model\Currency**](Currency.md) |  |
**payment_method** | [**\Komoju\Model\ChargebackPaymentMethod**](ChargebackPaymentMethod.md) |  |
**reason_code** | **string** | Machine-readable reason code. Internal codes (e.g. \&quot;CB_Fraud\&quot;) are used by default; for Worldpay Visa/Mastercard payments the network&#39;s own reason codes are used instead (e.g. \&quot;10.4\&quot; or \&quot;4837\&quot;). |
**reason** | **string** | Human-readable chargeback reason corresponding to the reason code. |
**created_at** | **\DateTime** | Timestamp when the chargeback was created. |
**due_date** | **\DateTime** | Deadline by which the merchant must respond. |
**status** | [**\Komoju\Model\ChargebackStatus**](ChargebackStatus.md) |  |
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
