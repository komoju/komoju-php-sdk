# Komoju\DisbursementsApi

All URIs are relative to https://komoju.com/api/v1, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**cancelDisbursement()**](DisbursementsApi.md#cancelDisbursement) | **POST** /disbursements/{id}/cancel | Disbursement: Cancel |
| [**createDisbursement()**](DisbursementsApi.md#createDisbursement) | **POST** /disbursements | Disbursement: Create |
| [**disbursementReport()**](DisbursementsApi.md#disbursementReport) | **GET** /disbursements/report | Disbursement: Report |
| [**listDisbursements()**](DisbursementsApi.md#listDisbursements) | **GET** /disbursements | Disbursement: List |
| [**showDisbursement()**](DisbursementsApi.md#showDisbursement) | **GET** /disbursements/{id} | Disbursement: Show |


## Request Models


- [**\Komoju\Model\CancelDisbursementRequest**](../Model/CancelDisbursementRequest.md) — used by `cancelDisbursement`

- [**\Komoju\Model\CreateDisbursementRequest**](../Model/CreateDisbursementRequest.md) — used by `createDisbursement`




## `cancelDisbursement()`

```php
cancelDisbursement($id, $cancel_disbursement_request): \Komoju\Model\Disbursement
```

Disbursement: Cancel

Cancels a disbursement.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\DisbursementsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$cancel_disbursement_request = new \Komoju\Model\CancelDisbursementRequest(); // \Komoju\Model\CancelDisbursementRequest

try {
    $result = $apiInstance->cancelDisbursement($id, $cancel_disbursement_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DisbursementsApi->cancelDisbursement: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **cancel_disbursement_request** | [**\Komoju\Model\CancelDisbursementRequest**](../Model/CancelDisbursementRequest.md)|  | |

### Return type

[**\Komoju\Model\Disbursement**](../Model/Disbursement.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createDisbursement()`

```php
createDisbursement($create_disbursement_request): \Komoju\Model\Disbursement
```

Disbursement: Create

Creates a new disbursement.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\DisbursementsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_disbursement_request = new \Komoju\Model\CreateDisbursementRequest(); // \Komoju\Model\CreateDisbursementRequest

try {
    $result = $apiInstance->createDisbursement($create_disbursement_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DisbursementsApi->createDisbursement: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_disbursement_request** | [**\Komoju\Model\CreateDisbursementRequest**](../Model/CreateDisbursementRequest.md)|  | |

### Return type

[**\Komoju\Model\Disbursement**](../Model/Disbursement.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `disbursementReport()`

```php
disbursementReport($start_time, $end_time, $currency, $status)
```

Disbursement: Report

View disbursements in CSV format.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\DisbursementsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$start_time = new \DateTime("2013-10-20T19:20:30+01:00"); // \DateTime
$end_time = new \DateTime("2013-10-20T19:20:30+01:00"); // \DateTime
$currency = new \Komoju\Model\\Komoju\Model\Currency(); // \Komoju\Model\Currency
$status = new \Komoju\Model\\Komoju\Model\DisbursementStatus(); // \Komoju\Model\DisbursementStatus

try {
    $apiInstance->disbursementReport($start_time, $end_time, $currency, $status);
} catch (Exception $e) {
    echo 'Exception when calling DisbursementsApi->disbursementReport: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **start_time** | **\DateTime**|  | |
| **end_time** | **\DateTime**|  | |
| **currency** | [**\Komoju\Model\Currency**](../Model/.md)|  | |
| **status** | [**\Komoju\Model\DisbursementStatus**](../Model/.md)|  | |

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

## `listDisbursements()`

```php
listDisbursements($start_time, $end_time, $per_page, $page, $currency): \Komoju\Model\DisbursementList
```

Disbursement: List

Lists disbursements.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\DisbursementsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$start_time = new \DateTime("2013-10-20T19:20:30+01:00"); // \DateTime | Query for records created after this time.
$end_time = new \DateTime("2013-10-20T19:20:30+01:00"); // \DateTime | Query for records created before this time.
$per_page = 56; // int | How many objects per page.
$page = 56; // int | Page number to query for.
$currency = new \Komoju\Model\\Komoju\Model\Currency(); // \Komoju\Model\Currency

try {
    $result = $apiInstance->listDisbursements($start_time, $end_time, $per_page, $page, $currency);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DisbursementsApi->listDisbursements: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **start_time** | **\DateTime**| Query for records created after this time. | [optional] |
| **end_time** | **\DateTime**| Query for records created before this time. | [optional] |
| **per_page** | **int**| How many objects per page. | [optional] |
| **page** | **int**| Page number to query for. | [optional] |
| **currency** | [**\Komoju\Model\Currency**](../Model/.md)|  | [optional] |

### Return type

[**\Komoju\Model\DisbursementList**](../Model/DisbursementList.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `showDisbursement()`

```php
showDisbursement($id): \Komoju\Model\Disbursement
```

Disbursement: Show

Retrieves a disbursement.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\DisbursementsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->showDisbursement($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DisbursementsApi->showDisbursement: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Komoju\Model\Disbursement**](../Model/Disbursement.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
