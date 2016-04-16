# Little Giant Default Installation

This is the base project for a SilverStripe project initiated at Little Giant. It includes a number of custom elements and code which are of use to you.

## Pamphlet and Catalog Websites
While it includes a few default packages, there are others which we use within our ecosystem which you may find useful.

```json
    "littlegiant/silverstripe-catalogmanager": "dev-master",
    "littlegiant/silverstripe-singlepageadmin": "dev-master",
    "littlegiant/silverstripe-events": "dev-master",
    "littlegiant/silverstripe-default-dashboard": "dev-master",
    "micmania1/silverstripe-blog": "dev-master"
```

These can be found either on [packagist](http://www.packagist.org) or the [Little Giant Satis](http://packages.littlegiantdev.co.nz) repository.

## Ecommerce
To set up an ecommerce project include the following in your `composer.json`.

```json
    "littlegiant/swipestripe-theme-default": "dev-master",
    "littlegiant/swipestripe": "2.1.*@dev",
    "littlegiant/swipestripe-addresses": "2.1.*@dev",
    "littlegiant/swipestripe-category": "2.1.*@dev",
    "littlegiant/swipestripe-coupon": "2.1.*@dev",
    "littlegiant/swipestripe-dashboard": "2.1.*@dev",
    "littlegiant/swipestripe-dispatchemail": "2.1.*@dev",
    "littlegiant/swipestripe-flatfeeshipping": "2.1.*@dev",
    "littlegiant/swipestripe-reports": "2.1.*@dev",
    "littlegiant/swipestripe-stockmanagement": "2.1.*@dev",
    "frankmullenger/payment-paymentexpress": "*"
```

## Base theme

You will need to run `npm install` in this directory to before the build tasks can run.

Assets are bundled using [Webpack](webpack.github.io). Tasks can be invoked using `make`. If you are using windows
you may need to install `make` from the cygwin installer. Built assets are copied to the `./production` directory.

### Tasks

#### make clean
Removes the `./production` directory

#### make build
Runs `make clean` and bundles the assets using webpack with `NODE_ENV=production`. Copies the bundle to
the `./production` directory.

#### make watch
Serves the bundle and watches for changes. By default it will be served from `localhost:3000` but this can be configured
using the `HOST` and `PORT` environment variables.

## Environment

### .htaccess

You must change the .htaccess file to point to the development domain you have set up for the project.

### _ss_environment.php

A valid `_ss_environment.php` file must be present for the website to be able to connect to your database. A sample file is below

```php
<?php
/* What kind of environment is this: development, test, or live (ie, production)? */
define('SS_ENVIRONMENT_TYPE', 'dev');

/* Database connection */
define('SS_DATABASE_SERVER', 'localhost');
define('SS_DATABASE_USERNAME', 'root');
define('SS_DATABASE_PASSWORD', '');
define('SS_DATABASE_NAME', 'ssdefault'); // add a database name here

/* Configure a default username and password to access the CMS on all sites in this environment. */
define('SS_DEFAULT_ADMIN_USERNAME', 'dev@littlegiant.co.nz');
define('SS_DEFAULT_ADMIN_PASSWORD', 'password');

global $_FILE_TO_URL_MAPPING;

$_FILE_TO_URL_MAPPING['C:/wamp/www/silverstripe-default/'] = 'http://ssdefault.dev'; // use the mapping you created with vhostman
```

