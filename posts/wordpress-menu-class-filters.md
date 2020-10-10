---
layout: layouts/post.njk
title: Adding Bootstrap (or other) classes to WordPress menu lists and links
description: This is a post on My Blog about win-win survival strategies.
date: 2020-10-10T16:17:51.118Z
tags:
  - WordPress
  - Bootstrap
---
Here is a filter for adding a class to to the `<li>` in a `wp_nav_menu()` function.

```php
add_filter('nav_menu_css_class', function($classes, $item, $args) {
    if($args->theme_location == 'primary_navigation') {
        $classes[] = 'nav-item';
    }
    return $classes;
}, 11, 3);
```

And here is a filter for adding a class to the <a> tag in `wp_nav_menu()` function.

```php
add_filter( 'nav_menu_link_attributes', function( $atts, $item, $args ) {
    $atts['class'] = 'nav-link';
    return $atts;
}, 11, 3);
```

No need for writing complicated nav walkers unless want fine grained control over the menu markup. If you, like me, are starting from scratch with an empty theme, there is no need to remove any classes as they do not interfere. Just adding the Bootstrap classes is enough to get the navbar menu up and running with the WordPress menu functions.