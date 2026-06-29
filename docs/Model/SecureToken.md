# SecureToken
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** | A unique 25-character alphanumeric resource identifier. |
**created_at** | **\DateTime** | Timestamp when the SecureToken was created. |
**verification_status** | **string** | Current 3DS verification status of this SecureToken. |
**authentication_url** | **string** | URL to redirect the customer to for 3DS authentication. Only present when verification_status is \&quot;NEEDS_VERIFY\&quot;. | [optional]
**three_d_secure_account** | [**\Komoju\Model\SecureTokenThreeDSecureAccount**](SecureTokenThreeDSecureAccount.md) |  | [optional]
**three_ds_auth_result** | [**\Komoju\Model\ThreeDsAuthResult**](ThreeDsAuthResult.md) |  | [optional]
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
