# Komoju\SessionsApi

All URIs are relative to https://komoju.com/api/v1, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**cancelSession()**](SessionsApi.md#cancelSession) | **POST** /sessions/{id}/cancel | Session: Cancel |
| [**createSession()**](SessionsApi.md#createSession) | **POST** /sessions | Session: Create |
| [**paySession()**](SessionsApi.md#paySession) | **POST** /sessions/{id}/pay | Session: Pay |
| [**showSession()**](SessionsApi.md#showSession) | **GET** /sessions/{id} | Session: Show |


## Request Models


- [**\Komoju\Model\CreateSessionRequest**](../Model/CreateSessionRequest.md) — used by `createSession`

- [**\Komoju\Model\PaySessionRequest**](../Model/PaySessionRequest.md) — used by `paySession`




## `cancelSession()`

```php
cancelSession($id): \Komoju\Model\Session
```

Session: Cancel

Cancels a session.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');

$apiInstance = new Komoju\Api\SessionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string | A unique identifier for the session.

try {
    $result = $apiInstance->cancelSession($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SessionsApi->cancelSession: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**| A unique identifier for the session. | |

### Return type

[**\Komoju\Model\Session**](../Model/Session.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createSession()`

```php
createSession($create_session_request): \Komoju\Model\Session
```

Session: Create

Creates a session. There're 3 modes for the session:  * `payment`: A payment will be created after user completed the session (default). * `customer`: A customer will be created instead of a payment, or updated if `customer_id` is given. This customer resource can then be used to perform delayed billing or subscriptions. * `customer_payment`: A payment will be created, and customer will be created or updated. You can use this mode to charge money upfront and save customer's payment details in one go.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');

$apiInstance = new Komoju\Api\SessionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_session_request = new \Komoju\Model\CreateSessionRequest(); // \Komoju\Model\CreateSessionRequest

try {
    $result = $apiInstance->createSession($create_session_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SessionsApi->createSession: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_session_request** | [**\Komoju\Model\CreateSessionRequest**](../Model/CreateSessionRequest.md)|  | |

### Return type

[**\Komoju\Model\Session**](../Model/Session.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `paySession()`

```php
paySession($id, $pay_session_request): \Komoju\Model\PaySessionResponse
```

Session: Pay

Provide customer payment details to pay for a session.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');

$apiInstance = new Komoju\Api\SessionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string | A unique identifier for the session.
$pay_session_request = new \Komoju\Model\PaySessionRequest(); // \Komoju\Model\PaySessionRequest

try {
    $result = $apiInstance->paySession($id, $pay_session_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SessionsApi->paySession: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**| A unique identifier for the session. | |
| **pay_session_request** | [**\Komoju\Model\PaySessionRequest**](../Model/PaySessionRequest.md)|  | |

### Return type

[**\Komoju\Model\PaySessionResponse**](../Model/PaySessionResponse.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `showSession()`

```php
showSession($id): \Komoju\Model\Session
```

Session: Show

Retrieves a Session given its ID.  A Session's status changes when the user completes or cancels their payment. You can listen for those events via webhooks, or use this API to poll for changes.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');

$apiInstance = new Komoju\Api\SessionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string | A unique identifier for the session.

try {
    $result = $apiInstance->showSession($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SessionsApi->showSession: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**| A unique identifier for the session. | |

### Return type

[**\Komoju\Model\Session**](../Model/Session.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
