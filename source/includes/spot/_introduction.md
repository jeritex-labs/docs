# Introduction

## API Key Setup

<!-- TODO: fix link -->

- Some endpoints will require an API Key. Please refer to [this page](https://www.jeritex.io/api-key/) regarding API key creation.
- Once API key is created, it is recommended to set IP restrictions on the key for security reasons.
- Never share your API key/secret key to ANYONE.

<aside class="warning">
 If the API keys were accidentally shared, please delete them immediately and create a new key.
</aside>

## API Key Restrictions

- After creating the API key, the default restrictions is Enable Reading.
- To **enable withdrawals via the API**, the API key restriction needs to be modified through the Jeritex UI.

## Enabling Accounts

A <code>SPOT</code> account is provided by default upon creation of a Jeritex Account.

## General API Information

- The base endpoint is: **<https://api.jeritex.io/api/v1/>**
- All endpoints return either a JSON object or array.
- All time and timestamp related fields are in milliseconds.

## Contact Us

- [Jeritex API Telegram Group](https://t.me/jeritex)
  - For any questions in sudden drop in performance with the API and/or Websockets.
  - For any general questions about the API not covered in the documentation.
