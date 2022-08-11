<p align="center">

<img alt="preview" src="https://neftyblocks.me/preview-drops.png"></img>

</p>

[![npm bundle size](https://img.shields.io/bundlephobia/min/@neftyblocks/drops?style=flat)](https://www.npmjs.org/package/@neftyblocks/drops)
[![npm](https://img.shields.io/npm/dw/@neftyblocks/drops?style=flat)](https://www.npmjs.org/package/@neftyblocks/drops)
[![npm](https://img.shields.io/npm/v/@neftyblocks/drops?style=flat)](https://www.npmjs.org/package/@neftyblocks/drops)

# NeftyBlocks drops

We at NeftyBlocks understand the importance of keeping your users engaged. We want to make it easy for you to keep your community of NFT gamers, collectors and enthusiast close to your project. So, we have created drops for you to embed in your website and keep your users engaged with what matters most, your NFT project!

#### What does this embed include?

-   ⚙️ Fully functioning drops overview
-   🎨 [Customizable look](#-styling) (styling)
-   💲 [Payment processing](#-payment-processing) (read more below)

## 🚀 Usage

Install the library:

#### Package manager

1. Type in the terminal:

```bash
    # install dependencies
    $ npm i @neftyblocks/drops

    # or yarn
    $ yarn add @neftyblocks/drops
```

2. Include in your javascript file:

```js
import '@neftyblocks/drops';
```

3. Place in your HTML where you want to embed the drops:

```html
<neftyblocks-drops collection="your-collection"></neftyblocks-drops>
```

#### CDN (Plain HTML)

1. Place in your HTML where you want to embed the drops:

```html
<neftyblocks-drops collection="your-collection"> </neftyblocks-drops>

<script type="module" src="https://cdn.jsdelivr.net/npm/@neftyblocks/drops@latest"></script>
```

## 🎛 Options

Options are placed the element as `attributes` with a `value`.
which looks as follows:

```html
<neftyblocks-drops collection="your-collection-id" network="mainnet"> </neftyblocks-drops>
```

Most attributes are optional except for `collection`

| Attribute                   | Value                                                      | Default              | Description                                                                                                                                                                                                                   |
| --------------------------- | ---------------------------------------------------------- | -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `collection` **(required)** | `your-collection-id`                                       | None                 | set your collection name so the API knows which collection to send to the embed                                                                                                                                               |
| `limit`                     | number between `1` and `100`                               | `8`                  | set a value on how the maximum amount of drops to show per page                                                                                                                                                               |
| `network`                   | [supported chains / networks](#supported-chains--networks) | `mainnet`            | `mainnet` is the default network you can set it to `testnet` if you want to try it out first.                                                                                                                                 |
| `chain`                     | [supported chains / networks](#supported-chains--networks) | `wax`                | there is support for multiple chains, see [supported chains / networks](#supported-chains--networks) below.                                                                                                                   |
| `redirect`                  | None                                                       | None                 | the redirect URL is optional and is a way for you to interact with a transaction that happened [see redirect URL](#redirect-URL), default behavior is to redirect the user back to the URL it came from with no extra params. |
| `endpoint`                  | None                                                       | `api.neftyblocks.me` | only useful for development, API is highly customized for it's purpose.                                                                                                                                                       |
| `options`                   | None                                                       | None                 | Used to customize the drops order, sorting, etc. [See options config](#options-config)                                                                                                                                        |

#### supported chains / networks

The following blockchains are supported by the embedded drops

| chain         | network                    |
| ------------- | -------------------------- |
| wax (default) | mainnet (default), testnet |

#### redirect URL

if a redirect URL is placed as an attribute after the user has signed the transaction, the user will be redirected to the redirect URL after the transaction has been completed. we will include a couple of attributes in the query string to help you with the process.

-   `tx`: the transaction hash
-   `status`: the status of the transaction (`executed` or `failed`) this still needs to be validated as successfully executed
-   `sale`: the sale id
-   `assets`: the asset ids as `"12345,12345,12345"`

while we provide some useful data it's still up to you to validate that the transaction is valid and the user did make the sale. Everybody can write to a URL so be careful.

## 🎨 Styling

To get your look and feel to match your project, can customize by using [css variables](https://www.w3schools.com/css/css3_variables.asp).

either place this in your `style.css` css file or add a `<style> ... css here ... </style>` tag in your HTML.

```css
:root {
    /* the font-family for all text */
    --nefty-font-family: sans-serif;
    /* the default font size (best kept as is) */
    --nefty-font-size: 16px;
    /* the smaller font size (best kept as is) */
    --nefty-font-size--small: 14px;

    /* the minimum and maximum width of the drop (responsive)  */
    --nefty-drop-size-min: 250px;
    --nefty-drop-size-max: 1fr;

    /* the space between drops */
    --nefty-drops-gap: 48px;

    /* spacing between paragraphs in the description (markdown)  */
    --nefty-spacing: 6px;

    /* border radius for all roundings of inputs, buttons, images, markdown */
    --nefty-radius: 24px;
    --nefty-radius-image: 18px;
    --nefty-radius-markdown: 18px;
    --nefty-radius-small: 12px;

    /* border color for buttons, inputs */
    --nefty-border: #353945;
    /* border color for the drop*/
    --nefty-border-drop: #23262f;
    /* border thickness */
    --nefty-border-size: 1px;

    /* color primary text */
    --nefty-color: #fcfcfd;
    /* colors for non primary text */
    --nefty-color-secondary: #777e90;
    /* color for highlights (if price is free) */
    --nefty-color-highlight: #00ffff;
    /* color for the banner text */
    --nefty-color-banner: #24262f;
    /* color for the lock icon if drop is secured */
    --nefty-icon-banner: #fff;

    /* claim button in the drop (highlight) */
    --nefty-btn-primary: #00ffff;
    --nefty-btn-primary-bg: #23262f;
    --nefty-btn-primary-border: #00ffff;
    --nefty-btn-primary--active: #23262f;
    --nefty-btn-primary-bg--active: #00ffff;
    --nefty-btn-primary-border--active: #00ffff;

    /* sold button in the drop (no hover state) */
    --nefty-btn-sold: #cc333d;
    --nefty-btn-sold-bg: rgba(255, 255, 255, 0);
    --nefty-btn-sold-border: #cc333d;

    /* styling of pagination, info, and visual carousel buttons */
    --nefty-btn-secondary: #fcfcfd;
    --nefty-btn-secondary-bg: #141416;
    --nefty-btn-secondary-bg-50: rgba(20, 20, 22, 0.5);
    --nefty-btn-secondary-border: #353945;
    --nefty-btn-secondary--active: #fcfcfd;
    --nefty-btn-secondary-bg--active: #353945;
    --nefty-btn-secondary-border--active: #353945;

    /* backgrounds */
    /* drop mint background */
    --nefty-bg-mint: #0e0f12;
    /* all inputs */
    --nefty-bg-inputs: #23262f;
    /* drop background */
    --nefty-bg-drop: #23262f;
    /* markdown (desciption) background */
    --nefty-bg-markdown: #353843;
    /* banner (info for secure drop) */
    --nefty-bg-banner: #fcfcfd;
    /* loading state */
    --nefty-bg-loading: rgba(255, 255, 255, 0.05);
    /* fallback background color for images (best kept as is) */
    --nefty-bg-image: rgba(255, 255, 255, 0.05);
}
```

### 🪄 Advanced Styling Options

For more options we support the use of `::part` which will give you full controle to overwrite styling. [read more about ::part](https://developer.mozilla.org/en-US/docs/Web/CSS/::part)

To see what you can style look at the HTML in the console and look for the attribute `part="..."`

```css
neftyblocks-drops::part(part-name) {
    /* override the styling */
}
```

the following parts are available

Drops part:

-   `drops`
-   `drops-empty`
-   `pagination`
-   `pagination-btn`
-   `pagination-back`
-   `pagination-next`

Drop part:

-   `drop`
-   `drop-banner`
-   `drop-banner-icon`
-   `drop-banner-text`
-   `drop-pricing`
-   `drop-price`
-   `drop-price-image`
-   `drop-price-usd`
-   `drop-price-free`
-   `drop-visual`
-   `drop-visual-fade`
-   `drop-video`
-   `drop-image`
-   `drop-shadow`
-   `drop-visual-text`
-   `drop-visual-prev`
-   `drop-visual-next`
-   `drop-mint`
-   `drop-content`
-   `drop-title`
-   `drop-collection`
-   `drop-collection-image`
-   `drop-collection-name`
-   `drop-list`
-   `drop-list-key`
-   `drop-list-value`
-   `drop-sold`
-   `drop-claim`

Drop markdown (description) part:

-   `drop-md-button`
-   `drop-md-button-active`
-   `drop-md-wrapper`
-   `drop-md-wrapper-active`
-   `md-a`
-   `md-big`
-   `md-blockquote`
-   `md-code`
-   `md-em`
-   `md-h1`
-   `md-h2`
-   `md-h3`
-   `md-h4`
-   `md-h5`
-   `md-h6`
-   `md-hr`
-   `md-img`
-   `md-li`
-   `md-ol`
-   `md-p`
-   `md-pre`
-   `md-s`
-   `md-small`
-   `md-strong`
-   `md-sub`
-   `md-sup`
-   `md-table`
-   `md-td`
-   `md-th`
-   `md-tr`
-   `md-ul`

Other part:

-   `loading-group`
-   `loading`
-   `loading-visual`
-   `loading-content`
-   `loading-text`
-   `error-text`
-   `error-btn`

## Options config

> **Note**
> This is for advanced users and require basic knowledge on Javascript and API's.

Options config is used to customize the drops being displayed, this give you the option to only show drops you want or to sort or order the drops.

See [aa.neftyblocks.com](https://aa.neftyblocks.com/docs/#/drops/get_neftydrops_v1_drops) for all options

To use options config you need to add a `options` object.
this object needs to be `stringified` and passed in to the attribute called `options`.

```js
// Example config with some options
const options = {
    ids: '10001,10002,10003',
    order: 'desc',
    symbol: 'NEFTY',
    sort: 'start_time',
};

// use the way your framework provides dynamic attributes
`<neftyblocks-drops collection="yourCollection" options=${JSON.stringify(options)}></neftyblocks-drops>`;
```

## 💲 Payment processing

As we do not expect everybody to have a login and a way to handle signing transactions, we provide a payment processor that will be used to handle the payment process. The payment processor runs on a custom domain [https://neftyblocks.me](https://neftyblocks.me) and will deal with login, signing, and getting the user back to the site from where they came.

## ❤️ Community & Support

-   [GitHub Issues.](https://github.com/neftyblocks/embeds) Best for: bugs and errors you encounter using the embeded drops.
-   [Discord.](https://discord.com/invite/Bf789hjAsE) Best for: sharing your project and hanging out with the community.
