# volto-matomo
[![Releases](https://img.shields.io/github/v/release/eea/volto-matomo)](https://github.com/eea/volto-matomo/releases)

[Volto](https://github.com/plone/volto) add-on

## Features

Integrates [Matomo](https://matomo.org/) with Volto sites. At this moment there is a very basic integration that just pings Matomo on each router location change.

To configure it, either set the following variables:

  * `settings.matomoSiteId` (if not available it uses: `1`)
  * `settings.matomoUrlBase` (if not available it uses: `https://matomo.eea.europa.eu/`)

or `RAZZLE_MATOMO_SITE_ID` and `RAZZLE_MATOMO_URL` environment variables.

## API

There are two exports in `utils.js` (which can be imported from `volto-matomo/utils`, including from other Volto addons):

1. `trackPageView({ href, ...options }) : void` - takes an object with `href` and other options and sends to Matomo a page view track;
2. `trackEvent(options) : void` - takes an `options` object parameter and sends to Matomo an event track.

Note that the Matomo instance is behind the scenes lazy-loaded and cached.

The default behavior of volto-matomo is a call to `trackPageView` in `utils.js`, with the `href` and `documentTitle` options, on every URL change as recorded by the `AppExtras` component in Volto. The `href` is taken from `props.content['@id']` received by the `MatomoAppExtra.jsx` component. The `utils.js` file exposes just a part of the Matomo React API. If you wish to extend it or to understand it better, [this link](https://github.com/Amsterdam/matomo-tracker/tree/master/packages/react) might be helpful.

## Getting started

1. Create new volto project if you don't already have one:
    ```
    $ npm install -g @plone/create-volto-app
    $ create-volto-app my-volto-project
    $ cd my-volto-project
    ```

1. Update `package.json`:
    ```json
    "addons": [
        "@eeacms/volto-matomo"
    ],

    "dependencies": {
        "@eeacms/volto-matomo": "1.0.0"
    }
    ```

1. Install new add-ons and restart Volto:
    ```
    $ yarn
    $ yarn start
    ```

1. Go to http://localhost:3000

1. Happy editing!

## How to contribute

See [DEVELOP.md](https://github.com/eea/volto-matomo/blob/master/DEVELOP.md).

## Copyright and license

The Initial Owner of the Original Code is European Environment Agency (EEA).
All Rights Reserved.

See [LICENSE.md](https://github.com/eea/volto-matomo/blob/master/LICENSE.md) for details.

## Funding

[European Environment Agency (EU)](http://eea.europa.eu)
