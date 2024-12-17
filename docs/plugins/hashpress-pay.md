# HashPress Pay

HashPress Pay allows users to integrate Hedera transactions into their WordPress websites and WooCommerce shops.

## Dependencies

-   [HashPress Core](/plugins/hashpress-core) — Small but essential plugin for establishing wallet connections.

## Recommended Plugins

-   [Advanced Custom Fields PRO](https://www.advancedcustomfields.com/pro/) — HashPress Pay adds an ACF Gutenberg block
-   [WooCommerce](https://woocommerce.com/) — HashPress Pay adds (optional) WooCommerce Payment Gateways.

## Installation

1. Download the plugin as a ZIP file from its [repository](https://github.com/louweal/hashpress-pay).
2. Go to `Plugins` section in WordPress
3. Click `Add New Plugin`
4. Click `Upload Plugin`
5. Upload the ZIP file
6. Click `Activate`

## Configuration

No configuration needed, just make sure that you did the [configuration](/hashpress-core#configuration) for HashPress Core.

### WooCommerce

If you want to use HashPress Pay inside WooCommerce shop, configure its settings by going to `WooCommerce` **>** `Settings` **>** `Payments`.

## Shortcodes

### `[hashpress_pay]`

Adds a transaction button for sending transactions on Hedera. It uses [WalletConnect](https://walletconnect.com/) to establish a a secure connection with cryptocurrency wallets.

> The button has a small badge in the top right corner when the active network is `testnet` or `previewnet` to warn the user/developer that the code isn't running on the mainnet.

| Attribute | Description                                   | Default value |
| :-------- | :-------------------------------------------- | :------------ |
| title     | Button text                                   | Pay           |
| amount    | Amount to be send in _currency_ (see details) | null          |
| currency  | Currency the _amount_ is in (see details)     | USD           |
| memo      | Message to send along with the transaction    | null          |
| wallet    | Receiver Account ID - Required                | null          |
| accepts   | ...                                           | HBAR          |

**Currency**

The following currencies are supported: `USD` `EUR` `JPY` `GBP` `AUD` `CAD` `CNY` `INR` `BRL` `ZAR` `CHF` `RUB` `NZD` `MXN` `SGD`
The currencies aren't case-sensitive.

**Amount**

Amounts are converted to `HBAR` using the [CoinGecko API](https://docs.coingecko.com/v3.0.1/reference/simple-price). Subsequently, the `HBAR` amount is converted to `tinybar` and rounded to an integer value. When no amount is provided an input-field appears in which the user can enter an amount.

> 1 HBAR = 100.000.000 tinybar.

**Wallet**

....

> Account IDs on Hedera have to start with **_0.0._**

Example: `[hashpress_pay amount="0.1" currency="eur" title="☕︎ Buy us a coffee" network="testnet" wallet="0.0.4915084" accepts="USDC"]`

On the [demo page](https://hashpress.io/plugins/hashpress-pay) you can find more examples.

## Gutenberg Block

On websites with Gutenberg (WordPress version >= 5.0) and [Advanced Custom Fields PRO](https://www.advancedcustomfields.com/pro/) you can use the _HashPress Pay_-Gutenberg block instead of the shortcode. The functionality and output are the same as the shortcode.
