# RefundRequest
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** | A unique 25-character alphanumeric refund request identifier. |
**payment** | **string** | A unique 25-character alphanumeric payment identifier. |
**customer_name** | **string** | Customer&#39;s name in half-width katakana characters. |
**bank_name** | **string** | The name of the bank that customer would like money to be deposited to. |
**bank_code** | **string** | 4-digit bank code. May be &#x60;null&#x60; if it&#39;s not given. |
**branch_name** | **string** | The name of the branch. |
**branch_number** | **string** | 3-digit branch number. |
**account_number** | **string** | 7-digit account number. |
**description** | **string** | Optional description or reason for this refund request. | [optional]
**status** | [**\Komoju\Model\RefundRequestStatus**](RefundRequestStatus.md) |  |
**created_at** | **\DateTime** | Timestamp when the refund request was created. |
**platform_details** | [**\Komoju\Model\PlatformDetails**](PlatformDetails.md) |  | [optional]
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
