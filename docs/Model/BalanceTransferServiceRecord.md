# BalanceTransferServiceRecord
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**type** | **string** | The type identifier for this balance transfer record. |
**recipient** | **string** | Identifier of the merchant receiving the funds. |
**remitter** | **string** | Identifier of the merchant sending the funds. |
**amount** | **int** | Amount greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**currency** | [**\Komoju\Model\Currency**](Currency.md) |  |
**happened_at** | **\DateTime** | Timestamp when the balance transfer occurred. |
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
