# komoju-php-sdk

The KOMOJU PHP SDK is a full-featured PHP client for the KOMOJU Payments API, built on [Guzzle](https://github.com/guzzle/guzzle).

For a full reference of all available endpoints and models, see the [KOMOJU API Reference](https://doc.komoju.com/reference/getting-started).

## Installation
Install the package via Composer.

```bash
composer require komoju-official/komoju-sdk:^1.0.0
```

## Quick Start

```php
<?php
require_once __DIR__ . '/vendor/autoload.php';

$config = Komoju\Configuration::getDefaultConfiguration()
    ->setApiKey('YOUR_SECRET_KEY');
```

Get your API keys from the [KOMOJU Merchant Settings](https://komoju.com/merchant/settings).

## Example: Hosted Page Payment

The following example walks through a basic hosted page payment flow. For a full guide, see the [Hosted Page Integration Guide](https://doc.komoju.com/docs/hosted-page-integration-guide).

### 1. Creating a Session

When your customer is ready to pay, create a session and redirect them to the returned `session_url`.

```php
<?php
$sessionsApi = new Komoju\Api\SessionsApi(new GuzzleHttp\Client(), $config);

$session = $sessionsApi->createSession(
    new Komoju\Model\CreateSessionRequestWithPaymentMode([
        'mode'       => 'payment',
        'amount'     => 1000,
        'currency'   => 'JPY',
        'return_url' => 'https://your-site.com/orders/return',
    ])
);

header('Location: ' . $session->getSessionUrl());
```

### 2. Handling the Return URL

After the customer pays, KOMOJU redirects them back to your `return_url` with a `session_id` query param appended:

```
https://your-site.com/orders/return?session_id=xxxxx
```

Fetch the session to check the outcome:

```php
<?php
$sessionId = $_GET['session_id'];

$komojuSession = $sessionsApi->showSession($sessionId);

if ($komojuSession->getStatus() === Komoju\Model\SessionStatus::COMPLETED) {
    // payment status will be "captured", "authorized", or "pending"
    echo 'Payment ' . $komojuSession->getPayment()->getStatus();
} else {
    echo 'Payment was cancelled or failed';
}
```

### 3. Set Up Webhooks (Recommended)

It is possible that the redirect in step 2 fails, possibly due to the user closing their browser, network issues, etc. Or, that the capture will only take place later on, such as with Convenience Store payments. To account for this, we recommend setting up a [Webhook](https://doc.komoju.com/docs/webhooks) to listen for payment events such as `payment.captured`, `payment.authorized`, and `payment.cancelled`. Configure your webhook URL in the [KOMOJU Merchant Dashboard](https://komoju.com/merchant/settings).

#### Verifying Webhook Signatures

To ensure a webhook request genuinely came from KOMOJU, set a **secret token** when creating or updating the webhook. KOMOJU then signs every delivery with a SHA-256 HMAC of the raw request body in the `X-Komoju-Signature` header, which you can recompute and verify.

See [Webhooks → Secret Token](https://doc.komoju.com/docs/webhooks#secret-token) for the full explanation and code examples.

## Error Handling

All API errors throw `Komoju\ApiException`:

```php
try {
    $payment = $paymentsApi->showPayment('pay_xxx');
} catch (Komoju\ApiException $e) {
    echo $e->getCode();       // HTTP status code (e.g. 404, 422)
    echo $e->getMessage();    // Human-readable description
    print_r($e->getResponseBody()); // Full response body
}
```

## Documentation

Full API reference is auto-generated in the `docs/` directory.

All URIs are relative to *https://komoju.com/api/v1*

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*BarcodesApi* | [**showBarcode**](docs/Api/BarcodesApi.md#showbarcode) | **GET** /barcodes/{payment_id} | Barcode: Show
*ChargebacksApi* | [**acceptChargebackRequest**](docs/Api/ChargebacksApi.md#acceptchargebackrequest) | **POST** /chargeback_requests/{id}/accept | Chargeback: Accept
*ChargebacksApi* | [**defendChargebackRequest**](docs/Api/ChargebacksApi.md#defendchargebackrequest) | **POST** /chargeback_requests/{id}/defend | Chargeback: Defend
*ChargebacksApi* | [**listChargebackRequests**](docs/Api/ChargebacksApi.md#listchargebackrequests) | **GET** /chargeback_requests | Chargeback: List
*ChargebacksApi* | [**showChargebackRequest**](docs/Api/ChargebacksApi.md#showchargebackrequest) | **GET** /chargeback_requests/{id} | Chargeback: Show
*DisbursementsApi* | [**cancelDisbursement**](docs/Api/DisbursementsApi.md#canceldisbursement) | **POST** /disbursements/{id}/cancel | Disbursement: Cancel
*DisbursementsApi* | [**createDisbursement**](docs/Api/DisbursementsApi.md#createdisbursement) | **POST** /disbursements | Disbursement: Create
*DisbursementsApi* | [**disbursementReport**](docs/Api/DisbursementsApi.md#disbursementreport) | **GET** /disbursements/report | Disbursement: Report
*DisbursementsApi* | [**listDisbursements**](docs/Api/DisbursementsApi.md#listdisbursements) | **GET** /disbursements | Disbursement: List
*DisbursementsApi* | [**showDisbursement**](docs/Api/DisbursementsApi.md#showdisbursement) | **GET** /disbursements/{id} | Disbursement: Show
*EventsApi* | [**listEvents**](docs/Api/EventsApi.md#listevents) | **GET** /events | Event: List
*EventsApi* | [**showEvent**](docs/Api/EventsApi.md#showevent) | **GET** /events/{id} | Event Show
*OneClickApi* | [**deleteExternalCustomer**](docs/Api/OneClickApi.md#deleteexternalcustomer) | **DELETE** /external_customers/{id} | External Customer: Destroy
*PaymentsApi* | [**cancelPayment**](docs/Api/PaymentsApi.md#cancelpayment) | **POST** /payments/{id}/cancel | Payment: Cancel
*PaymentsApi* | [**capturePayment**](docs/Api/PaymentsApi.md#capturepayment) | **POST** /payments/{id}/capture | Payment: Capture
*PaymentsApi* | [**createPayment**](docs/Api/PaymentsApi.md#createpayment) | **POST** /payments | Payment: Create
*PaymentsApi* | [**createRefundRequest**](docs/Api/PaymentsApi.md#createrefundrequest) | **POST** /payments/{id}/refund_request | Payment: Refund Request
*PaymentsApi* | [**finalizePayment**](docs/Api/PaymentsApi.md#finalizepayment) | **POST** /payments/{id}/finalize | Payment: Finalize
*PaymentsApi* | [**listPaymentMethods**](docs/Api/PaymentsApi.md#listpaymentmethods) | **GET** /payment_methods | Payment Method: List
*PaymentsApi* | [**listPayments**](docs/Api/PaymentsApi.md#listpayments) | **GET** /payments | Payment: List
*PaymentsApi* | [**refundPayment**](docs/Api/PaymentsApi.md#refundpayment) | **POST** /payments/{id}/refund | Payment: Refund
*PaymentsApi* | [**showPayment**](docs/Api/PaymentsApi.md#showpayment) | **GET** /payments/{id} | Payment: Show
*PaymentsApi* | [**updatePayment**](docs/Api/PaymentsApi.md#updatepayment) | **PATCH** /payments/{id} | Payment: Update
*PlatformModelApi* | [**balanceTransfer**](docs/Api/PlatformModelApi.md#balancetransfer) | **POST** /balances/{currency}/transfer | Balance: Transfer
*PlatformModelApi* | [**createFile**](docs/Api/PlatformModelApi.md#createfile) | **POST** /merchants/{merchant_id}/files | File: Create
*PlatformModelApi* | [**createMerchant**](docs/Api/PlatformModelApi.md#createmerchant) | **POST** /merchants | Merchant: Create
*PlatformModelApi* | [**createMerchantBalanceTransfer**](docs/Api/PlatformModelApi.md#createmerchantbalancetransfer) | **POST** /merchants/{merchant_id}/balances/{currency}/transfer | Balance: Transfer
*PlatformModelApi* | [**editMerchantBalanceSettings**](docs/Api/PlatformModelApi.md#editmerchantbalancesettings) | **PUT** /merchants/{merchant_id}/balances/{currency}/settings | Balances: Edit Settings
*PlatformModelApi* | [**listLiveApplicationPaymentMethods**](docs/Api/PlatformModelApi.md#listliveapplicationpaymentmethods) | **GET** /live_application/{merchant_id}/payment_methods | Live Application: Payment Methods
*PlatformModelApi* | [**listMerchants**](docs/Api/PlatformModelApi.md#listmerchants) | **GET** /merchants | Merchant: List
*PlatformModelApi* | [**listSubmerchantPayments**](docs/Api/PlatformModelApi.md#listsubmerchantpayments) | **GET** /merchants/{merchant_id}/payments | Payment: List for Merchant
*PlatformModelApi* | [**listSubmerchantSettlements**](docs/Api/PlatformModelApi.md#listsubmerchantsettlements) | **GET** /merchants/{merchant_id}/settlements | Settlement: List
*PlatformModelApi* | [**merchantBalanceTransactions**](docs/Api/PlatformModelApi.md#merchantbalancetransactions) | **GET** /merchants/{merchant_id}/balances/{currency}/transactions | Balance: Transactions
*PlatformModelApi* | [**showFile**](docs/Api/PlatformModelApi.md#showfile) | **GET** /merchants/{merchant_id}/files/{id} | File: Show
*PlatformModelApi* | [**showLiveApplication**](docs/Api/PlatformModelApi.md#showliveapplication) | **GET** /live_application/{merchant_id} | Live Application: Show
*PlatformModelApi* | [**showLiveApplicationPaymentMethod**](docs/Api/PlatformModelApi.md#showliveapplicationpaymentmethod) | **GET** /live_application/{merchant_id}/payment_methods/{payment_method} | Live Application: Show Payment Method
*PlatformModelApi* | [**showMerchant**](docs/Api/PlatformModelApi.md#showmerchant) | **GET** /merchants/{id} | Merchant: Show
*PlatformModelApi* | [**showMerchantBalance**](docs/Api/PlatformModelApi.md#showmerchantbalance) | **GET** /merchants/{merchant_id}/balances/{currency} | Balance: Show
*PlatformModelApi* | [**showMerchantBalanceSettings**](docs/Api/PlatformModelApi.md#showmerchantbalancesettings) | **GET** /merchants/{merchant_id}/balances/{currency}/settings | Balance: Show Settings
*PlatformModelApi* | [**showMerchantBalanceTransaction**](docs/Api/PlatformModelApi.md#showmerchantbalancetransaction) | **GET** /merchants/{merchant_id}/balances/{currency}/transactions/{transaction_uuid} | Balance: Transaction
*PlatformModelApi* | [**showSubmerchantSettlement**](docs/Api/PlatformModelApi.md#showsubmerchantsettlement) | **GET** /merchants/{merchant_id}/settlements/{id} | Settlement: Show
*PlatformModelApi* | [**simulateLiveApplicationPaymentMethodStatus**](docs/Api/PlatformModelApi.md#simulateliveapplicationpaymentmethodstatus) | **PATCH** /live_application/{merchant_id}/payment_methods/{payment_method}/simulate_status | Live Application: Simulate Payment Method Status
*PlatformModelApi* | [**simulateLiveApplicationStatus**](docs/Api/PlatformModelApi.md#simulateliveapplicationstatus) | **PATCH** /live_application/{merchant_id}/simulate_status | Live Application: Simulate Status
*PlatformModelApi* | [**submerchantSettlementCSV**](docs/Api/PlatformModelApi.md#submerchantsettlementcsv) | **GET** /merchants/{merchant_id}/settlements/{id}/csv | Settlement: CSV
*PlatformModelApi* | [**submerchantSettlementPDF**](docs/Api/PlatformModelApi.md#submerchantsettlementpdf) | **GET** /merchants/{merchant_id}/settlements/{id}/pdf | Settlement: PDF
*PlatformModelApi* | [**submerchantSettlementXLS**](docs/Api/PlatformModelApi.md#submerchantsettlementxls) | **GET** /merchants/{merchant_id}/settlements/{id}/xls | Settlement: XLS
*PlatformModelApi* | [**updateLiveApplication**](docs/Api/PlatformModelApi.md#updateliveapplication) | **PATCH** /live_application/{merchant_id} | Live Application: Update
*PlatformModelApi* | [**updateLiveApplicationPaymentMethod**](docs/Api/PlatformModelApi.md#updateliveapplicationpaymentmethod) | **PATCH** /live_application/{merchant_id}/payment_methods/{payment_method} | Live Application: Update Payment Method
*PlatformModelApi* | [**updateMerchant**](docs/Api/PlatformModelApi.md#updatemerchant) | **PATCH** /merchants/{id} | Merchant: Update
*SecureTokensApi* | [**createSecureToken**](docs/Api/SecureTokensApi.md#createsecuretoken) | **POST** /secure_tokens | SecureToken: Create
*SecureTokensApi* | [**showSecureToken**](docs/Api/SecureTokensApi.md#showsecuretoken) | **GET** /secure_tokens/{id} | SecureToken: Show
*SessionsApi* | [**cancelSession**](docs/Api/SessionsApi.md#cancelsession) | **POST** /sessions/{id}/cancel | Session: Cancel
*SessionsApi* | [**createSession**](docs/Api/SessionsApi.md#createsession) | **POST** /sessions | Session: Create
*SessionsApi* | [**paySession**](docs/Api/SessionsApi.md#paysession) | **POST** /sessions/{id}/pay | Session: Pay
*SessionsApi* | [**showSession**](docs/Api/SessionsApi.md#showsession) | **GET** /sessions/{id} | Session: Show
*SettlementsApi* | [**balanceTransactions**](docs/Api/SettlementsApi.md#balancetransactions) | **GET** /balances/{currency}/transactions | Balance: Transactions
*SettlementsApi* | [**listSettlements**](docs/Api/SettlementsApi.md#listsettlements) | **GET** /settlements | Settlement: Index
*SettlementsApi* | [**showBalance**](docs/Api/SettlementsApi.md#showbalance) | **GET** /balances/{currency} | Balance: Show
*SettlementsApi* | [**showSettlement**](docs/Api/SettlementsApi.md#showsettlement) | **GET** /settlements/{id} | Settlement: Show
*SettlementsApi* | [**showSettlementCSV**](docs/Api/SettlementsApi.md#showsettlementcsv) | **GET** /settlements/{id}/csv | Settlement: CSV
*SettlementsApi* | [**showSettlementPDF**](docs/Api/SettlementsApi.md#showsettlementpdf) | **GET** /settlements/{id}/pdf | Settlement: PDF
*SettlementsApi* | [**showSettlementXLS**](docs/Api/SettlementsApi.md#showsettlementxls) | **GET** /settlements/{id}/xls | Settlement: XLS
*SettlementsApi* | [**showTransaction**](docs/Api/SettlementsApi.md#showtransaction) | **GET** /balances/{currency}/transactions/{transaction_uuid} | Balance: Transaction
*SubscriptionsApi* | [**createCustomer**](docs/Api/SubscriptionsApi.md#createcustomer) | **POST** /customers | Customer: Create
*SubscriptionsApi* | [**createSubscription**](docs/Api/SubscriptionsApi.md#createsubscription) | **POST** /subscriptions | Subscription: Create
*SubscriptionsApi* | [**deleteCustomer**](docs/Api/SubscriptionsApi.md#deletecustomer) | **DELETE** /customers/{id} | Customer: Destroy
*SubscriptionsApi* | [**deleteSubscription**](docs/Api/SubscriptionsApi.md#deletesubscription) | **DELETE** /subscriptions/{id} | Subscription: Destroy
*SubscriptionsApi* | [**listCustomers**](docs/Api/SubscriptionsApi.md#listcustomers) | **GET** /customers | Customer: List
*SubscriptionsApi* | [**listSubscriptions**](docs/Api/SubscriptionsApi.md#listsubscriptions) | **GET** /subscriptions | Subscription: List
*SubscriptionsApi* | [**showCustomer**](docs/Api/SubscriptionsApi.md#showcustomer) | **GET** /customers/{id} | Customer: Show
*SubscriptionsApi* | [**showSubscription**](docs/Api/SubscriptionsApi.md#showsubscription) | **GET** /subscriptions/{id} | Subscription: Show
*SubscriptionsApi* | [**updateCustomer**](docs/Api/SubscriptionsApi.md#updatecustomer) | **PATCH** /customers/{id} | Customer: Update
*TokensApi* | [**createToken**](docs/Api/TokensApi.md#createtoken) | **POST** /tokens | Token: Create


## Models

- [APIError](docs/Model/APIError.md)
- [APIErrorBody](docs/Model/APIErrorBody.md)
- [Address](docs/Model/Address.md)
- [Auto](docs/Model/Auto.md)
- [AvailablePaymentMethod](docs/Model/AvailablePaymentMethod.md)
- [Balance](docs/Model/Balance.md)
- [BalanceSettings](docs/Model/BalanceSettings.md)
- [BalanceShow](docs/Model/BalanceShow.md)
- [BalanceTransactionList](docs/Model/BalanceTransactionList.md)
- [BalanceTransferRequest](docs/Model/BalanceTransferRequest.md)
- [BalanceTransferServiceRecord](docs/Model/BalanceTransferServiceRecord.md)
- [BarcodePendingResponse](docs/Model/BarcodePendingResponse.md)
- [BarcodeReadyResponse](docs/Model/BarcodeReadyResponse.md)
- [CancelDisbursementRequest](docs/Model/CancelDisbursementRequest.md)
- [CapturePaymentRequest](docs/Model/CapturePaymentRequest.md)
- [ChargebackCustomer](docs/Model/ChargebackCustomer.md)
- [ChargebackDefense](docs/Model/ChargebackDefense.md)
- [ChargebackDefenseDocument](docs/Model/ChargebackDefenseDocument.md)
- [ChargebackDefenseRecipientInfo](docs/Model/ChargebackDefenseRecipientInfo.md)
- [ChargebackDefenseShippingInfo](docs/Model/ChargebackDefenseShippingInfo.md)
- [ChargebackPayment](docs/Model/ChargebackPayment.md)
- [ChargebackPaymentMethod](docs/Model/ChargebackPaymentMethod.md)
- [ChargebackRequestDetail](docs/Model/ChargebackRequestDetail.md)
- [ChargebackRequestList](docs/Model/ChargebackRequestList.md)
- [ChargebackRequestListItem](docs/Model/ChargebackRequestListItem.md)
- [ChargebackStatus](docs/Model/ChargebackStatus.md)
- [ChargebackTimelineEntry](docs/Model/ChargebackTimelineEntry.md)
- [CountryCode](docs/Model/CountryCode.md)
- [CreateCustomerRequest](docs/Model/CreateCustomerRequest.md)
- [CreateDisbursementRequest](docs/Model/CreateDisbursementRequest.md)
- [CreateFileRequest](docs/Model/CreateFileRequest.md)
- [CreateMerchantBalanceTransferRequest](docs/Model/CreateMerchantBalanceTransferRequest.md)
- [CreateMerchantRequest](docs/Model/CreateMerchantRequest.md)
- [CreatePaymentRequest](docs/Model/CreatePaymentRequest.md)
- [CreatePaymentRequestWithCustomer](docs/Model/CreatePaymentRequestWithCustomer.md)
- [CreatePaymentRequestWithPaymentDetails](docs/Model/CreatePaymentRequestWithPaymentDetails.md)
- [CreatePaymentRequestWithPaymentDetailsTax](docs/Model/CreatePaymentRequestWithPaymentDetailsTax.md)
- [CreateRefundRequestRequest](docs/Model/CreateRefundRequestRequest.md)
- [CreateSecureTokenRequest](docs/Model/CreateSecureTokenRequest.md)
- [CreateSecureTokenRequestWithCustomer](docs/Model/CreateSecureTokenRequestWithCustomer.md)
- [CreateSecureTokenRequestWithPaymentDetails](docs/Model/CreateSecureTokenRequestWithPaymentDetails.md)
- [CreateSessionRequest](docs/Model/CreateSessionRequest.md)
- [CreateSessionRequestWithCustomerMode](docs/Model/CreateSessionRequestWithCustomerMode.md)
- [CreateSessionRequestWithCustomerPaymentMode](docs/Model/CreateSessionRequestWithCustomerPaymentMode.md)
- [CreateSessionRequestWithPaymentMode](docs/Model/CreateSessionRequestWithPaymentMode.md)
- [CreateSubscriptionRequest](docs/Model/CreateSubscriptionRequest.md)
- [CreateTokenRequest](docs/Model/CreateTokenRequest.md)
- [Currency](docs/Model/Currency.md)
- [Customer](docs/Model/Customer.md)
- [CustomerList](docs/Model/CustomerList.md)
- [CustomerSource](docs/Model/CustomerSource.md)
- [DefendChargebackDocument](docs/Model/DefendChargebackDocument.md)
- [DefendChargebackRecipientInfo](docs/Model/DefendChargebackRecipientInfo.md)
- [DefendChargebackRequestBody](docs/Model/DefendChargebackRequestBody.md)
- [DefendChargebackShippingInfo](docs/Model/DefendChargebackShippingInfo.md)
- [DeleteExternalCustomer200Response](docs/Model/DeleteExternalCustomer200Response.md)
- [Disbursement](docs/Model/Disbursement.md)
- [DisbursementList](docs/Model/DisbursementList.md)
- [DisbursementStatus](docs/Model/DisbursementStatus.md)
- [EditMerchantBalanceSettingsRequest](docs/Model/EditMerchantBalanceSettingsRequest.md)
- [ErroredField](docs/Model/ErroredField.md)
- [Event](docs/Model/Event.md)
- [EventList](docs/Model/EventList.md)
- [Field](docs/Model/Field.md)
- [FieldFieldProperties](docs/Model/FieldFieldProperties.md)
- [FinalizePaymentRequest](docs/Model/FinalizePaymentRequest.md)
- [FraudDetails](docs/Model/FraudDetails.md)
- [IndustryType](docs/Model/IndustryType.md)
- [Installments](docs/Model/Installments.md)
- [Intent](docs/Model/Intent.md)
- [LineItem](docs/Model/LineItem.md)
- [LiveApplication](docs/Model/LiveApplication.md)
- [LiveApplicationRequest](docs/Model/LiveApplicationRequest.md)
- [LiveApplicationStatus](docs/Model/LiveApplicationStatus.md)
- [LiveApplicationWithSubmittedFields](docs/Model/LiveApplicationWithSubmittedFields.md)
- [Locale](docs/Model/Locale.md)
- [MerchantBalance](docs/Model/MerchantBalance.md)
- [MerchantData](docs/Model/MerchantData.md)
- [MerchantFile](docs/Model/MerchantFile.md)
- [MerchantRole](docs/Model/MerchantRole.md)
- [MerchantSubmissionStatus](docs/Model/MerchantSubmissionStatus.md)
- [PaySessionRequest](docs/Model/PaySessionRequest.md)
- [PaySessionResponse](docs/Model/PaySessionResponse.md)
- [Payment](docs/Model/Payment.md)
- [PaymentData](docs/Model/PaymentData.md)
- [PaymentDataRequest](docs/Model/PaymentDataRequest.md)
- [PaymentDetailsAU](docs/Model/PaymentDetailsAU.md)
- [PaymentDetailsAlipay](docs/Model/PaymentDetailsAlipay.md)
- [PaymentDetailsAlipayHK](docs/Model/PaymentDetailsAlipayHK.md)
- [PaymentDetailsAll](docs/Model/PaymentDetailsAll.md)
- [PaymentDetailsAupay](docs/Model/PaymentDetailsAupay.md)
- [PaymentDetailsBancontact](docs/Model/PaymentDetailsBancontact.md)
- [PaymentDetailsBankTransfer](docs/Model/PaymentDetailsBankTransfer.md)
- [PaymentDetailsBitCash](docs/Model/PaymentDetailsBitCash.md)
- [PaymentDetailsBlik](docs/Model/PaymentDetailsBlik.md)
- [PaymentDetailsCVS](docs/Model/PaymentDetailsCVS.md)
- [PaymentDetailsCreditCard](docs/Model/PaymentDetailsCreditCard.md)
- [PaymentDetailsCreditCardBrazil](docs/Model/PaymentDetailsCreditCardBrazil.md)
- [PaymentDetailsCreditCardKorea](docs/Model/PaymentDetailsCreditCardKorea.md)
- [PaymentDetailsCreditCardKoreaSocialId](docs/Model/PaymentDetailsCreditCardKoreaSocialId.md)
- [PaymentDetailsCreditCardTerminal](docs/Model/PaymentDetailsCreditCardTerminal.md)
- [PaymentDetailsCultureVoucher](docs/Model/PaymentDetailsCultureVoucher.md)
- [PaymentDetailsDana](docs/Model/PaymentDetailsDana.md)
- [PaymentDetailsDocomo](docs/Model/PaymentDetailsDocomo.md)
- [PaymentDetailsDokuWallet](docs/Model/PaymentDetailsDokuWallet.md)
- [PaymentDetailsDospara](docs/Model/PaymentDetailsDospara.md)
- [PaymentDetailsDragonpay](docs/Model/PaymentDetailsDragonpay.md)
- [PaymentDetailsEnets](docs/Model/PaymentDetailsEnets.md)
- [PaymentDetailsEpospay](docs/Model/PaymentDetailsEpospay.md)
- [PaymentDetailsEps](docs/Model/PaymentDetailsEps.md)
- [PaymentDetailsFpx](docs/Model/PaymentDetailsFpx.md)
- [PaymentDetailsGCash](docs/Model/PaymentDetailsGCash.md)
- [PaymentDetailsGiropay](docs/Model/PaymentDetailsGiropay.md)
- [PaymentDetailsHappyMoney](docs/Model/PaymentDetailsHappyMoney.md)
- [PaymentDetailsIdeal](docs/Model/PaymentDetailsIdeal.md)
- [PaymentDetailsKakaopay](docs/Model/PaymentDetailsKakaopay.md)
- [PaymentDetailsKonbini](docs/Model/PaymentDetailsKonbini.md)
- [PaymentDetailsMerpay](docs/Model/PaymentDetailsMerpay.md)
- [PaymentDetailsMobile](docs/Model/PaymentDetailsMobile.md)
- [PaymentDetailsMobileJapan](docs/Model/PaymentDetailsMobileJapan.md)
- [PaymentDetailsMultibanco](docs/Model/PaymentDetailsMultibanco.md)
- [PaymentDetailsMybank](docs/Model/PaymentDetailsMybank.md)
- [PaymentDetailsNarvesen](docs/Model/PaymentDetailsNarvesen.md)
- [PaymentDetailsNaverpay](docs/Model/PaymentDetailsNaverpay.md)
- [PaymentDetailsNetCash](docs/Model/PaymentDetailsNetCash.md)
- [PaymentDetailsOnlyCreditCards](docs/Model/PaymentDetailsOnlyCreditCards.md)
- [PaymentDetailsOvo](docs/Model/PaymentDetailsOvo.md)
- [PaymentDetailsPaidy](docs/Model/PaymentDetailsPaidy.md)
- [PaymentDetailsPayEasy](docs/Model/PaymentDetailsPayEasy.md)
- [PaymentDetailsPayPay](docs/Model/PaymentDetailsPayPay.md)
- [PaymentDetailsPayco](docs/Model/PaymentDetailsPayco.md)
- [PaymentDetailsPaypost](docs/Model/PaymentDetailsPaypost.md)
- [PaymentDetailsPaysafeCard](docs/Model/PaymentDetailsPaysafeCard.md)
- [PaymentDetailsPaysafeCash](docs/Model/PaymentDetailsPaysafeCash.md)
- [PaymentDetailsPaysera](docs/Model/PaymentDetailsPaysera.md)
- [PaymentDetailsPayu](docs/Model/PaymentDetailsPayu.md)
- [PaymentDetailsPerlas](docs/Model/PaymentDetailsPerlas.md)
- [PaymentDetailsPix](docs/Model/PaymentDetailsPix.md)
- [PaymentDetailsPoli](docs/Model/PaymentDetailsPoli.md)
- [PaymentDetailsPrzelewy24](docs/Model/PaymentDetailsPrzelewy24.md)
- [PaymentDetailsRakutenpay](docs/Model/PaymentDetailsRakutenpay.md)
- [PaymentDetailsSepaTransfer](docs/Model/PaymentDetailsSepaTransfer.md)
- [PaymentDetailsSofortbanking](docs/Model/PaymentDetailsSofortbanking.md)
- [PaymentDetailsSoftbank](docs/Model/PaymentDetailsSoftbank.md)
- [PaymentDetailsTNG](docs/Model/PaymentDetailsTNG.md)
- [PaymentDetailsToss](docs/Model/PaymentDetailsToss.md)
- [PaymentDetailsTruemoney](docs/Model/PaymentDetailsTruemoney.md)
- [PaymentDetailsUnionpay](docs/Model/PaymentDetailsUnionpay.md)
- [PaymentDetailsWebMoney](docs/Model/PaymentDetailsWebMoney.md)
- [PaymentDetailsWechatpay](docs/Model/PaymentDetailsWechatpay.md)
- [PaymentList](docs/Model/PaymentList.md)
- [PaymentMethod](docs/Model/PaymentMethod.md)
- [PaymentMethodApplication](docs/Model/PaymentMethodApplication.md)
- [PaymentMethodApplicationStatus](docs/Model/PaymentMethodApplicationStatus.md)
- [PaymentMethodApplicationWithSubmittedFields](docs/Model/PaymentMethodApplicationWithSubmittedFields.md)
- [PaymentMethodBrands](docs/Model/PaymentMethodBrands.md)
- [PaymentMethodInstallmentsInner](docs/Model/PaymentMethodInstallmentsInner.md)
- [PaymentMethodStatus](docs/Model/PaymentMethodStatus.md)
- [PaymentMethodsList](docs/Model/PaymentMethodsList.md)
- [PaymentStatus](docs/Model/PaymentStatus.md)
- [PaymentType](docs/Model/PaymentType.md)
- [PlatformDetails](docs/Model/PlatformDetails.md)
- [PlatformMerchantPaymentList](docs/Model/PlatformMerchantPaymentList.md)
- [PlatformPayment](docs/Model/PlatformPayment.md)
- [PrepaidCards](docs/Model/PrepaidCards.md)
- [ProcessingMerchant](docs/Model/ProcessingMerchant.md)
- [Refund](docs/Model/Refund.md)
- [RefundPaymentRequest](docs/Model/RefundPaymentRequest.md)
- [RefundRequest](docs/Model/RefundRequest.md)
- [RefundRequestStatus](docs/Model/RefundRequestStatus.md)
- [ResponsePaymentDetailsAU](docs/Model/ResponsePaymentDetailsAU.md)
- [ResponsePaymentDetailsAlipay](docs/Model/ResponsePaymentDetailsAlipay.md)
- [ResponsePaymentDetailsAlipayHK](docs/Model/ResponsePaymentDetailsAlipayHK.md)
- [ResponsePaymentDetailsAll](docs/Model/ResponsePaymentDetailsAll.md)
- [ResponsePaymentDetailsAupay](docs/Model/ResponsePaymentDetailsAupay.md)
- [ResponsePaymentDetailsBancontact](docs/Model/ResponsePaymentDetailsBancontact.md)
- [ResponsePaymentDetailsBankTransfer](docs/Model/ResponsePaymentDetailsBankTransfer.md)
- [ResponsePaymentDetailsBitCash](docs/Model/ResponsePaymentDetailsBitCash.md)
- [ResponsePaymentDetailsBlik](docs/Model/ResponsePaymentDetailsBlik.md)
- [ResponsePaymentDetailsCVS](docs/Model/ResponsePaymentDetailsCVS.md)
- [ResponsePaymentDetailsCreditCard](docs/Model/ResponsePaymentDetailsCreditCard.md)
- [ResponsePaymentDetailsCreditCardBrazil](docs/Model/ResponsePaymentDetailsCreditCardBrazil.md)
- [ResponsePaymentDetailsCreditCardKorea](docs/Model/ResponsePaymentDetailsCreditCardKorea.md)
- [ResponsePaymentDetailsCreditCardTerminal](docs/Model/ResponsePaymentDetailsCreditCardTerminal.md)
- [ResponsePaymentDetailsCultureVoucher](docs/Model/ResponsePaymentDetailsCultureVoucher.md)
- [ResponsePaymentDetailsDana](docs/Model/ResponsePaymentDetailsDana.md)
- [ResponsePaymentDetailsDocomo](docs/Model/ResponsePaymentDetailsDocomo.md)
- [ResponsePaymentDetailsDokuWallet](docs/Model/ResponsePaymentDetailsDokuWallet.md)
- [ResponsePaymentDetailsDospara](docs/Model/ResponsePaymentDetailsDospara.md)
- [ResponsePaymentDetailsDragonpay](docs/Model/ResponsePaymentDetailsDragonpay.md)
- [ResponsePaymentDetailsEnets](docs/Model/ResponsePaymentDetailsEnets.md)
- [ResponsePaymentDetailsEpospay](docs/Model/ResponsePaymentDetailsEpospay.md)
- [ResponsePaymentDetailsEps](docs/Model/ResponsePaymentDetailsEps.md)
- [ResponsePaymentDetailsFpx](docs/Model/ResponsePaymentDetailsFpx.md)
- [ResponsePaymentDetailsGCash](docs/Model/ResponsePaymentDetailsGCash.md)
- [ResponsePaymentDetailsGiropay](docs/Model/ResponsePaymentDetailsGiropay.md)
- [ResponsePaymentDetailsHappyMoney](docs/Model/ResponsePaymentDetailsHappyMoney.md)
- [ResponsePaymentDetailsIdeal](docs/Model/ResponsePaymentDetailsIdeal.md)
- [ResponsePaymentDetailsKakaopay](docs/Model/ResponsePaymentDetailsKakaopay.md)
- [ResponsePaymentDetailsKonbini](docs/Model/ResponsePaymentDetailsKonbini.md)
- [ResponsePaymentDetailsMerpay](docs/Model/ResponsePaymentDetailsMerpay.md)
- [ResponsePaymentDetailsMobile](docs/Model/ResponsePaymentDetailsMobile.md)
- [ResponsePaymentDetailsMobileJapan](docs/Model/ResponsePaymentDetailsMobileJapan.md)
- [ResponsePaymentDetailsMultibanco](docs/Model/ResponsePaymentDetailsMultibanco.md)
- [ResponsePaymentDetailsMybank](docs/Model/ResponsePaymentDetailsMybank.md)
- [ResponsePaymentDetailsNarvesen](docs/Model/ResponsePaymentDetailsNarvesen.md)
- [ResponsePaymentDetailsNaverpay](docs/Model/ResponsePaymentDetailsNaverpay.md)
- [ResponsePaymentDetailsNetCash](docs/Model/ResponsePaymentDetailsNetCash.md)
- [ResponsePaymentDetailsOvo](docs/Model/ResponsePaymentDetailsOvo.md)
- [ResponsePaymentDetailsPaidy](docs/Model/ResponsePaymentDetailsPaidy.md)
- [ResponsePaymentDetailsPayEasy](docs/Model/ResponsePaymentDetailsPayEasy.md)
- [ResponsePaymentDetailsPayPay](docs/Model/ResponsePaymentDetailsPayPay.md)
- [ResponsePaymentDetailsPayco](docs/Model/ResponsePaymentDetailsPayco.md)
- [ResponsePaymentDetailsPaypost](docs/Model/ResponsePaymentDetailsPaypost.md)
- [ResponsePaymentDetailsPaysafeCard](docs/Model/ResponsePaymentDetailsPaysafeCard.md)
- [ResponsePaymentDetailsPaysafeCash](docs/Model/ResponsePaymentDetailsPaysafeCash.md)
- [ResponsePaymentDetailsPaysera](docs/Model/ResponsePaymentDetailsPaysera.md)
- [ResponsePaymentDetailsPayu](docs/Model/ResponsePaymentDetailsPayu.md)
- [ResponsePaymentDetailsPerlas](docs/Model/ResponsePaymentDetailsPerlas.md)
- [ResponsePaymentDetailsPix](docs/Model/ResponsePaymentDetailsPix.md)
- [ResponsePaymentDetailsPoli](docs/Model/ResponsePaymentDetailsPoli.md)
- [ResponsePaymentDetailsPrzelewy24](docs/Model/ResponsePaymentDetailsPrzelewy24.md)
- [ResponsePaymentDetailsRakutenpay](docs/Model/ResponsePaymentDetailsRakutenpay.md)
- [ResponsePaymentDetailsSepaTransfer](docs/Model/ResponsePaymentDetailsSepaTransfer.md)
- [ResponsePaymentDetailsSofortbanking](docs/Model/ResponsePaymentDetailsSofortbanking.md)
- [ResponsePaymentDetailsSoftbank](docs/Model/ResponsePaymentDetailsSoftbank.md)
- [ResponsePaymentDetailsTNG](docs/Model/ResponsePaymentDetailsTNG.md)
- [ResponsePaymentDetailsToss](docs/Model/ResponsePaymentDetailsToss.md)
- [ResponsePaymentDetailsTruemoney](docs/Model/ResponsePaymentDetailsTruemoney.md)
- [ResponsePaymentDetailsUnionpay](docs/Model/ResponsePaymentDetailsUnionpay.md)
- [ResponsePaymentDetailsWebMoney](docs/Model/ResponsePaymentDetailsWebMoney.md)
- [ResponsePaymentDetailsWechatpay](docs/Model/ResponsePaymentDetailsWechatpay.md)
- [SecureToken](docs/Model/SecureToken.md)
- [SecureTokenThreeDSecureAccount](docs/Model/SecureTokenThreeDSecureAccount.md)
- [SerializedSubmerchant](docs/Model/SerializedSubmerchant.md)
- [SerializedSubmerchantActivePaymentMethodsInner](docs/Model/SerializedSubmerchantActivePaymentMethodsInner.md)
- [SerializedSubmerchantExpirySettingsInner](docs/Model/SerializedSubmerchantExpirySettingsInner.md)
- [Session](docs/Model/Session.md)
- [SessionMode](docs/Model/SessionMode.md)
- [SessionStatus](docs/Model/SessionStatus.md)
- [Settlement](docs/Model/Settlement.md)
- [SettlementDownload](docs/Model/SettlementDownload.md)
- [SettlementFrequency](docs/Model/SettlementFrequency.md)
- [SettlementList](docs/Model/SettlementList.md)
- [SettlementShow](docs/Model/SettlementShow.md)
- [SharedDetails](docs/Model/SharedDetails.md)
- [SharedDetailsCorrections](docs/Model/SharedDetailsCorrections.md)
- [SharedDetailsDisbursements](docs/Model/SharedDetailsDisbursements.md)
- [SharedDetailsMisc](docs/Model/SharedDetailsMisc.md)
- [SharedDetailsPayments](docs/Model/SharedDetailsPayments.md)
- [SharedDetailsPlatformModel](docs/Model/SharedDetailsPlatformModel.md)
- [SharedDetailsRefunds](docs/Model/SharedDetailsRefunds.md)
- [ShowBalance200Response](docs/Model/ShowBalance200Response.md)
- [ShowBarcodeResponse](docs/Model/ShowBarcodeResponse.md)
- [SimulateLiveApplicationPaymentMethodStatusRequest](docs/Model/SimulateLiveApplicationPaymentMethodStatusRequest.md)
- [StatementDescriptor](docs/Model/StatementDescriptor.md)
- [Status](docs/Model/Status.md)
- [Submerchant](docs/Model/Submerchant.md)
- [SubmerchantListItem](docs/Model/SubmerchantListItem.md)
- [SubmerchantsList](docs/Model/SubmerchantsList.md)
- [SubmittedField](docs/Model/SubmittedField.md)
- [SubmittedFieldAllOfValue](docs/Model/SubmittedFieldAllOfValue.md)
- [Subscription](docs/Model/Subscription.md)
- [SubscriptionCustomer](docs/Model/SubscriptionCustomer.md)
- [SubscriptionList](docs/Model/SubscriptionList.md)
- [SubscriptionPaymentDetails](docs/Model/SubscriptionPaymentDetails.md)
- [SubscriptionPeriod](docs/Model/SubscriptionPeriod.md)
- [TerminalError](docs/Model/TerminalError.md)
- [TerminalErrorBody](docs/Model/TerminalErrorBody.md)
- [ThreeDsAuthResult](docs/Model/ThreeDsAuthResult.md)
- [Token](docs/Model/Token.md)
- [TokenPaymentDetails](docs/Model/TokenPaymentDetails.md)
- [Transaction](docs/Model/Transaction.md)
- [Transfer](docs/Model/Transfer.md)
- [UpdateCustomerRequest](docs/Model/UpdateCustomerRequest.md)
- [UpdateMerchantRequest](docs/Model/UpdateMerchantRequest.md)
- [UpdateMerchantRequestExpirySettingsInner](docs/Model/UpdateMerchantRequestExpirySettingsInner.md)
- [UpdatePaymentMethodRequest](docs/Model/UpdatePaymentMethodRequest.md)
- [UpdatePaymentRequest](docs/Model/UpdatePaymentRequest.md)

## Authorization


Authentication schemes defined for the API:
### api_key
- **Type**: HTTP basic authentication (KOMOJU API key as username, blank password)
- Use `$config->setApiKey('YOUR_SECRET_KEY')` for convenience

## Support

- [KOMOJU Developer Documentation](https://docs.komoju.com)
- [KOMOJU Merchant Dashboard](https://komoju.com/merchant)
- For SDK issues, open an issue on GitHub
