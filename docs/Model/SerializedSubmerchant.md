# SerializedSubmerchant
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** | Unique identifier for this sub-merchant. |
**live** | **bool** | Whether this merchant is operating in live (production) mode. |
**created_at** | **\DateTime** | Timestamp when this merchant was created. |
**updated_at** | **\DateTime** | Timestamp when this merchant record was last updated. |
**account_id** | **string** | Account identifier associated with this merchant. |
**name** | **string** | Display name of the sub-merchant. |
**platform_role** | [**\Komoju\Model\MerchantRole**](MerchantRole.md) |  |
**status** | **string** | Current account/application status of the merchant. |
**payments_enabled** | **bool** | Whether payments are currently enabled for this merchant. |
**payouts_enabled** | **bool** | Whether payouts are currently enabled for this merchant. |
**send_payment_instruction_email** | **bool** | Whether payment instruction emails are sent to customers for this merchant. Omitted for &#x60;payout&#x60;-role merchants. | [optional]
**send_payment_receipt_email** | **bool** | Whether payment receipt emails are sent to customers for this merchant. Omitted for &#x60;payout&#x60;-role merchants. | [optional]
**send_payment_reminder_email** | **bool** | Whether payment reminder emails are sent to customers for this merchant. Omitted for &#x60;payout&#x60;-role merchants. | [optional]
**send_payment_refund_email** | **bool** | Whether refund notification emails are sent to customers for this merchant. Omitted for &#x60;payout&#x60;-role merchants. | [optional]
**expiry_settings** | [**\Komoju\Model\SerializedSubmerchantExpirySettingsInner[]**](SerializedSubmerchantExpirySettingsInner.md) |  |
**active_payment_methods** | [**\Komoju\Model\SerializedSubmerchantActivePaymentMethodsInner[]**](SerializedSubmerchantActivePaymentMethodsInner.md) |  |
**publishable_key** | **string** | The merchant&#39;s publishable API key for client-side use. |
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
