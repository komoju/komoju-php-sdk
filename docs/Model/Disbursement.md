# Disbursement
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** | A unique 25-character alphanumeric resource identifier. |
**currency** | [**\Komoju\Model\Currency**](Currency.md) |  |
**amount** | **int** | Amount greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**fee** | **int** | Amount greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**fee_tax** | **int** | Amount greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**status** | [**\Komoju\Model\DisbursementStatus**](DisbursementStatus.md) |  |
**bank_code** | **string** | 4-digit Zengin bank code of the recipient&#39;s bank. |
**branch_code** | **string** | 3-digit Zengin branch code. |
**account_type** | **string** | Type of the recipient&#39;s bank account. |
**account_number** | **string** | Recipient&#39;s bank account number. |
**account_name_kana** | **string** | Name of the recipient bank account holder in katakana. |
**error** | **string** | Error message if the disbursement failed, otherwise null. |
**external_id** | **string** | Merchant-assigned external reference ID for this disbursement. |
**created_at** | **\DateTime** | Timestamp when the disbursement was created. |
**last_updated_at** | **\DateTime** | Timestamp when the disbursement record was last updated. |
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
