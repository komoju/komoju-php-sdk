# Komoju\SecureTokensApi

All URIs are relative to https://komoju.com/api/v1, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createSecureToken()**](SecureTokensApi.md#createSecureToken) | **POST** /secure_tokens | SecureToken: Create |
| [**showSecureToken()**](SecureTokensApi.md#showSecureToken) | **GET** /secure_tokens/{id} | SecureToken: Show |


## Request Models


- [**\Komoju\Model\CreateSecureTokenRequest**](../Model/CreateSecureTokenRequest.md) — used by `createSecureToken`




## `createSecureToken()`

```php
createSecureToken($create_secure_token_request): \Komoju\Model\SecureToken
```

SecureToken: Create

Creates a SecureToken with the given credit card `payment_details` or `customer` ID.  There are two ways to create a SecureToken:  - Using `payment_details` with credit card information. - Using `customer` ID, which is a unique identifier for a customer created via the [Customer: Create](https://doc.komoju.com/reference/createcustomer) endpoint. Customer's saved payment details will be used as `payment_details`.  It is recommended to have a client application make this request directly so that sensitive payment information (e.g. credit card number) doesn't hit your server. Receiving credit card numbers requires your business to be PCI-DSS compliant. Once you create a secure token using a customer's credit card details, you can redirect the customer to the authentication url to perform 3DS authentication. Once a secure token has been authenticated, the secure token id can safely be sent to your server and used as `payment_details` to a future KOMOJU API request.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');

$apiInstance = new Komoju\Api\SecureTokensApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_secure_token_request = new \Komoju\Model\CreateSecureTokenRequest(); // \Komoju\Model\CreateSecureTokenRequest

try {
    $result = $apiInstance->createSecureToken($create_secure_token_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SecureTokensApi->createSecureToken: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_secure_token_request** | [**\Komoju\Model\CreateSecureTokenRequest**](../Model/CreateSecureTokenRequest.md)|  | |

### Return type

[**\Komoju\Model\SecureToken**](../Model/SecureToken.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `showSecureToken()`

```php
showSecureToken($id): \Komoju\Model\SecureToken
```

SecureToken: Show

Retrieves a single SecureToken object by its `id`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');

$apiInstance = new Komoju\Api\SecureTokensApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string | A unique identifier for the SecureToken.

try {
    $result = $apiInstance->showSecureToken($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SecureTokensApi->showSecureToken: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**| A unique identifier for the SecureToken. | |

### Return type

[**\Komoju\Model\SecureToken**](../Model/SecureToken.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
