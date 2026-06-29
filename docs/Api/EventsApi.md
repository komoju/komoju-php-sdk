# Komoju\EventsApi

All URIs are relative to https://komoju.com/api/v1, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**listEvents()**](EventsApi.md#listEvents) | **GET** /events | Event: List |
| [**showEvent()**](EventsApi.md#showEvent) | **GET** /events/{id} | Event Show |


## Request Models





## `listEvents()`

```php
listEvents($start_time, $end_time, $per_page, $page): \Komoju\Model\EventList
```

Event: List

Lists out past webhook events from most-recent to least-recent.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');

$apiInstance = new Komoju\Api\EventsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$start_time = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime | Query for records created after this time.
$end_time = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime | Query for records created before this time.
$per_page = 56; // int | How many objects per page.
$page = 56; // int | Page number to query for.

try {
    $result = $apiInstance->listEvents($start_time, $end_time, $per_page, $page);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EventsApi->listEvents: ', $e->getMessage(), PHP_EOL;
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

[**\Komoju\Model\EventList**](../Model/EventList.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `showEvent()`

```php
showEvent($id): \Komoju\Model\Event
```

Event Show

View an event given an `id`. Event `id`s can be saved from a webhook or found by querying all events.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure your KOMOJU API key
$config = Komoju\Configuration::getDefaultConfiguration()
              ->setApiKey('YOUR_SECRET_KEY');

$apiInstance = new Komoju\Api\EventsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string | A unique identifier for an event.

try {
    $result = $apiInstance->showEvent($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EventsApi->showEvent: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**| A unique identifier for an event. | |

### Return type

[**\Komoju\Model\Event**](../Model/Event.md)

### Authorization

[api_key](../../README.md#api_key)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
