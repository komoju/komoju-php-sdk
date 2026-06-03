# # PaymentDataRequest
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**capture** | **string** | Whether to capture the payment automatically on completion, or hold it for manual capture later. | [optional]
**amount** | **int** | Amount greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). | [optional]
**currency** | [**\Komoju\Model\Currency**](Currency.md) |  | [optional]
**external_order_num** | **string** | Merchant-assigned order reference number to associate with the payment. | [optional]
**name** | **string** | Customer&#39;s full name. | [optional]
**name_kana** | **string** | Customer&#39;s full name in katakana. | [optional]
**mcc** | **string** | Merchant Category Code to use for this payment. | [optional]
**intent** | [**\Komoju\Model\Intent**](Intent.md) |  | [optional]
**statement_descriptor** | [**\Komoju\Model\StatementDescriptor**](StatementDescriptor.md) |  | [optional]
**platform_details** | [**\Komoju\Model\PlatformDetails**](PlatformDetails.md) |  | [optional]
**billing_address** | [**\Komoju\Model\Address**](Address.md) |  | [optional]
**shipping_address** | [**\Komoju\Model\Address**](Address.md) |  | [optional]
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
