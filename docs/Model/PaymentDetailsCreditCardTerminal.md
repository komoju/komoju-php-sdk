# # PaymentDetailsCreditCardTerminal
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**type** | **string** | Payment method type. |
**number** | **string** | Credit card number. |
**month** | **int** | Credit card expiration month. | [optional]
**year** | **int** | Credit card expiration year.  If this value is less than 100, it will be treated as two digits year in the current century. E.g. If current year is &#x60;2024&#x60;, &#x60;99&#x60; means &#x60;2099&#x60;. | [optional]
**sequence_number** | **string** | Specify the sequence number from the credit card terminal | [optional]
**field55** | **string** | Specify the EMV data produced by the terminal. | [optional]
**pos_data_code** | **string** | Specify the POS data code produced by the terminal. | [optional]
**track2** | **string** | Specify the data read from track 2 of the payment card. | [optional]
**flow_type** | **string** | Specify whether this transaction is a EMV or magnetic stripe transaction.  - Use value \&quot;1\&quot; for EMV transaction. - Use value \&quot;2\&quot; for magnetic stripe transaction. | [optional]
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
