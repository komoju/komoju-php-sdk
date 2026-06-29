# Komoju\ChargebacksApi

All URIs are relative to https://komoju.com/api/v1, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**acceptChargebackRequest()**](ChargebacksApi.md#acceptChargebackRequest) | **POST** /chargeback_requests/{id}/accept | Chargeback: Accept |
| [**defendChargebackRequest()**](ChargebacksApi.md#defendChargebackRequest) | **POST** /chargeback_requests/{id}/defend | Chargeback: Defend |
| [**listChargebackRequests()**](ChargebacksApi.md#listChargebackRequests) | **GET** /chargeback_requests | Chargeback: List |
| [**showChargebackRequest()**](ChargebacksApi.md#showChargebackRequest) | **GET** /chargeback_requests/{id} | Chargeback: Show |


## Request Models


- [**\Komoju\Model\DefendChargebackRequestBody**](../Model/DefendChargebackRequestBody.md) — used by `defendChargebackRequest`




## `acceptChargebackRequest()`

```php
acceptChargebackRequest($id)
```

Chargeback: Accept

Accepts a chargeback, agreeing to the dispute. Takes no request body.  A chargeback can only be accepted while its status is `pending`. If the due date has passed, the request returns an error. Accepting an already-accepted chargeback returns `204` (idempotent).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');

$apiInstance = new Komoju\Api\ChargebacksApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string | The chargeback request UUID.

try {
    $apiInstance->acceptChargebackRequest($id);
} catch (Exception $e) {
    echo 'Exception when calling ChargebacksApi->acceptChargebackRequest: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**| The chargeback request UUID. | |

### Return type

void (empty response body)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `defendChargebackRequest()`

```php
defendChargebackRequest($id, $defend_chargeback_request_body)
```

Chargeback: Defend

Submits a defense against a chargeback, including supporting documentation.  A chargeback can only be defended while its status is `pending`. If the due date has passed, the request returns an error. Defending an already-defended chargeback returns `204` (idempotent). Only one defense can be created per chargeback request.  The `document.document_base64` payload must be 15 MB or less. Supported types are PDF, JPG/JPEG, PNG, and GIF; the type is inferred from the file's bytes, not the filename.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');

$apiInstance = new Komoju\Api\ChargebacksApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string | The chargeback request UUID.
$defend_chargeback_request_body = new \Komoju\Model\DefendChargebackRequestBody(); // \Komoju\Model\DefendChargebackRequestBody

try {
    $apiInstance->defendChargebackRequest($id, $defend_chargeback_request_body);
} catch (Exception $e) {
    echo 'Exception when calling ChargebacksApi->defendChargebackRequest: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**| The chargeback request UUID. | |
| **defend_chargeback_request_body** | [**\Komoju\Model\DefendChargebackRequestBody**](../Model/DefendChargebackRequestBody.md)|  | |

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

## `listChargebackRequests()`

```php
listChargebackRequests($start_time, $end_time, $per_page, $page, $status, $payment_id, $due_date_start, $due_date_end): \Komoju\Model\ChargebackRequestList
```

Chargeback: List

Retrieves a paginated list of chargeback requests for the authenticated merchant.  Results are ordered with `pending` chargebacks first, followed by non-pending chargebacks. There is no request sort parameter.  This endpoint is only available to merchants with the chargeback feature enabled; otherwise it returns `404 Not Found`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');

$apiInstance = new Komoju\Api\ChargebacksApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$start_time = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime | Query for records created after this time.
$end_time = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime | Query for records created before this time.
$per_page = 56; // int | How many objects per page.
$page = 56; // int | Page number to query for.
$status = new \Komoju\Model\\Komoju\Model\ChargebackStatus(); // \Komoju\Model\ChargebackStatus | Filter by chargeback status.
$payment_id = 'payment_id_example'; // string | Filter by the associated payment ID.
$due_date_start = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime | Lower bound (inclusive) on the chargeback's due date.
$due_date_end = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime | Upper bound (inclusive) on the chargeback's due date.

try {
    $result = $apiInstance->listChargebackRequests($start_time, $end_time, $per_page, $page, $status, $payment_id, $due_date_start, $due_date_end);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChargebacksApi->listChargebackRequests: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **start_time** | **\DateTime**| Query for records created after this time. | [optional] |
| **end_time** | **\DateTime**| Query for records created before this time. | [optional] |
| **per_page** | **int**| How many objects per page. | [optional] |
| **page** | **int**| Page number to query for. | [optional] |
| **status** | [**\Komoju\Model\ChargebackStatus**](../Model/.md)| Filter by chargeback status. | [optional] |
| **payment_id** | **string**| Filter by the associated payment ID. | [optional] |
| **due_date_start** | **\DateTime**| Lower bound (inclusive) on the chargeback&#39;s due date. | [optional] |
| **due_date_end** | **\DateTime**| Upper bound (inclusive) on the chargeback&#39;s due date. | [optional] |

### Return type

[**\Komoju\Model\ChargebackRequestList**](../Model/ChargebackRequestList.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `showChargebackRequest()`

```php
showChargebackRequest($id): \Komoju\Model\ChargebackRequestDetail
```

Chargeback: Show

Retrieves the details of a single chargeback request, including its timeline, payment, customer, and defense (if one exists).  This endpoint is only available to merchants with the chargeback feature enabled; otherwise it returns `404 Not Found`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');

$apiInstance = new Komoju\Api\ChargebacksApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string | The chargeback request UUID.

try {
    $result = $apiInstance->showChargebackRequest($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ChargebacksApi->showChargebackRequest: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**| The chargeback request UUID. | |

### Return type

[**\Komoju\Model\ChargebackRequestDetail**](../Model/ChargebackRequestDetail.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
