Yii 2 Base App for Purists
==========================

Features
--------

The main tenet of this template is: Keep it simple! The idea was to only include
the absolutely necessary features - and optimize some of the configuration issues
of the original Yii2 base template.

 * Very flat configuration file structure
 * Provide local configuration files that won't get committed
 * Move `YII_DEBUG` and `YII_ENV` to configuration files
 * SiteController with login, logout, signup and password forget actions

Configuration
-------------

All configuration lives in 4 (or 5) files in the `config/` directory.

 * `web.php` configuration of the web app
 * `local.php` local overrides to the web config. **This file is not committed.**
 * `console.php` configuration of the console. Here you can reuse parts of the merged `web.php` and `local.php` configuration. See the example file for how this works.
 * `params.php` application parameters for both web and console application
 * `console-local.php` an optional file with local overrides to the console configuration. **This file is not committed.**


Workflow
--------

Before you can create new applications on a host, you first have to install the composer asset plugin:

    composer global require "fxp/composer-asset-plugin:1.0.0-beta2"

To create a new application you will usually follow this workflow:

 1. Install the template with `composer create-project --prefer-dist --stability=dev mikehaertl/yii2-base-app .`
 2. Add optional dependencies to `composer.json` and run `composer update`
 3. Add local configuration to `config/local.php` (DB, etc.)
 4. Check `config/params.php`, `config/web.php` and `config/console.php` and add project wide configuration
 5. Check `migrations/m140328_144900_init` to suit your user table schema.
 6. Check the models in `models/` and add/remove attributes.
 7. Run migrations with `yii migrate`

This should get you started. Your app should now run in a base version and is ready to be
committed to your project repository.

> Note: After the `composer create-command` step a unique cookie validation key is automatically
> generated and added to `config/local.php` for you.

> Note 2: `composer update` above may fail with an error about github rate limit exceeded.
> Have a look [here](https://getcomposer.org/doc/articles/troubleshooting.md#api-rate-limit-and-oauth-tokens)
> for how to resolve this issue.

Development
-----------

To keep this template updated with the latest package version, we should run `composer update`
from time to time and then commit `composer.lock`.
