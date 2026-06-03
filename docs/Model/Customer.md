# # Customer
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** | A unique 25-character alphanumeric resource identifier. |
**resource** | **string** | Resource type name, always \&quot;customer\&quot;. |
**email** | **string** | Customer&#39;s email address, or null if not provided. |
**source** | [**\Komoju\Model\CustomerSource**](CustomerSource.md) |  |
**metadata** | **object** | Arbitrary key-value metadata attached to this customer. |
**created_at** | **\DateTime** | Timestamp when the customer was created. |
**locale** | [**\Komoju\Model\Locale**](Locale.md) |  | [optional]
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
