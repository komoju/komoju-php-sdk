# Transaction
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** | A unique 25-character alphanumeric resource identifier. |
**type** | **string** | Type of ledger transaction (e.g. \&quot;payment\&quot;, \&quot;fee\&quot;, \&quot;disbursement\&quot;). |
**amount_cents** | **int** | Amount greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**happened_at** | **\DateTime** | Timestamp when this ledger transaction occurred. |
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
