# # PaymentDetailsCreditCard
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**type** | **string** | Payment method type. |
**email** | **string** | Customer&#39;s email address. Will be used for fraud prevention and payment receipt. | [optional]
**number** | **string** | Credit card number. |
**month** | **int** | Credit card expiration month. |
**year** | **int** | Credit card expiration year.  If this value is less than 100, it will be treated as two digits year in the current century. E.g. If current year is &#x60;2024&#x60;, &#x60;99&#x60; means &#x60;2099&#x60;. |
**verification_value** | **string** | Credit card verification value (Also known as CVV2 or CVC2). | [optional]
**name** | **string** | Full name of the customer.  This attribute takes precedence over &#x60;given_name&#x60; and &#x60;family_name&#x60;. | [optional]
**given_name** | **string** | Given name of the customer.  **Note:** You should only set this attribute if you have separate fields for given name and family name. Otherwise, you should only set the full name via &#x60;name&#x60;. | [optional]
**family_name** | **string** | Family name of the customer.  **Note:** You should only set this attribute if you have separate fields for given name and family name. Otherwise, you should only set the full name via &#x60;name&#x60;. | [optional]
**expiry_days** | **int** | If the payment is not immediately captured, specify how many days before the payment expires.  If this value is omitted, the default expiry day shown in the merchant dashboard will be used. | [optional]
**intent** | [**\Komoju\Model\Intent**](Intent.md) |  | [optional]
**initiator** | **string** | Specify the initiator of this payment.  Specifying this attribute can increase authorization credit card payments authorization rates, especially when using a stored card.  You can set this value to &#x60;customer&#x60; when the payment is being made for one-time goods or service purchase, or &#x60;merchant&#x60; for recurring subscription or installment payments. | [optional]
**usage** | **string** | Specify whether this payment is the first (&#x60;first&#x60;) or a subsequent payment in a series (&#x60;used&#x60;).  Specifying this attribute can increase authorization credit card payments authorization rates, especially when using a stored card. | [optional]
**scheme_reference** | **string** | Specify a scheme reference value, which is used to track the chain of multiple related payments.  This value can be subscription number for a recurring subscription payments, or installment agreement number for installment payments.  Specifying this attribute can increase authorization credit card payments authorization rates, especially when using a stored card. | [optional]
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
