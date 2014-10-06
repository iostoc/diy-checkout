Celery Custom Checkout Example
============

> **What is this?** This is an example of how to create a custom, self-hosted checkout powered by the [Celery](https://trycelery.com) backend. <br/><br/>
> **Why would I want this?** You can  make a beautifully branded and high-converting checkout. And because it's powered by Celery backend, you'll automatically get robust e-commerce and order management. <br/><br/>
> **What can I do with this?** You can shape and extend the checkout interface and user experience into whatever you want or just use it as inspiration for your own checkout.

## Prerequisites

* A [Celery](https://trycelery.com) account
* Your own website
* Your website must use SSL
* jQuery

### IE9 Support

If you want to support IE9, you must include some some plugins for placeholders and CORS support.

* XDR plugin for Cross Domain calls, we recommend this one: [jQuery-ajaxTransport-XDomainRequest](https://github.com/MoonScript/jQuery-ajaxTransport-XDomainRequest)
* Placeholder polyfill, we recommend this one: [placeholdr](https://github.com/vote539/placeholdr)

## Limitations

- Stripe only
- No state-level shipping rate overrides
- No "Message to buyer"
- No collections support
- No product options or variants support

## Getting Started

1. Create a product on [Celery](https://trycelery.com)
1. Note your product slug or ID
  * If you are in the dashboard, go to the product you want to sell. The ID is after `products` in the URL, ex. `/products/[id]`
1. Add `data-celery="[id or slug]"` to your button element

    ```html
    <!-- Example button element -->
    <a href="#" data-celery="53ebdd5e1fd9c90400553dab">Pre-Order</a>
    ```

1. Add [dist/celery-cart.min.js](https://github.com/airbrite/diy-checkout/blob/master/dist/celery-cart.min.js) and [dist/celery.css](https://github.com/airbrite/diy-checkout/blob/master/dist/celery.css) to your site, where you put it is up to you:

    ```html
    <!-- Include jQuery before celery-cart.min.js -->
    <script src="jquery.js"></script>
    
    <script src="celery-cart.min.js"></script>
    <link rel="stylesheet" href="celery.css" />
    ```

1.  Click on your "Pre-Order" link


## Customizing the Checkout

Currently, you must manually customize the templates to set the countries, quantity options, and copy (header, footer, etc). In the future, this will be more easily configured.

The templates are written in using Mustache ([Hogan](http://twitter.github.io/hogan.js/)).

### Get up and running

1. Clone this repo
1. Install dependencies
  1. [Install node/npm](http://nodejs.org/)
  1. Run `npm install` in this repo folder
1. Run `npm run serve` to automatically start processing file changes and start a server
1. Replace `data-celery` value in `src/index.html` with your product id/slug
1. Open `http://localhost:8000/src` in a browser

### Edit features

Edit `src/js/config.js` and flip any feature flags before building. For example:

```js
{
  features: {
    taxes: true,
    coupons: true
  }
}
```

### Edit text and styling

1. To edit text and content, edit the files located in  `src/templates`
2. To customize styling, edit the files located in `src/less`
  * **Note:** After editing and saving the `.less` files, the CSS will automatically update in the browser without refreshing. You will be able to see the styling changes almost instantly.

### Put it on your website

1. When you are done customizing, run `npm run build` to generate the minimized files in `dist`
1. Include the newly generated `dist/celery-cart.min.js` and `dist/celery.css` on your site, where you put it is up to you:

    ```html
    <!-- Include jQuery before celery-cart.min.js -->
    <script src="jquery.js"></script>
    
    <script src="celery-cart.min.js"></script>
    <link rel="stylesheet" href="celery.css" />
    ```

1.  Click on your "Pre-Order" link

## Future

This is just an example, you can shape it into whatever you want or just use it as inspiration for your own checkout. Here are some things we will be adding to the example.

### CSS/LESS

* A customization config file will be available for easy basic customizations
* More explicit styles to reduce weird interactions with existing CSS

### Checkout features (tentative)

* Variant support
* "Message to Buyer" support
