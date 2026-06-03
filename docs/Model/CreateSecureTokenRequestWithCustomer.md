# # CreateSecureTokenRequestWithCustomer
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**amount** | **int** | Amount greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**currency** | [**\Komoju\Model\Currency**](Currency.md) |  |
**customer** | **string** | To use instead of &#x60;payment_details&#x60;, specify customer&#39;s identifier for this SecureToken.  This identifier can be obtained from [Customer: Create](https://doc.komoju.com/reference/createcustomer) endpoint. |
**return_url** | **string** |  |
**platform_details** | [**\Komoju\Model\ProcessingMerchant**](ProcessingMerchant.md) |  | [optional]
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
