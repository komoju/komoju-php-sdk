# CreateSessionRequestWithCustomerPaymentMode
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**mode** | **string** | In &#x60;customer_payment&#x60; mode, a payment will be created and:  * If &#x60;customer_id&#x60; is omitted, a new customer will be created. * If &#x60;customer_id&#x60; is given, updated payment information will be saved to that customer. |
**amount** | **int** | Amount greater than 0, in the lowest denomination of the currency (e.g. cents for USD). |
**return_url** | **string** | Specify the URL where user will be redirected to after they have completed or aborted the session. A &#x60;session_id&#x60; will be appended to this URL as a query parameter. | [optional]
**currency** | [**\Komoju\Model\Currency**](Currency.md) |  |
**email** | **string** | Customer&#39;s email address. | [optional]
**expires_in_seconds** | **int** | Time in seconds until the session expires after being created.  The default value and upper limit are 86,400 seconds (24 hours). | [optional]
**external_customer_id** | **string** | An unique identifier of your customer. If your system has the concept of user accounts, then the ID of the current logged in user would be appropriate. | [optional]
**payment_types** | [**\Komoju\Model\PaymentType[]**](PaymentType.md) | Specify which payment types are available for this session.  By default, all activated payment methods will be available for the session if this value is omitted. | [optional]
**default_locale** | [**\Komoju\Model\Locale**](Locale.md) |  | [optional]
**line_items** | [**\Komoju\Model\LineItem[]**](LineItem.md) | Specify the line items which will be displayed on the session page. | [optional]
**metadata** | **object** | Store any additional data you want to associate with the session. The object&#39;s keys and values must be strings. Keys have a maximum length of 30 characters. Values have a maximum length of 2000 characters. | [optional]
**payment_data** | [**\Komoju\Model\PaymentDataRequest**](PaymentDataRequest.md) |  | [optional]
**customer_id** | **string** | If provided, updated payment details will be saved on the customer. | [optional]
[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
