# Changelog

## [Unreleased]

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
