# # ResponsePaymentDetailsEpospay
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**type** | **string** | Payment method type. |
**email** | **string** | Customer&#39;s email address. Will be used for fraud prevention and payment receipt. |
**offsite_fake_new_path** | **string** | When using test mode. | [optional]
**offsite_url** | **string** | URL for the customer to complete the EPOS payment offsite. | [optional]
**merchant_id** | **string** | Merchant identifier used in the EPOS payment request. | [optional]
**shop_id** | **string** | Shop identifier used in the EPOS payment request. | [optional]
**deal_id** | **string** | Deal identifier for this EPOS transaction. | [optional]
**token** | **string** | Authentication token for the EPOS payment. | [optional]
**prd_list** | **string** | Product list data for the EPOS payment. | [optional]
**amount** | **int** | Payment amount in the lowest denomination of the currency. | [optional]
**customer_id** | **string** | Customer identifier in the EPOS system. | [optional]
**return_url** | **string** | URL to redirect the customer to after completing the EPOS payment. | [optional]
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
