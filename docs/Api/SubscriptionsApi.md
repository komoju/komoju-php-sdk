# Komoju\SubscriptionsApi

All URIs are relative to https://komoju.com/api/v1, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createCustomer()**](SubscriptionsApi.md#createCustomer) | **POST** /customers | Customer: Create |
| [**createSubscription()**](SubscriptionsApi.md#createSubscription) | **POST** /subscriptions | Subscription: Create |
| [**deleteCustomer()**](SubscriptionsApi.md#deleteCustomer) | **DELETE** /customers/{id} | Customer: Destroy |
| [**deleteSubscription()**](SubscriptionsApi.md#deleteSubscription) | **DELETE** /subscriptions/{id} | Subscription: Destroy |
| [**listCustomers()**](SubscriptionsApi.md#listCustomers) | **GET** /customers | Customer: List |
| [**listSubscriptions()**](SubscriptionsApi.md#listSubscriptions) | **GET** /subscriptions | Subscription: List |
| [**showCustomer()**](SubscriptionsApi.md#showCustomer) | **GET** /customers/{id} | Customer: Show |
| [**showSubscription()**](SubscriptionsApi.md#showSubscription) | **GET** /subscriptions/{id} | Subscription: Show |
| [**updateCustomer()**](SubscriptionsApi.md#updateCustomer) | **PATCH** /customers/{id} | Customer: Update |


## Request Models


- [**\Komoju\Model\CreateCustomerRequest**](../Model/CreateCustomerRequest.md) — used by `createCustomer`

- [**\Komoju\Model\CreateSubscriptionRequest**](../Model/CreateSubscriptionRequest.md) — used by `createSubscription`

- [**\Komoju\Model\UpdateCustomerRequest**](../Model/UpdateCustomerRequest.md) — used by `updateCustomer`




## `createCustomer()`

```php
createCustomer($create_customer_request): \Komoju\Model\Customer
```

Customer: Create

Creates a new customer with the specified `payment_details`. Customer payment details are stored in a secure, PCI DSS-compliant way.  Once you have a customer, you may specify the customer's `id` instead of `payment_details` when creating a payment.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\SubscriptionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_customer_request = new \Komoju\Model\CreateCustomerRequest(); // \Komoju\Model\CreateCustomerRequest

try {
    $result = $apiInstance->createCustomer($create_customer_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SubscriptionsApi->createCustomer: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_customer_request** | [**\Komoju\Model\CreateCustomerRequest**](../Model/CreateCustomerRequest.md)|  | |

### Return type

[**\Komoju\Model\Customer**](../Model/Customer.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createSubscription()`

```php
createSubscription($create_subscription_request): \Komoju\Model\Subscription
```

Subscription: Create

Create a new subscription. A subscription represents a recurring payment. Recurring payments may be on a `weekly`, `monthly`, or `yearly` basis, specified by the period parameter.  In order to create a subscription, a customer ID must be supplied. The customer object contains saved payment info, which is regularly charged by the subscription.  A subscription can't be modified once it's created. To change a subscription, you must delete it and create a new one.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\SubscriptionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_subscription_request = new \Komoju\Model\CreateSubscriptionRequest(); // \Komoju\Model\CreateSubscriptionRequest

try {
    $result = $apiInstance->createSubscription($create_subscription_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SubscriptionsApi->createSubscription: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_subscription_request** | [**\Komoju\Model\CreateSubscriptionRequest**](../Model/CreateSubscriptionRequest.md)|  | |

### Return type

[**\Komoju\Model\Subscription**](../Model/Subscription.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteCustomer()`

```php
deleteCustomer($id): \Komoju\Model\Customer
```

Customer: Destroy

Deletes the customer with the given `id`. This complete erases the stored payment details from our database.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\SubscriptionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->deleteCustomer($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SubscriptionsApi->deleteCustomer: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Komoju\Model\Customer**](../Model/Customer.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteSubscription()`

```php
deleteSubscription($id): \Komoju\Model\Subscription
```

Subscription: Destroy

Delete a subscription. Once deleted, the subscription's regular payments will stop.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\SubscriptionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->deleteSubscription($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SubscriptionsApi->deleteSubscription: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Komoju\Model\Subscription**](../Model/Subscription.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listCustomers()`

```php
listCustomers($start_time, $end_time, $per_page, $page, $expiration): \Komoju\Model\CustomerList
```

Customer: List

Retrieves a paginated list of all previously-registered customers.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\SubscriptionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$start_time = new \DateTime("2013-10-20T19:20:30+01:00"); // \DateTime | Query for records created after this time.
$end_time = new \DateTime("2013-10-20T19:20:30+01:00"); // \DateTime | Query for records created before this time.
$per_page = 56; // int | How many objects per page.
$page = 56; // int | Page number to query for.
$expiration = 'expiration_example'; // string | The expiration of the customer's credit card in MMYY format.

try {
    $result = $apiInstance->listCustomers($start_time, $end_time, $per_page, $page, $expiration);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SubscriptionsApi->listCustomers: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **start_time** | **\DateTime**| Query for records created after this time. | [optional] |
| **end_time** | **\DateTime**| Query for records created before this time. | [optional] |
| **per_page** | **int**| How many objects per page. | [optional] |
| **page** | **int**| Page number to query for. | [optional] |
| **expiration** | **string**| The expiration of the customer&#39;s credit card in MMYY format. | [optional] |

### Return type

[**\Komoju\Model\CustomerList**](../Model/CustomerList.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listSubscriptions()`

```php
listSubscriptions($start_time, $end_time, $per_page, $page): \Komoju\Model\SubscriptionList
```

Subscription: List

List existing subscriptions.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\SubscriptionsApi(
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
    $result = $apiInstance->listSubscriptions($start_time, $end_time, $per_page, $page);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SubscriptionsApi->listSubscriptions: ', $e->getMessage(), PHP_EOL;
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

[**\Komoju\Model\SubscriptionList**](../Model/SubscriptionList.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `showCustomer()`

```php
showCustomer($id): \Komoju\Model\Customer
```

Customer: Show

Retrieves customer personal information.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\SubscriptionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->showCustomer($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SubscriptionsApi->showCustomer: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Komoju\Model\Customer**](../Model/Customer.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `showSubscription()`

```php
showSubscription($id): \Komoju\Model\Subscription
```

Subscription: Show

Show an existing subscription, including its customer and scrubbed payment details.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\SubscriptionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->showSubscription($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SubscriptionsApi->showSubscription: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Komoju\Model\Subscription**](../Model/Subscription.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateCustomer()`

```php
updateCustomer($id, $update_customer_request): \Komoju\Model\Customer
```

Customer: Update

Updates the customer with the given `id`. A new set of `payment_details` may be specified.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\SubscriptionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$update_customer_request = new \Komoju\Model\UpdateCustomerRequest(); // \Komoju\Model\UpdateCustomerRequest

try {
    $result = $apiInstance->updateCustomer($id, $update_customer_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SubscriptionsApi->updateCustomer: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **update_customer_request** | [**\Komoju\Model\UpdateCustomerRequest**](../Model/UpdateCustomerRequest.md)|  | |

### Return type

[**\Komoju\Model\Customer**](../Model/Customer.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
