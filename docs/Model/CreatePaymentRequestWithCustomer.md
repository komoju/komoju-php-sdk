# # CreatePaymentRequestWithCustomer
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**amount** | **int** | The payment amount before tax, greater than or equal to 0, in the lowest denomination of the currency (e.g. cents for USD). |
**capture** | **bool** | If &#x60;false&#x60;, the payment will be authorized on success, and you must manually capture it later to secure funds.  The payment will be captured immediately if omitted. | [optional]
**description** | **string** | A description from your application for this payment. | [optional]
**tax** | [**\Komoju\Model\CreatePaymentRequestWithPaymentDetailsTax**](CreatePaymentRequestWithPaymentDetailsTax.md) |  | [optional]
**currency** | [**\Komoju\Model\Currency**](Currency.md) |  |
**external_order_num** | **string** | A unique ID from your application used to track this payment. | [optional]
**return_url** | **string** | For offsite payment methods, specify the URL where user will be redirected to after they have completed the payment. | [optional]
**cancel_url** | **string** | For offsite payment methods, specify the URL where user will be redirected to if they cancel the payment. | [optional]
**locale** | [**\Komoju\Model\Locale**](Locale.md) |  | [optional]
**metadata** | **object** | Specify a key-value map which will be stored on the payment. You can use this field to store metadata related to this payment. Keys and values must be strings. Keys have a maximum length of 30 characters. Values have a maximum length of 2000 characters. | [optional]
**mcc** | **string** | On supported merchant and supported payment methods, specify a custom Merchant Category Code (MCC) for this payment.  See [Dynamic Statement Descriptors &amp; MCCs](https://doc.komoju.com/docs/payments-with-dynamic-statement-descriptors) for more information. | [optional]
**statement_descriptor** | [**\Komoju\Model\StatementDescriptor**](StatementDescriptor.md) |  | [optional]
**fraud_details** | [**\Komoju\Model\FraudDetails**](FraudDetails.md) |  | [optional]
**platform_details** | [**\Komoju\Model\PlatformDetails**](PlatformDetails.md) |  | [optional]
**customer** | **string** | For a subscription payment, specify customer&#39;s identifier for this payment.  This identifier can be obtained from [Customer: Create](https://doc.komoju.com/reference/createcustomer) endpoint. |
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
