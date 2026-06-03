# # CreateDisbursementRequest
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**amount** | **int** | Amount greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**currency** | [**\Komoju\Model\Currency**](Currency.md) |  |
**account_number** | **string** | Recipient&#39;s bank account number. |
**account_type** | **string** | Type of the recipient&#39;s bank account. |
**account_name_kana** | **string** | Name of the recipient bank account holder in katakana. |
**bank_code** | **string** | 4-digit Zengin bank code. |
**branch_code** | **string** | 3-digit Zengin branch code. |
**external_id** | **string** | Merchant-assigned external reference ID for this disbursement. | [optional]
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
