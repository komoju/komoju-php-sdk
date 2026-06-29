# Changelog

## [Unreleased]

## [1.0.0] - 2026-06-29

Targets KOMOJU API version `2025-01-28`.

### Changed

- [`GET payments` endpoint] The response object for partially captured payments has been updated.

  - **Return value changes**:
    - `amount_refunded`: the refund amount for the difference between the authorized amount and captured amount is no longer included for partially captured payments.
    - `refunds`: partially captured payments no longer show a refund for the difference between the authorized amount and captured amount.

- [`POST payments` endpoint] The response object for partially captured payments has been updated.

  - **Return value changes**:
    - `amount_refunded`: the refund amount for the difference between the authorized amount and captured amount is no longer included for partially captured payments.
    - `refunds`: a refund for the difference between the authorized amount and captured amount is not shown if the payment is a partially captured payment.

- [`GET payments/:id` endpoint] The response object for a partially captured payment has been updated.

  - **Return value changes**:
    - `amount_refunded`: the refund amount for the difference between the authorized amount and captured amount is no longer included for partially captured payments.
    - `refunds`: a refund for the difference between the authorized amount and captured amount is not shown if the payment is a partially captured payment.

- [`PATCH payments/:id` endpoint] The response object for a partially captured payment has been updated.

  - **Return value changes**:
    - `amount_refunded`: the refund amount for the difference between the authorized amount and captured amount is no longer included for partially captured payments.
    - `refunds`: a refund for the difference between the authorized amount and captured amount is not shown if the payment is a partially captured payment.

- [`POST payments/:id/capture` endpoint] The response object for a partially captured payment has been updated.

  - **Return value changes**:
    - `amount_refunded`: the refund amount for the difference between the authorized amount and captured amount is no longer included for partially captured payments.
    - `refunds`: a refund for the difference between the authorized amount and captured amount is not shown if the payment is a partially captured payment.

- [`POST payments/:id/refund` endpoint] The response object for a partially captured payment has been updated.

  - **Return value changes**:
    - `amount_refunded`: the refund amount for the difference between the authorized amount and captured amount is no longer included for partially captured payments.
    - `refunds`: a refund for the difference between the authorized amount and captured amount is not shown if the payment is a partially captured payment.

- [`POST payments/:id/cancel` endpoint] The response object for a partially captured payment has been updated.

  - **Return value changes**:
    - `amount_refunded`: the refund amount for the difference between the authorized amount and captured amount is no longer included for partially captured payments.
    - `refunds`: a refund for the difference between the authorized amount and captured amount is not shown if the payment is a partially captured payment.

- [`POST payments/:id/finalize` endpoint] The response object for a partially captured payment has been updated.

    - `amount_refunded`: the refund amount for the difference between the authorized amount and captured amount is no longer included for partially captured payments.
    - `refunds`: a refund for the difference between the authorized amount and captured amount is not shown if the payment is a partially captured payment.

- [`GET merchants/{merchant_id}/payments` endpoint] The response object for a partially captured payment has been updated.

  - **Return value changes**:
    - `amount_refunded`: the refund amount for the difference between the authorized amount and captured amount is no longer included for partially captured payments.
    - `refunds`: partially captured payments no longer show a refund for the difference between the authorized amount and captured amount.

