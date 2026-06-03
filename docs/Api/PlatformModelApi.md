# Komoju\PlatformModelApi

All URIs are relative to https://komoju.com/api/v1, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**balanceTransfer()**](PlatformModelApi.md#balanceTransfer) | **POST** /balances/{currency}/transfer | Balance: Transfer |
| [**createFile()**](PlatformModelApi.md#createFile) | **POST** /merchants/{merchant_id}/files | File: Create |
| [**createMerchant()**](PlatformModelApi.md#createMerchant) | **POST** /merchants | Merchant: Create |
| [**createMerchantBalanceTransfer()**](PlatformModelApi.md#createMerchantBalanceTransfer) | **POST** /merchants/{merchant_id}/balances/{currency}/transfer | Balance: Transfer |
| [**editMerchantBalanceSettings()**](PlatformModelApi.md#editMerchantBalanceSettings) | **PATCH** /merchants/{merchant_id}/balances/{currency}/settings | Balances: Edit Settings |
| [**listLiveApplicationPaymentMethods()**](PlatformModelApi.md#listLiveApplicationPaymentMethods) | **GET** /live_application/{merchant_id}/payment_methods | Live Application: Payment Methods |
| [**listMerchants()**](PlatformModelApi.md#listMerchants) | **GET** /merchants | Merchant: List |
| [**listSubmerchantPayments()**](PlatformModelApi.md#listSubmerchantPayments) | **GET** /merchants/{merchant_id}/payments | Payment: List for Merchant |
| [**listSubmerchantSettlements()**](PlatformModelApi.md#listSubmerchantSettlements) | **GET** /merchants/{merchant_id}/settlements | Settlement: List |
| [**merchantBalanceTransactions()**](PlatformModelApi.md#merchantBalanceTransactions) | **GET** /merchants/{merchant_id}/balances/{currency}/transactions | Balance: Transactions |
| [**showFile()**](PlatformModelApi.md#showFile) | **GET** /merchants/{merchant_id}/files/{id} | File: Show |
| [**showLiveApplication()**](PlatformModelApi.md#showLiveApplication) | **GET** /live_application/{merchant_id} | Live Application: Show |
| [**showLiveApplicationPaymentMethod()**](PlatformModelApi.md#showLiveApplicationPaymentMethod) | **GET** /live_application/{merchant_id}/payment_methods/{payment_method} | Live Application: Show Payment Method |
| [**showMerchant()**](PlatformModelApi.md#showMerchant) | **GET** /merchants/{id} | Merchant: Show |
| [**showMerchantBalance()**](PlatformModelApi.md#showMerchantBalance) | **GET** /merchants/{merchant_id}/balances/{currency} | Balance: Show |
| [**showMerchantBalanceSettings()**](PlatformModelApi.md#showMerchantBalanceSettings) | **GET** /merchants/{merchant_id}/balances/{currency}/settings | Balance: Show Settings |
| [**showMerchantBalanceTransaction()**](PlatformModelApi.md#showMerchantBalanceTransaction) | **GET** /merchants/{merchant_id}/balances/{currency}/transactions/{transaction_uuid} | Balance: Transaction |
| [**showSubmerchantSettlement()**](PlatformModelApi.md#showSubmerchantSettlement) | **GET** /merchants/{merchant_id}/settlements/{id} | Settlement: Show |
| [**simulateLiveApplicationPaymentMethodStatus()**](PlatformModelApi.md#simulateLiveApplicationPaymentMethodStatus) | **PATCH** /live_application/{merchant_id}/payment_methods/{payment_method}/simulate_status | Live Application: Simulate Payment Method Status |
| [**simulateLiveApplicationStatus()**](PlatformModelApi.md#simulateLiveApplicationStatus) | **PATCH** /live_application/{merchant_id}/simulate_status | Live Application: Simulate Status |
| [**submerchantSettlementCSV()**](PlatformModelApi.md#submerchantSettlementCSV) | **GET** /merchants/{merchant_id}/settlements/{id}/csv | Settlement: CSV |
| [**submerchantSettlementPDF()**](PlatformModelApi.md#submerchantSettlementPDF) | **GET** /merchants/{merchant_id}/settlements/{id}/pdf | Settlement: PDF |
| [**submerchantSettlementXLS()**](PlatformModelApi.md#submerchantSettlementXLS) | **GET** /merchants/{merchant_id}/settlements/{id}/xls | Settlement: XLS |
| [**updateLiveApplication()**](PlatformModelApi.md#updateLiveApplication) | **PATCH** /live_application/{merchant_id} | Live Application: Update |
| [**updateLiveApplicationPaymentMethod()**](PlatformModelApi.md#updateLiveApplicationPaymentMethod) | **PATCH** /live_application/{merchant_id}/payment_methods/{payment_method} | Live Application: Update Payment Method |
| [**updateMerchant()**](PlatformModelApi.md#updateMerchant) | **PATCH** /merchants/{id} | Merchant: Update |


## Request Models


- [**\Komoju\Model\BalanceTransferRequest**](../Model/BalanceTransferRequest.md) — used by `balanceTransfer`

- [**\Komoju\Model\CreateFileRequest**](../Model/CreateFileRequest.md) — used by `createFile`

- [**\Komoju\Model\CreateMerchantRequest**](../Model/CreateMerchantRequest.md) — used by `createMerchant`

- [**\Komoju\Model\CreateMerchantBalanceTransferRequest**](../Model/CreateMerchantBalanceTransferRequest.md) — used by `createMerchantBalanceTransfer`

- [**\Komoju\Model\EditMerchantBalanceSettingsRequest**](../Model/EditMerchantBalanceSettingsRequest.md) — used by `editMerchantBalanceSettings`

- [**\Komoju\Model\SimulateLiveApplicationPaymentMethodStatusRequest**](../Model/SimulateLiveApplicationPaymentMethodStatusRequest.md) — used by `simulateLiveApplicationPaymentMethodStatus`

- [**\Komoju\Model\SimulateLiveApplicationPaymentMethodStatusRequest**](../Model/SimulateLiveApplicationPaymentMethodStatusRequest.md) — used by `simulateLiveApplicationStatus`

- [**\Komoju\Model\LiveApplicationRequest**](../Model/LiveApplicationRequest.md) — used by `updateLiveApplication`

- [**\Komoju\Model\UpdatePaymentMethodRequest**](../Model/UpdatePaymentMethodRequest.md) — used by `updateLiveApplicationPaymentMethod`

- [**\Komoju\Model\UpdateMerchantRequest**](../Model/UpdateMerchantRequest.md) — used by `updateMerchant`




## `balanceTransfer()`

```php
balanceTransfer($currency, $balance_transfer_request): \Komoju\Model\Transfer
```

Balance: Transfer

Transfers funds from the currently authenticated merchant's balance to another associated merchant for the given `currency`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$currency = new \Komoju\Model\\Komoju\Model\Currency(); // \Komoju\Model\Currency
$balance_transfer_request = new \Komoju\Model\BalanceTransferRequest(); // \Komoju\Model\BalanceTransferRequest

try {
    $result = $apiInstance->balanceTransfer($currency, $balance_transfer_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->balanceTransfer: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **currency** | [**\Komoju\Model\Currency**](../Model/.md)|  | |
| **balance_transfer_request** | [**\Komoju\Model\BalanceTransferRequest**](../Model/BalanceTransferRequest.md)|  | |

### Return type

[**\Komoju\Model\Transfer**](../Model/Transfer.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createFile()`

```php
createFile($merchant_id, $create_file_request): \Komoju\Model\MerchantFile
```

File: Create

Creates a new file for the current merchant.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$merchant_id = 'merchant_id_example'; // string
$create_file_request = new \Komoju\Model\CreateFileRequest(); // \Komoju\Model\CreateFileRequest

try {
    $result = $apiInstance->createFile($merchant_id, $create_file_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->createFile: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **merchant_id** | **string**|  | |
| **create_file_request** | [**\Komoju\Model\CreateFileRequest**](../Model/CreateFileRequest.md)|  | |

### Return type

[**\Komoju\Model\MerchantFile**](../Model/MerchantFile.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createMerchant()`

```php
createMerchant($create_merchant_request): \Komoju\Model\SerializedSubmerchant
```

Merchant: Create

Creates a new merchant.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_merchant_request = new \Komoju\Model\CreateMerchantRequest(); // \Komoju\Model\CreateMerchantRequest

try {
    $result = $apiInstance->createMerchant($create_merchant_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->createMerchant: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_merchant_request** | [**\Komoju\Model\CreateMerchantRequest**](../Model/CreateMerchantRequest.md)|  | |

### Return type

[**\Komoju\Model\SerializedSubmerchant**](../Model/SerializedSubmerchant.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createMerchantBalanceTransfer()`

```php
createMerchantBalanceTransfer($merchant_id, $currency, $create_merchant_balance_transfer_request): \Komoju\Model\BalanceTransferServiceRecord
```

Balance: Transfer

Creates a balance transfer between associated merchants for a given `amount` and `currency`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$merchant_id = 'merchant_id_example'; // string
$currency = new \Komoju\Model\\Komoju\Model\Currency(); // \Komoju\Model\Currency
$create_merchant_balance_transfer_request = new \Komoju\Model\CreateMerchantBalanceTransferRequest(); // \Komoju\Model\CreateMerchantBalanceTransferRequest

try {
    $result = $apiInstance->createMerchantBalanceTransfer($merchant_id, $currency, $create_merchant_balance_transfer_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->createMerchantBalanceTransfer: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **merchant_id** | **string**|  | |
| **currency** | [**\Komoju\Model\Currency**](../Model/.md)|  | |
| **create_merchant_balance_transfer_request** | [**\Komoju\Model\CreateMerchantBalanceTransferRequest**](../Model/CreateMerchantBalanceTransferRequest.md)|  | |

### Return type

[**\Komoju\Model\BalanceTransferServiceRecord**](../Model/BalanceTransferServiceRecord.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `editMerchantBalanceSettings()`

```php
editMerchantBalanceSettings($merchant_id, $currency, $edit_merchant_balance_settings_request): \Komoju\Model\MerchantBalance
```

Balances: Edit Settings

Given a currency, edit the payout settings of the currently authenticated merchant or one of its sub-merchants.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$merchant_id = 'merchant_id_example'; // string
$currency = new \Komoju\Model\\Komoju\Model\Currency(); // \Komoju\Model\Currency
$edit_merchant_balance_settings_request = new \Komoju\Model\EditMerchantBalanceSettingsRequest(); // \Komoju\Model\EditMerchantBalanceSettingsRequest

try {
    $result = $apiInstance->editMerchantBalanceSettings($merchant_id, $currency, $edit_merchant_balance_settings_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->editMerchantBalanceSettings: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **merchant_id** | **string**|  | |
| **currency** | [**\Komoju\Model\Currency**](../Model/.md)|  | |
| **edit_merchant_balance_settings_request** | [**\Komoju\Model\EditMerchantBalanceSettingsRequest**](../Model/EditMerchantBalanceSettingsRequest.md)|  | |

### Return type

[**\Komoju\Model\MerchantBalance**](../Model/MerchantBalance.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listLiveApplicationPaymentMethods()`

```php
listLiveApplicationPaymentMethods($merchant_id, $locale): \Komoju\Model\PaymentMethodsList
```

Live Application: Payment Methods

List submitted/unsubmitted payment methods

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$merchant_id = 'merchant_id_example'; // string
$locale = new \Komoju\Model\\Komoju\Model\Locale(); // \Komoju\Model\Locale

try {
    $result = $apiInstance->listLiveApplicationPaymentMethods($merchant_id, $locale);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->listLiveApplicationPaymentMethods: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **merchant_id** | **string**|  | |
| **locale** | [**\Komoju\Model\Locale**](../Model/.md)|  | [optional] |

### Return type

[**\Komoju\Model\PaymentMethodsList**](../Model/PaymentMethodsList.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listMerchants()`

```php
listMerchants($start_time, $end_time, $per_page, $page, $live, $platform_role, $status, $payments_enabled, $payouts_enabled): \Komoju\Model\SubmerchantsList
```

Merchant: List

Retrieves a paginated list of sub-merchants. Results can be filtered by `live` status, `platform_role`, account `status`, and whether payments or payouts are enabled.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$start_time = new \DateTime("2013-10-20T19:20:30+01:00"); // \DateTime | Query for records created after this time.
$end_time = new \DateTime("2013-10-20T19:20:30+01:00"); // \DateTime | Query for records created before this time.
$per_page = 56; // int | How many objects per page.
$page = 56; // int | Page number to query for.
$live = True; // bool
$platform_role = new \Komoju\Model\\Komoju\Model\MerchantRole(); // \Komoju\Model\MerchantRole
$status = 'status_example'; // string
$payments_enabled = True; // bool
$payouts_enabled = True; // bool

try {
    $result = $apiInstance->listMerchants($start_time, $end_time, $per_page, $page, $live, $platform_role, $status, $payments_enabled, $payouts_enabled);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->listMerchants: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **start_time** | **\DateTime**| Query for records created after this time. | [optional] |
| **end_time** | **\DateTime**| Query for records created before this time. | [optional] |
| **per_page** | **int**| How many objects per page. | [optional] |
| **page** | **int**| Page number to query for. | [optional] |
| **live** | **bool**|  | [optional] |
| **platform_role** | [**\Komoju\Model\MerchantRole**](../Model/.md)|  | [optional] |
| **status** | **string**|  | [optional] |
| **payments_enabled** | **bool**|  | [optional] |
| **payouts_enabled** | **bool**|  | [optional] |

### Return type

[**\Komoju\Model\SubmerchantsList**](../Model/SubmerchantsList.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listSubmerchantPayments()`

```php
listSubmerchantPayments($merchant_id, $start_time, $end_time, $per_page, $page, $currency, $external_order_num, $status): \Komoju\Model\PlatformMerchantPaymentList
```

Payment: List for Merchant

Retrieves a paginated list of payments. Pagination can be configured with `page` and `per_page` parameters.  Payments can be filtered by `currency`, `external_order_num`, and `status`.  A time range can be specified with `start_time`, and `end_time`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$merchant_id = 'merchant_id_example'; // string
$start_time = new \DateTime("2013-10-20T19:20:30+01:00"); // \DateTime | Query for records created after this time.
$end_time = new \DateTime("2013-10-20T19:20:30+01:00"); // \DateTime | Query for records created before this time.
$per_page = 56; // int | How many objects per page.
$page = 56; // int | Page number to query for.
$currency = new \Komoju\Model\\Komoju\Model\Currency(); // \Komoju\Model\Currency
$external_order_num = 'external_order_num_example'; // string
$status = new \Komoju\Model\\Komoju\Model\PaymentStatus(); // \Komoju\Model\PaymentStatus

try {
    $result = $apiInstance->listSubmerchantPayments($merchant_id, $start_time, $end_time, $per_page, $page, $currency, $external_order_num, $status);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->listSubmerchantPayments: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **merchant_id** | **string**|  | |
| **start_time** | **\DateTime**| Query for records created after this time. | [optional] |
| **end_time** | **\DateTime**| Query for records created before this time. | [optional] |
| **per_page** | **int**| How many objects per page. | [optional] |
| **page** | **int**| Page number to query for. | [optional] |
| **currency** | [**\Komoju\Model\Currency**](../Model/.md)|  | [optional] |
| **external_order_num** | **string**|  | [optional] |
| **status** | [**\Komoju\Model\PaymentStatus**](../Model/.md)|  | [optional] |

### Return type

[**\Komoju\Model\PlatformMerchantPaymentList**](../Model/PlatformMerchantPaymentList.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listSubmerchantSettlements()`

```php
listSubmerchantSettlements($merchant_id): \Komoju\Model\SettlementList
```

Settlement: List

Lists out past settlements from most-recent to least-recent.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$merchant_id = 'merchant_id_example'; // string

try {
    $result = $apiInstance->listSubmerchantSettlements($merchant_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->listSubmerchantSettlements: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **merchant_id** | **string**|  | |

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

## `merchantBalanceTransactions()`

```php
merchantBalanceTransactions($merchant_id, $currency, $start_time, $end_time, $per_page, $page, $type): \Komoju\Model\BalanceTransactionList
```

Balance: Transactions

Given a currency, view the ledger transactions of the currently authenticated merchant or one of its sub-merchants. Will split ledger transactions into line items when appropriate.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$merchant_id = 'merchant_id_example'; // string
$currency = new \Komoju\Model\\Komoju\Model\Currency(); // \Komoju\Model\Currency
$start_time = new \DateTime("2013-10-20T19:20:30+01:00"); // \DateTime | Query for records created after this time.
$end_time = new \DateTime("2013-10-20T19:20:30+01:00"); // \DateTime | Query for records created before this time.
$per_page = 56; // int | How many objects per page.
$page = 56; // int | Page number to query for.
$type = 'type_example'; // string

try {
    $result = $apiInstance->merchantBalanceTransactions($merchant_id, $currency, $start_time, $end_time, $per_page, $page, $type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->merchantBalanceTransactions: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **merchant_id** | **string**|  | |
| **currency** | [**\Komoju\Model\Currency**](../Model/.md)|  | |
| **start_time** | **\DateTime**| Query for records created after this time. | [optional] |
| **end_time** | **\DateTime**| Query for records created before this time. | [optional] |
| **per_page** | **int**| How many objects per page. | [optional] |
| **page** | **int**| Page number to query for. | [optional] |
| **type** | **string**|  | [optional] |

### Return type

[**\Komoju\Model\BalanceTransactionList**](../Model/BalanceTransactionList.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `showFile()`

```php
showFile($merchant_id, $id): \Komoju\Model\MerchantFile
```

File: Show

Retrieves an existing file of the current merchant.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$merchant_id = 'merchant_id_example'; // string
$id = 'id_example'; // string

try {
    $result = $apiInstance->showFile($merchant_id, $id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->showFile: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **merchant_id** | **string**|  | |
| **id** | **string**|  | |

### Return type

[**\Komoju\Model\MerchantFile**](../Model/MerchantFile.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `showLiveApplication()`

```php
showLiveApplication($merchant_id, $locale): \Komoju\Model\LiveApplicationWithSubmittedFields
```

Live Application: Show

Shows the live application status of the applicant merchant

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$merchant_id = 'merchant_id_example'; // string
$locale = new \Komoju\Model\\Komoju\Model\Locale(); // \Komoju\Model\Locale

try {
    $result = $apiInstance->showLiveApplication($merchant_id, $locale);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->showLiveApplication: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **merchant_id** | **string**|  | |
| **locale** | [**\Komoju\Model\Locale**](../Model/.md)|  | [optional] |

### Return type

[**\Komoju\Model\LiveApplicationWithSubmittedFields**](../Model/LiveApplicationWithSubmittedFields.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `showLiveApplicationPaymentMethod()`

```php
showLiveApplicationPaymentMethod($merchant_id, $payment_method, $locale): \Komoju\Model\LiveApplicationWithSubmittedFields
```

Live Application: Show Payment Method

Shows the payment method status of the applicant merchant

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$merchant_id = 'merchant_id_example'; // string
$payment_method = 'payment_method_example'; // string
$locale = new \Komoju\Model\\Komoju\Model\Locale(); // \Komoju\Model\Locale

try {
    $result = $apiInstance->showLiveApplicationPaymentMethod($merchant_id, $payment_method, $locale);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->showLiveApplicationPaymentMethod: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **merchant_id** | **string**|  | |
| **payment_method** | **string**|  | |
| **locale** | [**\Komoju\Model\Locale**](../Model/.md)|  | [optional] |

### Return type

[**\Komoju\Model\LiveApplicationWithSubmittedFields**](../Model/LiveApplicationWithSubmittedFields.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `showMerchant()`

```php
showMerchant($id): \Komoju\Model\SerializedSubmerchant
```

Merchant: Show

Retrieves the details of a sub-merchant by its `id`, including account settings, payout configuration, and live status.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->showMerchant($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->showMerchant: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Komoju\Model\SerializedSubmerchant**](../Model/SerializedSubmerchant.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `showMerchantBalance()`

```php
showMerchantBalance($merchant_id, $currency): \Komoju\Model\BalanceShow
```

Balance: Show

Given a currency, view the unsettled balance of the currently authenticated merchant or one of its sub-merchants.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$merchant_id = 'merchant_id_example'; // string
$currency = new \Komoju\Model\\Komoju\Model\Currency(); // \Komoju\Model\Currency

try {
    $result = $apiInstance->showMerchantBalance($merchant_id, $currency);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->showMerchantBalance: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **merchant_id** | **string**|  | |
| **currency** | [**\Komoju\Model\Currency**](../Model/.md)|  | |

### Return type

[**\Komoju\Model\BalanceShow**](../Model/BalanceShow.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `showMerchantBalanceSettings()`

```php
showMerchantBalanceSettings($merchant_id, $currency): \Komoju\Model\BalanceSettings
```

Balance: Show Settings

Given a currency, view the payout settings of the currently authenticated merchant or one of its sub-merchants.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$merchant_id = 'merchant_id_example'; // string
$currency = new \Komoju\Model\\Komoju\Model\Currency(); // \Komoju\Model\Currency

try {
    $result = $apiInstance->showMerchantBalanceSettings($merchant_id, $currency);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->showMerchantBalanceSettings: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **merchant_id** | **string**|  | |
| **currency** | [**\Komoju\Model\Currency**](../Model/.md)|  | |

### Return type

[**\Komoju\Model\BalanceSettings**](../Model/BalanceSettings.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `showMerchantBalanceTransaction()`

```php
showMerchantBalanceTransaction($merchant_id, $currency, $transaction_uuid): \Komoju\Model\Transaction[]
```

Balance: Transaction

Given a currency and a transaction UUID, view the corresponding ledger transaction of the currently authenticated merchant or one of its sub-merchants. Will return one entry per line item of the transaction.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$merchant_id = 'merchant_id_example'; // string
$currency = new \Komoju\Model\\Komoju\Model\Currency(); // \Komoju\Model\Currency
$transaction_uuid = 'transaction_uuid_example'; // string

try {
    $result = $apiInstance->showMerchantBalanceTransaction($merchant_id, $currency, $transaction_uuid);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->showMerchantBalanceTransaction: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **merchant_id** | **string**|  | |
| **currency** | [**\Komoju\Model\Currency**](../Model/.md)|  | |
| **transaction_uuid** | **string**|  | |

### Return type

[**\Komoju\Model\Transaction[]**](../Model/Transaction.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `showSubmerchantSettlement()`

```php
showSubmerchantSettlement($merchant_id, $id): \Komoju\Model\SettlementShow
```

Settlement: Show

View a settlement given an `id`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$merchant_id = 'merchant_id_example'; // string
$id = 'id_example'; // string

try {
    $result = $apiInstance->showSubmerchantSettlement($merchant_id, $id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->showSubmerchantSettlement: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **merchant_id** | **string**|  | |
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

## `simulateLiveApplicationPaymentMethodStatus()`

```php
simulateLiveApplicationPaymentMethodStatus($merchant_id, $payment_method, $simulate_live_application_payment_method_status_request): \Komoju\Model\PaymentMethodStatus
```

Live Application: Simulate Payment Method Status

Simulate status change on payment method for test merchants

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$merchant_id = 'merchant_id_example'; // string
$payment_method = 'payment_method_example'; // string
$simulate_live_application_payment_method_status_request = new \Komoju\Model\SimulateLiveApplicationPaymentMethodStatusRequest(); // \Komoju\Model\SimulateLiveApplicationPaymentMethodStatusRequest

try {
    $result = $apiInstance->simulateLiveApplicationPaymentMethodStatus($merchant_id, $payment_method, $simulate_live_application_payment_method_status_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->simulateLiveApplicationPaymentMethodStatus: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **merchant_id** | **string**|  | |
| **payment_method** | **string**|  | |
| **simulate_live_application_payment_method_status_request** | [**\Komoju\Model\SimulateLiveApplicationPaymentMethodStatusRequest**](../Model/SimulateLiveApplicationPaymentMethodStatusRequest.md)|  | |

### Return type

[**\Komoju\Model\PaymentMethodStatus**](../Model/PaymentMethodStatus.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `simulateLiveApplicationStatus()`

```php
simulateLiveApplicationStatus($merchant_id, $simulate_live_application_payment_method_status_request): \Komoju\Model\MerchantSubmissionStatus
```

Live Application: Simulate Status

Simulate status change on applications for test merchants. In order for status to be changed to \"accepted,\" at least one payment method must be approved.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$merchant_id = 'merchant_id_example'; // string
$simulate_live_application_payment_method_status_request = new \Komoju\Model\SimulateLiveApplicationPaymentMethodStatusRequest(); // \Komoju\Model\SimulateLiveApplicationPaymentMethodStatusRequest

try {
    $result = $apiInstance->simulateLiveApplicationStatus($merchant_id, $simulate_live_application_payment_method_status_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->simulateLiveApplicationStatus: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **merchant_id** | **string**|  | |
| **simulate_live_application_payment_method_status_request** | [**\Komoju\Model\SimulateLiveApplicationPaymentMethodStatusRequest**](../Model/SimulateLiveApplicationPaymentMethodStatusRequest.md)|  | |

### Return type

[**\Komoju\Model\MerchantSubmissionStatus**](../Model/MerchantSubmissionStatus.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `submerchantSettlementCSV()`

```php
submerchantSettlementCSV($merchant_id, $id)
```

Settlement: CSV

View a settlement in CSV format given an `id`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$merchant_id = 'merchant_id_example'; // string
$id = 'id_example'; // string

try {
    $apiInstance->submerchantSettlementCSV($merchant_id, $id);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->submerchantSettlementCSV: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **merchant_id** | **string**|  | |
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

## `submerchantSettlementPDF()`

```php
submerchantSettlementPDF($merchant_id, $id)
```

Settlement: PDF

View a settlement in PDF format given an `id`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$merchant_id = 'merchant_id_example'; // string
$id = 'id_example'; // string

try {
    $apiInstance->submerchantSettlementPDF($merchant_id, $id);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->submerchantSettlementPDF: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **merchant_id** | **string**|  | |
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

## `submerchantSettlementXLS()`

```php
submerchantSettlementXLS($merchant_id, $id)
```

Settlement: XLS

View a settlement in XLS format given an `id`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$merchant_id = 'merchant_id_example'; // string
$id = 'id_example'; // string

try {
    $apiInstance->submerchantSettlementXLS($merchant_id, $id);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->submerchantSettlementXLS: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **merchant_id** | **string**|  | |
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

## `updateLiveApplication()`

```php
updateLiveApplication($merchant_id, $live_application_request): \Komoju\Model\LiveApplication
```

Live Application: Update

Updates the live application for the applicant merchant

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$merchant_id = 'merchant_id_example'; // string
$live_application_request = new \Komoju\Model\LiveApplicationRequest(); // \Komoju\Model\LiveApplicationRequest

try {
    $result = $apiInstance->updateLiveApplication($merchant_id, $live_application_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->updateLiveApplication: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **merchant_id** | **string**|  | |
| **live_application_request** | [**\Komoju\Model\LiveApplicationRequest**](../Model/LiveApplicationRequest.md)|  | |

### Return type

[**\Komoju\Model\LiveApplication**](../Model/LiveApplication.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateLiveApplicationPaymentMethod()`

```php
updateLiveApplicationPaymentMethod($merchant_id, $payment_method, $update_payment_method_request): \Komoju\Model\LiveApplication
```

Live Application: Update Payment Method

Update the payment method application of the applicant merchant

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$merchant_id = 'merchant_id_example'; // string
$payment_method = 'payment_method_example'; // string
$update_payment_method_request = new \Komoju\Model\UpdatePaymentMethodRequest(); // \Komoju\Model\UpdatePaymentMethodRequest

try {
    $result = $apiInstance->updateLiveApplicationPaymentMethod($merchant_id, $payment_method, $update_payment_method_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->updateLiveApplicationPaymentMethod: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **merchant_id** | **string**|  | |
| **payment_method** | **string**|  | |
| **update_payment_method_request** | [**\Komoju\Model\UpdatePaymentMethodRequest**](../Model/UpdatePaymentMethodRequest.md)|  | |

### Return type

[**\Komoju\Model\LiveApplication**](../Model/LiveApplication.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateMerchant()`

```php
updateMerchant($id, $update_merchant_request): \Komoju\Model\SerializedSubmerchant
```

Merchant: Update

Updates a sub-merchant's settings, including payment and payout toggles, email notification preferences, and payment method expiry settings.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\PlatformModelApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$update_merchant_request = new \Komoju\Model\UpdateMerchantRequest(); // \Komoju\Model\UpdateMerchantRequest

try {
    $result = $apiInstance->updateMerchant($id, $update_merchant_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PlatformModelApi->updateMerchant: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **update_merchant_request** | [**\Komoju\Model\UpdateMerchantRequest**](../Model/UpdateMerchantRequest.md)|  | |

### Return type

[**\Komoju\Model\SerializedSubmerchant**](../Model/SerializedSubmerchant.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
