# # SubscriptionCustomer
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **int** | Internal numeric ID of the customer. |
**uuid** | **string** | A unique 25-character alphanumeric resource identifier. |
**merchant_id** | **int** | Internal numeric ID of the merchant. |
**created_at** | **\DateTime** | Timestamp when the customer was created. |
**updated_at** | **\DateTime** | Timestamp when the customer was last updated. |
**email** | **string** | Customer&#39;s email address, or null if not provided. |
**currency** | [**\Komoju\Model\Currency**](Currency.md) |  |
**locale** | [**\Komoju\Model\Locale**](Locale.md) |  |
**name** | **string** | Customer-defined display name, or null if not set. |
**phone** | **string** | Customer&#39;s phone number, or null if not set. |
**archived_at** | **\DateTime** | Timestamp when the customer was archived, or null if still active. |
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
