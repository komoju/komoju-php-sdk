# # PaymentDetailsPaidy
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**type** | **string** | Payment method type. |
**customer_age** | **int** |  | [optional]
**customer_last_order_amount** | **int** |  | [optional]
**customer_last_order_at** | **int** |  | [optional]
**customer_lifetime_value** | **int** |  | [optional]
**customer_name** | **string** |  |
**customer_order_count** | **int** |  | [optional]
**email** | **string** | Customer&#39;s email address. Will be used for fraud prevention and payment receipt. | [optional]
**phone** | **string** | Customer&#39;s phone number | [optional]
**external_customer_id** | **string** |  | [optional]
**item_title** | **string** |  | [optional]
**customer_name_kana** | **string** |  | [optional]
**capture** | **bool** |  | [optional]
**shipping_address_name** | **string** | Shipping address name.  This is the recipient&#39;s name. | [optional]
**shipping_address_line1** | **string** | Shipping address line 1.  For Japanese addresses: building name, apartment number. Required for physical products. | [optional]
**shipping_address_line2** | **string** | Shipping address line 2.  For Japanese addresses: district, land number, land number extension. | [optional]
**shipping_address_city** | **string** | Shipping address city.  Name of city, municipality, or village. Required for physical products. | [optional]
**shipping_address_state** | **string** | Shipping address state / prefecture.  Required for physical products. | [optional]
**shipping_address_zip** | **string** | Shipping address ZIP code, in a 7-digit format (NNN-NNNN). Required for physical products. | [optional]
**shipping_address_country** | **string** | Shipping address country. Required for physical products. | [optional]
**billing_address_name** | **string** | Billing address name. This is the paying customer&#39;s name. | [optional]
**billing_address_line1** | **string** | Billing address line 1. | [optional]
**billing_address_line2** | **string** | Billing address line 2. | [optional]
**billing_address_city** | **string** | Billing address city. | [optional]
**billing_address_state** | **string** | Billing address state. | [optional]
**billing_address_zip** | **string** | Billing address ZIP code. | [optional]
**billing_address_country** | **string** | Billing address country. | [optional]
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
