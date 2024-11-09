# HashPress Core

...

## Installation

1. Download the plugin as a ZIP file from its [repository](https://github.com/louweal/hashpress-core).
2. Go to `Plugins` section in WordPress
3. Click `Add New Plugin`
4. Click `Upload Plugin`
5. Upload the ZIP file
6. Click `Activate`

## Configuration

You will need a WalletConnect Project ID specifically for your current website (domainname). You can get one by going to [WalletConnect](https://cloud.walletconnect.com/) and setting up a new `WalletKit` project.

Go to `Settings` > `HashPress Pay` and enter your project id.

## Shortcodes

### [hashpress_connect]

Adds a connect/disconnect button.

Useful when you want to allow the user to connect their wallet without sending a transaction. After connecting the button acts as a disconnect button. It uses [WalletConnect](https://walletconnect.com/) to establish a a secure connection with cryptocurrency wallets.

> The button has a small badge in the top right corner when the active network is `testnet` or `previewnet` to warn the user/developer that the code isn't running on the mainnet.

| Attribute       | Description                                     | Default value     |
| :-------------- | :---------------------------------------------- | :---------------- |
| network         | Type of network: testnet, previewnet or mainnet | testnet           |
| connect_text    | Button text before wallet is paired             | Connect wallet    |
| disconnect_text | Button text after connection is established     | Disconnect wallet |

**Example:**
`[hashpress_connect network="testnet" connect_text="Connect" disconnect_text="Disconnect"]`

### [hashpress_account]

Displays the Account ID of the paired wallet. It is hidden when no wallet is connected.
