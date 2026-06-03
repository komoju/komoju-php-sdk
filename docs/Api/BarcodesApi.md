# Komoju\BarcodesApi

All URIs are relative to https://komoju.com/api/v1, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**showBarcode()**](BarcodesApi.md#showBarcode) | **GET** /barcodes/{payment_id} | Barcode: Show |


## Request Models





## `showBarcode()`

```php
showBarcode($payment_id): \Komoju\Model\ShowBarcodeResponse
```

Barcode: Show

Fetches the latest barcode for a konbini payment.  Barcodes can be displayed in your client application to give your customers a more convenient way to pay. Not all konbini payments are compatible with barcodes. If a payment is compatible, it will have a `barcode_url` field in its `payment_details` object, which is a reference to this endpoint.  Newly created payments may not have a barcode available immediately. If the barcode is still being generated, the response will have a `status` of `pending` and a `retry_after` field indicating how many seconds to wait before you may retry the request.  The barcodes can only be used for payment for a limited amount of time, by default this is 10 minutes. Subsequent requests to this endpoint will return the same barcode as long as it is still valid. After expiration, a new barcode will be generated and returned.  <details> <summary>Fetching barcodes in JavaScript</summary>  If you're integrating barcodes on your website, the following JavaScript function can be used to fetch barcode data, handling the pending status and retrying. The `barcode_url` parameter is returned from Payments APIs when the payment is compatible with barcodes.  ```javascript async function fetchBarcode(barcode_url) {   const response = await fetch(barcode_url);   if (!response.ok) {     throw new Error(       `Error fetching barcode: ${response.status} ${response.statusText}`     );   }    const { status, retry_after, ...barcode } = await response.json();   if (status === 'ready') {     return barcode;   } else if (status === 'pending') {     await new Promise(resolve => setTimeout(resolve, retry_after * 1000));     return fetchBarcode(barcode_url);   } else {     throw new Error(`Error fetching barcode: unexpected status ${status}`);   } } ``` </details>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');


$apiInstance = new Komoju\Api\BarcodesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$payment_id = 'payment_id_example'; // string | Payment unique identifier

try {
    $result = $apiInstance->showBarcode($payment_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BarcodesApi->showBarcode: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **payment_id** | **string**| Payment unique identifier | |

### Return type

[**\Komoju\Model\ShowBarcodeResponse**](../Model/ShowBarcodeResponse.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
