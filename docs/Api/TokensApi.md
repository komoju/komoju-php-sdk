# Komoju\TokensApi

All URIs are relative to https://komoju.com/api/v1, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createToken()**](TokensApi.md#createToken) | **POST** /tokens | Token: Create |


## Request Models


- [**\Komoju\Model\CreateTokenRequest**](../Model/CreateTokenRequest.md) — used by `createToken`




## `createToken()`

```php
createToken($create_token_request): \Komoju\Model\Token
```

Token: Create

Creates a token with the given `payment_details`.  It is recommended to have a client application make this request directly so that sensitive payment information (e.g. credit card number) doesn't hit your server. Receiving credit card numbers requires your business to be PCI-DSS compliant. Once you turn your customer's details into a token, the token string can safely be sent to your server and used as `payment_details` to a future KOMOJU API request.  A `currency` may be optionally specified. When `currency` is provided, KOMOJU will ensure that the payment made using the new token is in the same currency.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\TokensApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_token_request = new \Komoju\Model\CreateTokenRequest(); // \Komoju\Model\CreateTokenRequest

try {
    $result = $apiInstance->createToken($create_token_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TokensApi->createToken: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_token_request** | [**\Komoju\Model\CreateTokenRequest**](../Model/CreateTokenRequest.md)|  | |

### Return type

[**\Komoju\Model\Token**](../Model/Token.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
