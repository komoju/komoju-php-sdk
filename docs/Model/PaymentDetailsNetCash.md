# PaymentDetailsNetCash
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**type** | **string** | Payment method type.  **Note:** This payment method support updating the payment with additional prepaid cards to cover the total balance. In case of insufficient funds, the payment status will be &#x60;pending&#x60;.  The &#x60;payment_details&#x60; in the response will also include these two attributes:  - &#x60;short_amount&#x60;: The amount that the payment is short by. - &#x60;prepaid_cards&#x60;: A list of prepaid cards used in the transaction.  Please see the integration document for more details. |
**email** | **string** | Customer&#39;s email address. Will be used for fraud prevention and payment receipt. | [optional]
**prepaid_number** | **string** | Prepaid card number. |
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
