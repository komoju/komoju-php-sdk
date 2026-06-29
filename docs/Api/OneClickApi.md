# Komoju\OneClickApi

All URIs are relative to https://komoju.com/api/v1, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**deleteExternalCustomer()**](OneClickApi.md#deleteExternalCustomer) | **DELETE** /external_customers/{id} | External Customer: Destroy |


## Request Models





## `deleteExternalCustomer()`

```php
deleteExternalCustomer($id): \Komoju\Model\DeleteExternalCustomer200Response
```

External Customer: Destroy

Deletes the external customer created by the Hosted Page One-Click feature with the given `id`. This completely erases the stored payment details from our database.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');

$apiInstance = new Komoju\Api\OneClickApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->deleteExternalCustomer($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OneClickApi->deleteExternalCustomer: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Komoju\Model\DeleteExternalCustomer200Response**](../Model/DeleteExternalCustomer200Response.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
