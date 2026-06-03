# # ResponsePaymentDetailsCreditCard
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**type** | **string** | Payment method type. |
**brand** | **string** | Card brand (e.g. \&quot;visa\&quot;, \&quot;mastercard\&quot;, \&quot;jcb\&quot;). |
**last_four_digits** | **string** | Last four digits of the card number. |
**month** | **int** | Credit card expiration month. |
**year** | **int** | Credit card expiration year.  If this value is less than 100, it will be treated as two digits year in the current century. E.g. If current year is &#x60;2024&#x60;, &#x60;99&#x60; means &#x60;2099&#x60;. |
**email** | **string** | Customer&#39;s email address. Will be used for fraud prevention and payment receipt. |
**verification_value** | **string** |  | [optional]
**name** | **string** | Full name of the customer.  This attribute takes precedence over &#x60;given_name&#x60; and &#x60;family_name&#x60;. | [optional]
**given_name** | **string** | Given name of the customer. | [optional]
**family_name** | **string** | Family name of the customer. | [optional]
**expiry_days** | **int** |  | [optional]
**intent** | **string** |  | [optional]
**initiator** | **string** |  | [optional]
**usage** | **string** |  | [optional]
**scheme_reference** | **string** |  | [optional]
**installments** | [**\Komoju\Model\Installments**](Installments.md) |  | [optional]
**shipping_address_name** | **string** | Shipping address name. This is the recipient&#39;s name. | [optional]
**shipping_address_line1** | **string** | Shipping address line 1. | [optional]
**shipping_address_line2** | **string** | Shipping address line 2. | [optional]
**shipping_address_city** | **string** | Shipping address city. | [optional]
**shipping_address_state** | **string** | Shipping address state. | [optional]
**shipping_address_zip** | **string** | Shipping address ZIP code. | [optional]
**shipping_address_country** | **string** | Shipping address country. | [optional]
**billing_address_name** | **string** | Billing address name. This is the paying customer&#39;s name. | [optional]
**billing_address_line1** | **string** | Billing address line 1. | [optional]
**billing_address_line2** | **string** | Billing address line 2. | [optional]
**billing_address_city** | **string** | Billing address city. | [optional]
**billing_address_state** | **string** | Billing address state. | [optional]
**billing_address_zip** | **string** | Billing address ZIP code. | [optional]
**billing_address_country** | **string** | Billing address country. | [optional]
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
