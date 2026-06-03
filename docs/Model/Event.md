# # Event
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** | A unique 25-character alphanumeric resource identifier. |
**type** | **string** | Event type slug (e.g. \&quot;payment.captured\&quot;, \&quot;payment.expired\&quot;). |
**resource** | **string** | Resource type name, always \&quot;event\&quot;. |
**created_at** | **\DateTime** | Timestamp when this event was created. |
**reason** | **string** | Human-readable reason or description for this event, or null. |
**data** | [**\Komoju\Model\Payment**](Payment.md) |  |
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