- [`GET balances/:id` endpoint] Transformed the response to a nested (2D) structure to match the Merchant dashboard's Payout Balance page.

  - **Renamed keys**: `balance_total` is now `total_balance_cents`.
  - **Removed keys**: `payment_fee_total`, `tax_total`.
  - **Structural changes**: Added new `payments`, `refunds`, `platform_model`, `corrections`, `komoju_card_charges` and `misc` sections.
    - `payments`:
      - Moved here: `payment_total` now called `captured_amount_total_cents`
      - New keys: `processing_fees_cents`
    - `refunds`:
      - Moved here:
        - `refund_total` now called `refunded_amount_total_cents`
        - `refund_fee_total` now called `refund_processing_fees_cents` and includes tax
        - `refunded_customer_fee_total` now called `refunded_customer_fees_cents` and includes tax
    - `platform_model` (only available for Platform merchants):
      - Moved here: `fund_transfer_total_cents`
      - New keys: `payment_share_total_cents`, `payment_share_refund_total_cents`, `platform_fee_total_cents`, `platform_fee_refund_total_cents`, `submerchant_management_fees_cents`.
    - `disbursements`:
      - New keys: `disbursement_amount_total_cents`, `disbursement_fee_total_cents`
    - `misc`:
      - New keys: `clearing_total_cents`, `komoju_card_discount_total_cents`, `chargeback_fixed_fee_total_cents`, `other_fee_adjustments_total_cents` (this is the sum of all fee adjustments, any misc. record types that don't belong in other sections, and/or any new types of records that impact a merchant's balance. Refer to the API reference for the exhaustive list).
    - For each section, added a `total_cents` of each of its amounts.

- [`GET settlements` endpoint] Renamed one key name, added a number of new keys, and made changes to several returned values.

  - **Renamed keys**:
    - `amount` is now `settlement_amount_cents` in order to make the key more clear and less generic.
  
  - **Added keys**:
    - NOTE: values for keys ending in `_cents` are returned as integers (not strings); any integers related to fees can be negative integers.
    - `transaction_amount_cents`
    - `fee_amount_cents`
    - `fee_tax_amount_cents`
    - `fx_currency`
    - `fx_conversion_rate`
    - `fx_conversion_amount_cents`
    - `bank_transfer_fee_amount_cents`
    - `remittance_amount_cents`

  - **Return value changes**: 
    - `status`: "automatic_pending" is now returned as "pending".
    - `settlement_amount_cents` (formerly `amount`): the value of `settlement_amount_cents` is now returned as an integer rather than a string.
    - `download`: all keys in this section (such as `csv` or `xls`) will show "null" instead of a link if the settlement is cancelled. If the settlement is not cancelled, all links will point to an updated version of the report.

- [`GET settlements/:id` endpoint] Renamed two key names, added a number of new keys, made changes to several returned values, and transformed the response to a nested (2D) structure to include details for various kinds of payments and fees.

  - **Renamed keys**:
    - `amount` is now `settlement_amount_cents` in order to make the key more clear and less generic.

  - **Removed keys**:
    - `payment_total`
    - `payment_fee_total`
    - `refund_total`
    - `refund_fee_total`
    - `refunded_customer_fee_total`
    - `correction_total`
    - `tax_total`
    - `balance_amount`
  
  - **Added keys**:
    - NOTE: values for keys ending in `_cents` are returned as integers (not strings); any integers related to fees can be negative integers.
    - `transaction_amount_cents`
    - `fee_amount_cents`
    - `fee_tax_amount_cents`
    - `fx_currency`
    - `fx_conversion_rate`
    - `fx_conversion_amount_cents`
    - `bank_transfer_fee_amount_cents`
    - `remittance_amount_cents`
    - `payments`, `refunds`, `platform_model`, `corrections`, `komoju_card_charges`, `disbursements`, `misc` sections (see `GET balances/:id` above for structure)

  - **Return value changes**: 
    - `download`: all keys in this section (such as `csv` or `xls`) will show "null" instead of a link if the settlement is cancelled. If the settlement is not cancelled, all links will point to an updated version of the report. Additionally, URLs for downloading settlement CSV and XLS files will point to a new version of the report.

  - [`GET settlements/:id/csv` endpoint] Updated format of the report.

  - [`GET settlements/:id/xls` endpoint] Updated format of the report.

## [1.0.0-beta.1] - 2026-05-26

Targets KOMOJU API version `2025-01-28`.

### Changed

- [`GET payments` endpoint] The response object for partially captured payments has been updated.

  - **Return value changes**:
    - `amount_refunded`: the refund amount for the difference between the authorized amount and captured amount is no longer included for partially captured payments.
    - `refunds`: partially captured payments no longer show a refund for the difference between the authorized amount and captured amount.

