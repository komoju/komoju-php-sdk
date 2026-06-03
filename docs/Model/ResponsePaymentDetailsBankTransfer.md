# # ResponsePaymentDetailsBankTransfer
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**type** | **string** | Payment method type. |
**email** | **string** | Customer&#39;s email address. Will be used for fraud prevention, payment instruction, and payment receipt. |
**order_id** | **string** | Order identifier for this bank transfer. | [optional]
**bank_name** | **string** | Name of the bank to transfer funds to. | [optional]
**account_branch_name** | **string** | Name of the bank branch. | [optional]
**account_number** | **string** | Bank account number to transfer funds to. | [optional]
**account_type** | **string** | Type of bank account. | [optional]
**account_name** | **string** | Name of the bank account holder. | [optional]
**instructions_url** | **string** | URL with payment instructions for the customer. | [optional]
**payment_deadline** | **\DateTime** | Deadline by which the bank transfer must be completed. | [optional]
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
