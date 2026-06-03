# # PaymentMethod
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**type** | **string** | Machine-readable type slug for this payment method (e.g. \&quot;credit_card\&quot;, \&quot;konbini\&quot;). |
**hashed_gateway** | **string** | Hashed identifier of the payment gateway processing this method. | [optional]
**amount** | **int** | Amount greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). | [optional]
**currency** | [**\Komoju\Model\Currency**](Currency.md) |  | [optional]
**exchange_rate** | **float** | Exchange rate applied when this payment method&#39;s currency differs from the session currency. | [optional]
**offsite** | **bool** | Whether this payment method redirects the customer to an external site to complete payment. | [optional]
**additional_fields** | **string[]** | Names of additional input fields required to complete payment with this method. | [optional]
**brands** | [**\Komoju\Model\PaymentMethodBrands**](PaymentMethodBrands.md) |  | [optional]
**seven_eleven_merchant_number** | **string** | Only for Konbini | [optional]
**installments** | [**\Komoju\Model\PaymentMethodInstallmentsInner[]**](PaymentMethodInstallmentsInner.md) | Only for Komoju Pay | [optional]
**api_endpoint** | **string** | Only for Komoju Pay | [optional]
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
