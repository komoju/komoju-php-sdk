# ChargebackRequestDetail
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** | A unique 25-character alphanumeric resource identifier. |
**status** | [**\Komoju\Model\ChargebackStatus**](ChargebackStatus.md) |  |
**reason_code** | **string** | Machine-readable reason code. Internal codes (e.g. \&quot;CB_Fraud\&quot;) are used by default; for Worldpay Visa/Mastercard payments the network&#39;s own reason codes are used instead (e.g. \&quot;10.4\&quot; or \&quot;4837\&quot;). |
**reason** | **string** | Human-readable chargeback reason corresponding to the reason code. |
**created_at** | **\DateTime** | Timestamp when the chargeback was created. |
**due_date** | **\DateTime** | Deadline by which the merchant must respond. |
**last_updated_at** | **\DateTime** | Timestamp when the chargeback was last updated. |
**timeline** | [**\Komoju\Model\ChargebackTimelineEntry[]**](ChargebackTimelineEntry.md) | Chronological list of chargeback events. |
**payment** | [**\Komoju\Model\ChargebackPayment**](ChargebackPayment.md) |  |
**customer** | [**\Komoju\Model\ChargebackCustomer**](ChargebackCustomer.md) |  |
**defense** | [**\Komoju\Model\ChargebackDefense**](ChargebackDefense.md) |  |
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
