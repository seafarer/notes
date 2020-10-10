---
title: Getting Ngrok, Laravel Valet, and WordPress Multisite with VIP local Jetpack search.
description: Documenting some of the issues I came across.
date: 2020-10-09
tags:
  - valet
  - ngrok
  - jetpack
  - multisite
  - wordpress
layout: layouts/post.njk
---
### Settings for wp-config.php, functions.php or MU plugin-loader.php depending on your setup

Where  `7` is your multisite site ID
```php
define( 'WP_7_HOME',    'http://' . $_SERVER['HTTP_HOST'] );
define( 'WP_7_SITEURL', 'http://' . $_SERVER['HTTP_HOST'] );
define( 'JETPACK_STAGING_MODE', false );
```

VIP app environment cannot be defined anywhere in your app. Even setting it to `production` activates Jetpacks staging mode. Comment it out if you have it set.
```php
// define( 'VIP_GO_APP_ENVIRONMENT', 'production' );
```

I also added this filter to be triple sure
```php
add_filter( 'jetpack_is_staging_site', '__return_false' );
```

### Other WP settings

Set your multisite domain to be your Ngrok domain. i.e. `subdomain.ngrok.io`

Make sure `blog_public` in your multisite site settings is set to 0. (1 might work, didnt test).

### Valet settings

When working with Valet and Multisite, you must 'link' each subdomain or individual site of your multisite in the valet WordPress root directory. For the Ngrok site, this must also be linked.

```bash
valet link subdomain.ngrok.io
```

Some tutorials will tell you to add your Ngrok domain to your `/etc/hosts/` file and redirect it to 127.0.0.1, but this is unnecessary. Valet already has Ngrok built in and handles this routing for you through its own magic.

