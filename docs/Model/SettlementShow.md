# SettlementShow
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** | A unique 25-character alphanumeric resource identifier. |
**resource** | **string** | Resource type name, always \&quot;settlement\&quot;. |
**reference** | **string** | Human-readable reference code for this settlement. |
**status** | [**\Komoju\Model\Status**](Status.md) |  |
**merchant_name** | **string** | Name of the merchant associated with this settlement. |
**company_name** | **string** | Legal company name of the merchant, or null if not set. |
**cycle** | **string** | Settlement cycle identifier (e.g. the week or month period covered). |
**transaction_amount_cents** | **int** | Amount in the lowest denomination of the currency (e.g. cents for USD). |
**currency** | [**\Komoju\Model\Currency**](Currency.md) |  |
**fee_amount_cents** | **int** | Amount in the lowest denomination of the currency (e.g. cents for USD). |
**fee_tax_amount_cents** | **int** | Amount in the lowest denomination of the currency (e.g. cents for USD). |
**settlement_amount_cents** | **int** | Amount in the lowest denomination of the currency (e.g. cents for USD). |
**fx_currency** | [**\Komoju\Model\Currency**](Currency.md) |  |
**fx_conversion_rate** | **string** | Exchange rate applied for FX conversion. |
**fx_conversion_amount_cents** | **int** | Amount in the lowest denomination of the currency (e.g. cents for USD). |
**bank_transfer_fee_amount_cents** | **int** | Amount in the lowest denomination of the currency (e.g. cents for USD). |
**remittance_amount_cents** | **int** | Amount in the lowest denomination of the currency (e.g. cents for USD). |
**cutoff_time** | **\DateTime** | Cutoff timestamp for transactions included in this settlement. |
**created_at** | **\DateTime** | Timestamp when this settlement record was created. |
**download** | [**\Komoju\Model\SettlementDownload**](SettlementDownload.md) |  |
**payments** | [**\Komoju\Model\SharedDetailsPayments**](SharedDetailsPayments.md) |  |
**refunds** | [**\Komoju\Model\SharedDetailsRefunds**](SharedDetailsRefunds.md) |  |
**platform_model** | [**\Komoju\Model\SharedDetailsPlatformModel**](SharedDetailsPlatformModel.md) |  | [optional]
**corrections** | [**\Komoju\Model\SharedDetailsCorrections**](SharedDetailsCorrections.md) |  |
**komoju_card_charges** | [**\Komoju\Model\SharedDetailsCorrections**](SharedDetailsCorrections.md) |  |
**disbursements** | [**\Komoju\Model\SharedDetailsDisbursements**](SharedDetailsDisbursements.md) |  |
**misc** | [**\Komoju\Model\SharedDetailsMisc**](SharedDetailsMisc.md) |  |
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
