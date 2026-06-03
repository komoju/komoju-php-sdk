# Komoju\PaymentsApi

All URIs are relative to https://komoju.com/api/v1, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**cancelPayment()**](PaymentsApi.md#cancelPayment) | **POST** /payments/{id}/cancel | Payment: Cancel |
| [**capturePayment()**](PaymentsApi.md#capturePayment) | **POST** /payments/{id}/capture | Payment: Capture |
| [**createPayment()**](PaymentsApi.md#createPayment) | **POST** /payments | Payment: Create |
| [**createRefundRequest()**](PaymentsApi.md#createRefundRequest) | **POST** /payments/{id}/refund_request | Payment: Refund Request |
| [**finalizePayment()**](PaymentsApi.md#finalizePayment) | **POST** /payments/{id}/finalize | Payment: Finalize |
| [**listPaymentMethods()**](PaymentsApi.md#listPaymentMethods) | **GET** /payment_methods | Payment Method: List |
| [**listPayments()**](PaymentsApi.md#listPayments) | **GET** /payments | Payment: List |
| [**refundPayment()**](PaymentsApi.md#refundPayment) | **POST** /payments/{id}/refund | Payment: Refund |
| [**showPayment()**](PaymentsApi.md#showPayment) | **GET** /payments/{id} | Payment: Show |
| [**updatePayment()**](PaymentsApi.md#updatePayment) | **PATCH** /payments/{id} | Payment: Update |


## Request Models


- [**\Komoju\Model\CapturePaymentRequest**](../Model/CapturePaymentRequest.md) — used by `capturePayment`

- [**\Komoju\Model\CreatePaymentRequest**](../Model/CreatePaymentRequest.md) — used by `createPayment`

- [**\Komoju\Model\CreateRefundRequestRequest**](../Model/CreateRefundRequestRequest.md) — used by `createRefundRequest`

- [**\Komoju\Model\FinalizePaymentRequest**](../Model/FinalizePaymentRequest.md) — used by `finalizePayment`

- [**\Komoju\Model\RefundPaymentRequest**](../Model/RefundPaymentRequest.md) — used by `refundPayment`

- [**\Komoju\Model\UpdatePaymentRequest**](../Model/UpdatePaymentRequest.md) — used by `updatePayment`




## `cancelPayment()`

```php
cancelPayment($id): \Komoju\Model\Payment
```

Payment: Cancel

Cancels a payment.  The given payment must have a state of `pending` or `authorized` in order to be canceled.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PaymentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string | A unique identifier for the payment.

try {
    $result = $apiInstance->cancelPayment($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PaymentsApi->cancelPayment: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**| A unique identifier for the payment. | |

### Return type

[**\Komoju\Model\Payment**](../Model/Payment.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `capturePayment()`

```php
capturePayment($id, $capture_payment_request): \Komoju\Model\Payment
```

Payment: Capture

Captures a payment.  Only works when the payment was created with `capture` set to false, or via a session with `capture` set to `\"manual\"`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PaymentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string | A unique identifier for the payment.
$capture_payment_request = new \Komoju\Model\CapturePaymentRequest(); // \Komoju\Model\CapturePaymentRequest

try {
    $result = $apiInstance->capturePayment($id, $capture_payment_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PaymentsApi->capturePayment: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**| A unique identifier for the payment. | |
| **capture_payment_request** | [**\Komoju\Model\CapturePaymentRequest**](../Model/CapturePaymentRequest.md)|  | |

### Return type

[**\Komoju\Model\Payment**](../Model/Payment.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createPayment()`

```php
createPayment($create_payment_request): \Komoju\Model\Payment
```

Payment: Create

Creates a payment for a given `amount` and `currency`.  There are two ways to create payment:  - For one-time payment, you can pass `payment_details` with payment method type and additional attributes. - For recurring payment, you can pass customer's ID via `customer` attribute. Customer's saved payment method will be used for the payment.  Note that either `payment_details` or `customer` is required for the payment. However, both of them should not be given at the same time.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PaymentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_payment_request = new \Komoju\Model\CreatePaymentRequest(); // \Komoju\Model\CreatePaymentRequest

try {
    $result = $apiInstance->createPayment($create_payment_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PaymentsApi->createPayment: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_payment_request** | [**\Komoju\Model\CreatePaymentRequest**](../Model/CreatePaymentRequest.md)|  | |

### Return type

[**\Komoju\Model\Payment**](../Model/Payment.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createRefundRequest()`

```php
createRefundRequest($id, $create_refund_request_request)
```

Payment: Refund Request

A \"Refund Request\" requests that a payment be refunded manually. This can be used for payment methods that do not support refunds, such as konbini. To support non-refundable payment methods, a bank account must be specified so that we know where to send the funds. Since it is a manual process, the refund will be carried out at a later date, and there's a possibility of it being rejected.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PaymentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string | A unique identifier for the payment.
$create_refund_request_request = new \Komoju\Model\CreateRefundRequestRequest(); // \Komoju\Model\CreateRefundRequestRequest

try {
    $apiInstance->createRefundRequest($id, $create_refund_request_request);
} catch (Exception $e) {
    echo 'Exception when calling PaymentsApi->createRefundRequest: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**| A unique identifier for the payment. | |
| **create_refund_request_request** | [**\Komoju\Model\CreateRefundRequestRequest**](../Model/CreateRefundRequestRequest.md)|  | |

### Return type

void (empty response body)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `finalizePayment()`

```php
finalizePayment($id, $finalize_payment_request): \Komoju\Model\Payment
```

Payment: Finalize

Finalizes a payment.  Finalizes an EMV contact transaction by confirming the chip card's final decision (TC for approved, AAC for declined). Use this after authorization to submit the terminal's transaction outcome and determine whether the payment is captured or cancelled.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PaymentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string | A unique identifier for the payment.
$finalize_payment_request = new \Komoju\Model\FinalizePaymentRequest(); // \Komoju\Model\FinalizePaymentRequest

try {
    $result = $apiInstance->finalizePayment($id, $finalize_payment_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PaymentsApi->finalizePayment: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**| A unique identifier for the payment. | |
| **finalize_payment_request** | [**\Komoju\Model\FinalizePaymentRequest**](../Model/FinalizePaymentRequest.md)|  | |

### Return type

[**\Komoju\Model\Payment**](../Model/Payment.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listPaymentMethods()`

```php
listPaymentMethods(): \Komoju\Model\AvailablePaymentMethod[]
```

Payment Method: List

Lists available payment methods.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PaymentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->listPaymentMethods();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PaymentsApi->listPaymentMethods: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Komoju\Model\AvailablePaymentMethod[]**](../Model/AvailablePaymentMethod.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listPayments()`

```php
listPayments($start_time, $end_time, $per_page, $page, $merchant_id, $currency, $external_order_num, $status): \Komoju\Model\PaymentList
```

Payment: List

Retrieves a paginated list of payments. Pagination can be configured with `page` and `per_page` parameters.  Payments can be filtered by `currency`, `external_order_num`, and `status`.  A time range can be specified with `start_time`, and `end_time`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PaymentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$start_time = new \DateTime("2013-10-20T19:20:30+01:00"); // \DateTime | Query for records created after this time.
$end_time = new \DateTime("2013-10-20T19:20:30+01:00"); // \DateTime | Query for records created before this time.
$per_page = 56; // int | How many objects per page.
$page = 56; // int | Page number to query for.
$merchant_id = 'merchant_id_example'; // string
$currency = new \Komoju\Model\\Komoju\Model\Currency(); // \Komoju\Model\Currency
$external_order_num = 'external_order_num_example'; // string | A unique ID from your application used to track this payment.
$status = pending,captured; // string | The status of the payment. Can be a single status or comma-separated values.

try {
    $result = $apiInstance->listPayments($start_time, $end_time, $per_page, $page, $merchant_id, $currency, $external_order_num, $status);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PaymentsApi->listPayments: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **start_time** | **\DateTime**| Query for records created after this time. | [optional] |
| **end_time** | **\DateTime**| Query for records created before this time. | [optional] |
| **per_page** | **int**| How many objects per page. | [optional] |
| **page** | **int**| Page number to query for. | [optional] |
| **merchant_id** | **string**|  | [optional] |
| **currency** | [**\Komoju\Model\Currency**](../Model/.md)|  | [optional] |
| **external_order_num** | **string**| A unique ID from your application used to track this payment. | [optional] |
| **status** | **string**| The status of the payment. Can be a single status or comma-separated values. | [optional] |

### Return type

[**\Komoju\Model\PaymentList**](../Model/PaymentList.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `refundPayment()`

```php
refundPayment($id, $refund_payment_request): \Komoju\Model\Payment
```

Payment: Refund

Refunds an arbitrary amount of money from an existing payment. If no amount is specified, the whole payment is refunded.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PaymentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string | A unique identifier for the payment.
$refund_payment_request = new \Komoju\Model\RefundPaymentRequest(); // \Komoju\Model\RefundPaymentRequest

try {
    $result = $apiInstance->refundPayment($id, $refund_payment_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PaymentsApi->refundPayment: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**| A unique identifier for the payment. | |
| **refund_payment_request** | [**\Komoju\Model\RefundPaymentRequest**](../Model/RefundPaymentRequest.md)|  | |

### Return type

[**\Komoju\Model\Payment**](../Model/Payment.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `showPayment()`

```php
showPayment($id): \Komoju\Model\Payment
```

Payment: Show

Retrieves a single payment object by its `id`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PaymentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string | A unique identifier for the payment.

try {
    $result = $apiInstance->showPayment($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PaymentsApi->showPayment: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**| A unique identifier for the payment. | |

### Return type

[**\Komoju\Model\Payment**](../Model/Payment.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updatePayment()`

```php
updatePayment($id, $update_payment_request): \Komoju\Model\Payment
```

Payment: Update

Updates a payment.  Only a payment's `description` and `metadata` can be changed.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PaymentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string | A unique identifier for the payment.
$update_payment_request = new \Komoju\Model\UpdatePaymentRequest(); // \Komoju\Model\UpdatePaymentRequest

try {
    $result = $apiInstance->updatePayment($id, $update_payment_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PaymentsApi->updatePayment: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**| A unique identifier for the payment. | |
| **update_payment_request** | [**\Komoju\Model\UpdatePaymentRequest**](../Model/UpdatePaymentRequest.md)|  | |

### Return type

[**\Komoju\Model\Payment**](../Model/Payment.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
