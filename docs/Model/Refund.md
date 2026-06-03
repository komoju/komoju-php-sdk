# # Refund
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** | A unique 25-character alphanumeric refund identifier. |
**resource** | **string** | Resource name. Will always be &#x60;refund&#x60;. |
**amount** | **int** | The refund amount with tax included, greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**currency** | [**\Komoju\Model\Currency**](Currency.md) |  |
**payment** | **string** | A unique 25-character alphanumeric payment identifier. |
**description** | **string** | Description of the refund. |
**created_at** | **\DateTime** |  |
**chargeback** | **bool** | Denotes if this refund was created due to a chargeback. |
**refund_type** | **string** |  | [optional]
**platform_details** | [**\Komoju\Model\PlatformDetails**](PlatformDetails.md) |  | [optional]
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