- [`POST payments` endpoint] The response object for partially captured payments has been updated.

  - **Return value changes**:
    - `amount_refunded`: the refund amount for the difference between the authorized amount and captured amount is no longer included for partially captured payments.
    - `refunds`: a refund for the difference between the authorized amount and captured amount is not shown if the payment is a partially captured payment.

- [`GET payments/:id` endpoint] The response object for a partially captured payment has been updated.

  - **Return value changes**:
    - `amount_refunded`: the refund amount for the difference between the authorized amount and captured amount is no longer included for partially captured payments.
    - `refunds`: a refund for the difference between the authorized amount and captured amount is not shown if the payment is a partially captured payment.

- [`PATCH payments/:id` endpoint] The response object for a partially captured payment has been updated.

  - **Return value changes**:
    - `amount_refunded`: the refund amount for the difference between the authorized amount and captured amount is no longer included for partially captured payments.
    - `refunds`: a refund for the difference between the authorized amount and captured amount is not shown if the payment is a partially captured payment.

- [`POST payments/:id/capture` endpoint] The response object for a partially captured payment has been updated.

  - **Return value changes**:
    - `amount_refunded`: the refund amount for the difference between the authorized amount and captured amount is no longer included for partially captured payments.
    - `refunds`: a refund for the difference between the authorized amount and captured amount is not shown if the payment is a partially captured payment.

- [`POST payments/:id/refund` endpoint] The response object for a partially captured payment has been updated.

  - **Return value changes**:
    - `amount_refunded`: the refund amount for the difference between the authorized amount and captured amount is no longer included for partially captured payments.
    - `refunds`: a refund for the difference between the authorized amount and captured amount is not shown if the payment is a partially captured payment.

- [`POST payments/:id/cancel` endpoint] The response object for a partially captured payment has been updated.

  - **Return value changes**:
    - `amount_refunded`: the refund amount for the difference between the authorized amount and captured amount is no longer included for partially captured payments.
    - `refunds`: a refund for the difference between the authorized amount and captured amount is not shown if the payment is a partially captured payment.

- [`POST payments/:id/finalize` endpoint] The response object for a partially captured payment has been updated.

    - `amount_refunded`: the refund amount for the difference between the authorized amount and captured amount is no longer included for partially captured payments.
    - `refunds`: a refund for the difference between the authorized amount and captured amount is not shown if the payment is a partially captured payment.

- [`GET merchants/{merchant_id}/payments` endpoint] The response object for a partially captured payment has been updated.

  - **Return value changes**:
    - `amount_refunded`: the refund amount for the difference between the authorized amount and captured amount is no longer included for partially captured payments.
    - `refunds`: partially captured payments no longer show a refund for the difference between the authorized amount and captured amount.

- [`GET balances/:id` endpoint] Transformed the response to a nested (2D) structure to match the Merchant dashboard's Payout Balance page.

  - **Renamed keys**: `balance_total` is now `total_balance_cents`.
  - **Removed keys**: `payment_fee_total`, `tax_total`.
  - **Structural changes**: Added new `payments`, `refunds`, `platform_model`, `corrections`, `komoju_card_charges` and `misc` sections.

- [`GET settlements` endpoint] Renamed one key name, added a number of new keys, and made changes to several returned values.

  - **Renamed keys**: `amount` is now `settlement_amount_cents`.
  - **Return value changes**: `status`: "automatic_pending" is now returned as "pending".

- [`GET settlements/:id` endpoint] Renamed two key names, added a number of new keys, made changes to several returned values, and transformed the response to a nested (2D) structure.

  - **Renamed keys**: `amount` is now `settlement_amount_cents`.
  - **Removed keys**: `payment_total`, `payment_fee_total`, `refund_total`, `refund_fee_total`, `refunded_customer_fee_total`, `correction_total`, `tax_total`, `balance_amount`.
