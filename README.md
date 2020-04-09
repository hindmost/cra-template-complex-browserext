# cra-template-complex-browserext

A template for bootstrapping complex Chrome/Firefox/(any Chromium-based browser) extensions, to be used with [Create React App](https://github.com/facebook/create-react-app) v3.3.0 and higher.

## Usage

```sh
npx create-react-app my-app --template complex-browserext
```

## Includes

* [react-app-rewired](https://github.com/timarney/react-app-rewired) - to customize the default CRA configuration.

## Features

This template replaces the default single entry point with the following multiple ones:

* popup (`src/index.js`) - extension's popup page, replaces the default index entry point.
* options (`src/options.js`) - extension's options page.
* background (`src/background.js`) - background script.
* content (`src/content.js`) - content script.

### Notes

Index/popup entry point still refers to `src/index.js` (which can't be changed) and the respective HTML template still refers to `public/index.html`, whereas the respective output (both JS and HTML) uses `'popup'` in its filename template.

Any listed entry point except index/popup may be excluded from compilation. See `config-overrides.js` file for details on config customization.

The default CRA's development mode is incompatible with this template cause, unlike regular web pages, browser extensions can't be hosted on server. So running `npm start` script doesn't make sense (though it's still available).

This template uses the same simple React component test from older CRA versions (prior to v3.3.0) for popup and options' React components. If you want to use more advanced tests like in CRA v3.3.0 and higher, look at the official base template [sources](https://github.com/facebook/create-react-app/blob/master/packages/cra-template) for example.

CRA and Jest aren't aware of Chrome API or WebExtensions API. So if you want to use these APIs in your tests, you have to mock all used API methods (manually or with help of 3rd-party libraries).

## License

Licensed under the MIT license.
