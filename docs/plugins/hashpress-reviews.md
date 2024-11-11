# HashPress Reviews

Integrate Hedera Smart Contracts into your WordPress website to get verifiable reviews. All reviews written using Realviews are stored on the Hedera network, connected to the purchase transaction and signed by the customer using their wallet.

## Dependencies

-   [HashPress Core](/plugins/hashpress-core) — Small but essential plugin for establishing wallet connections.

## Recommended Plugins

-   [Advanced Custom Fields PRO](https://www.advancedcustomfields.com/pro/) — HashPress Pay adds an ACF Gutenberg block
-   [WooCommerce](https://woocommerce.com/) — HashPress Pay adds (optional) WooCommerce Payment Gateways.

## Installation

1. Download the plugin as a ZIP file from its [repository](https://github.com/louweal/hashpress-reviews).
2. Go to `Plugins` section in WordPress
3. Click `Add New Plugin`
4. Click `Upload Plugin`
5. Upload the ZIP file
6. Click `Activate`

## Configuration

...

### WooCommerce

On the Realviews admin page you can select the number of reviews you want to show on a product page and set the button text for showing more reviews (if available). This button triggers a modal showing all reviews. Set the number of reviews to `-1` to show all reviews in-page.

> Set the number of reviews to `0` to hide the whole review section.

![Realviews Admin Settings](https://github.com/louweal/hellofuturehackathon/blob/master/realviews/assets/admin.png)

## Shortcodes

### [hederapay_transaction_button]

Realviews adds attribute `store` to the Hederapay transaction button that allows you to save the transaction IDs to the page metadata such that they can be used to enable reviewing on that page.

| Attribute          | Description                                            | Default value |
| :----------------- | :----------------------------------------------------- | :------------ |
| title              | Button text                                            | Pay           |
| amount             | Amount to be send in _currency_ (see details)          | null          |
| currency           | Currency the _amount_ is in (see details)              | USD           |
| memo               | Message to send along with the transaction             | null          |
| testnet_account    | Receiver Account ID on the testnet                     | null          |
| previewnet_account | Receiver Account ID on the previewnet                  | null          |
| mainnet_account    | Receiver Account ID on the mainnet                     | null          |
| **store**          | **Store transaction id in page metadata (true/false)** | **false**     |

**Example**
`[hederapay_transaction_button amount="5" currency="eur" title="Buy ebook" testnet_account="0.0.4505361" memo="Ebook purchase" store="true"]`

### [realviews_latest_reviews]

Retrieves all reviews for the current product/page from the Hedera Mirror [REST API](https://docs.hedera.com/hedera/sdks-and-apis/rest-api).

> The reviews have a small badge in the top right corner when they are from the `testnet` or `previewnet` network.

### [realviews_num_reviews]

Displays the total number of reviews for the current product/page.

Attributes

| Attribute   | Description                                       | Default value |
| :---------- | :------------------------------------------------ | :------------ |
| max_reviews | Maximum number of reviews to show on product page | 2             |
| button_text | Button text for showing all reviews               | All reviews   |

## Gutenberg Blocks

### HashPress Pay

Realviews also adds a `Store transactions` toggle to the Gutenberg block.

### Latest Reviews

On websites with Gutenberg (WordPress version >= 5.0) and [Advanced Custom Fields PRO](https://www.advancedcustomfields.com/pro/) you can use the _Latest Reviews (Realviews)_-Gutenberg block instead of the shortcode. The functionality and output are the same as the shortcode.

## Review verification

All reviews written using Realviews are stored on the Hedera network, connected to the purchase transaction and signed by the customer using their wallet. Therefore you can be sure that every review is, indeed, **real**.

**Inspecting transaction data**

The following two steps allow everyone to check the raw transaction data on Hedera to verify the review.

**Step 1**
Click on the review date of the review you wish to inspect. This brings up the raw transaction data on the Hedera Mirrornode. Look for the encoded string inside `"logs"`**>**`"data"` and copy it.
**Step 2**
Ask [ChatGPT](https://chatgpt.com/) to decode it.

> **Example**:

> ```
> decode without explanation: 0x000000000000000000000000000000000000000000000000000000000000002000000000000000000000000000000000000000000000000000000000000000c57b227472616e73616374696f6e4964223a22302e302e343530353336312d313732333937363938312d373134383035333734222c22726174696e67223a352c226e616d65223a22416c6578204d2e222c226d657373616765223a225468697320747261636b20697320612062616e676572212054686520656e65726779206973206f66662074686520636861727473e280947065726665637420666f722067657474696e672070756d706564207570206265666f72652061206e69676874206f75742e227d000000000000000000000000000000000000000000000000000000
> ```

```

ChatGPT will respond with the decoded string.

> **Example**:
> `{"transactionId":"0.0.4505361-1723976981-714805374","rating":5,"name":"Alex M.","message":"This track is a banger! The energy is off the charts—perfect for getting pumped up before a night out."}`

**Step 3** (optional)
If you also want to inspect the buy transaction connected to this review, you can simply copy the `transactionId` from ChatGPT and look it up using a Network Inspector such as [Hashscan](https://hashscan.io/).

> Tip: Make sure you select the right network in the network inspector.

## Other Plugins by HashPress Pioneers

-   [HederaPay](https://github.com/louweal/hellofuturehackathon/tree/master/hederapay)
```
