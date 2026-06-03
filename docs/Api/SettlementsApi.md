# Komoju\SettlementsApi

All URIs are relative to https://komoju.com/api/v1, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**listSettlements()**](SettlementsApi.md#listSettlements) | **GET** /settlements | Settlement: Index |
| [**showSettlement()**](SettlementsApi.md#showSettlement) | **GET** /settlements/{id} | Settlement: Show |
| [**showSettlementCSV()**](SettlementsApi.md#showSettlementCSV) | **GET** /settlements/{id}/csv | Settlement: CSV |
| [**showSettlementPDF()**](SettlementsApi.md#showSettlementPDF) | **GET** /settlements/{id}/pdf | Settlement: PDF |
| [**showSettlementXLS()**](SettlementsApi.md#showSettlementXLS) | **GET** /settlements/{id}/xls | Settlement: XLS |
| [**showTransaction()**](SettlementsApi.md#showTransaction) | **GET** /balances/{currency}/transactions/{transaction_uuid} | Balance: Transaction |


## Request Models





## `listSettlements()`

```php
listSettlements($start_time, $end_time, $per_page, $page): \Komoju\Model\SettlementList
```

Settlement: Index

Retrieves a paginated list of settlements from most-recent to least-recent. Pagination can be configured with `page` and `per_page` parameters.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\SettlementsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$start_time = new \DateTime("2013-10-20T19:20:30+01:00"); // \DateTime | Query for records created after this time.
$end_time = new \DateTime("2013-10-20T19:20:30+01:00"); // \DateTime | Query for records created before this time.
$per_page = 56; // int | How many objects per page.
$page = 56; // int | Page number to query for.

try {
    $result = $apiInstance->listSettlements($start_time, $end_time, $per_page, $page);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SettlementsApi->listSettlements: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **start_time** | **\DateTime**| Query for records created after this time. | [optional] |
| **end_time** | **\DateTime**| Query for records created before this time. | [optional] |
| **per_page** | **int**| How many objects per page. | [optional] |
| **page** | **int**| Page number to query for. | [optional] |

### Return type

[**\Komoju\Model\SettlementList**](../Model/SettlementList.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `showSettlement()`

```php
showSettlement($id): \Komoju\Model\SettlementShow
```

Settlement: Show

Retrieves a single settlement by its `id`, including a breakdown of payments, refunds, fees, corrections, and disbursements.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\SettlementsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->showSettlement($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SettlementsApi->showSettlement: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Komoju\Model\SettlementShow**](../Model/SettlementShow.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `showSettlementCSV()`

```php
showSettlementCSV($id)
```

Settlement: CSV

Retrieves the settlement in CSV format.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\SettlementsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $apiInstance->showSettlementCSV($id);
} catch (Exception $e) {
    echo 'Exception when calling SettlementsApi->showSettlementCSV: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

void (empty response body)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `showSettlementPDF()`

```php
showSettlementPDF($id)
```

Settlement: PDF

Retrieves the settlement in PDF format.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\SettlementsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $apiInstance->showSettlementPDF($id);
} catch (Exception $e) {
    echo 'Exception when calling SettlementsApi->showSettlementPDF: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

void (empty response body)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `showSettlementXLS()`

```php
showSettlementXLS($id)
```

Settlement: XLS

Retrieves the settlement in XLS format.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\SettlementsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $apiInstance->showSettlementXLS($id);
} catch (Exception $e) {
    echo 'Exception when calling SettlementsApi->showSettlementXLS: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

void (empty response body)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `showTransaction()`

```php
showTransaction($currency, $transaction_uuid): \Komoju\Model\Transaction
```

Balance: Transaction

Retrieves a single ledger transaction by its UUID for the given currency.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\SettlementsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$currency = new \Komoju\Model\\Komoju\Model\Currency(); // \Komoju\Model\Currency
$transaction_uuid = 'transaction_uuid_example'; // string

try {
    $result = $apiInstance->showTransaction($currency, $transaction_uuid);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SettlementsApi->showTransaction: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **currency** | [**\Komoju\Model\Currency**](../Model/.md)|  | |
| **transaction_uuid** | **string**|  | |

### Return type

[**\Komoju\Model\Transaction**](../Model/Transaction.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
