---
title: MySQL commands for common WordPress tasks
description: This is a post on My Blog about agile frameworks.
date: 2020-10-09T21:58:56.881Z
tags:
  - another-tag
layout: layouts/post.njk
tag:
  - mysql
  - wordpress
---
Some handy SQL commands

## Find specific meta key for posts

``` sql
SELECT wp_12_posts.ID, wp_12_posts.post_name, wp_12_posts.post_type, wp_12_posts.post_title, wp_12_postmeta.meta_value 
FROM wp_12_posts, wp_12_postmeta
WHERE wp_12_postmeta.post_id = wp_12_posts.id AND meta_key = 'reference_id'
ORDER BY wp_12_posts.ID;
```

## Find a string
Find a string in post content, and print out some other useful table columns along with it

``` sql
SELECT wp_12_posts.ID, wp_12_posts.post_name, wp_12_posts.post_type, wp_12_posts.post_title, wp_12_posts.post_content
FROM wp_12_posts
WHERE wp_12_posts.post_content LIKE '%words to find%'
ORDER BY wp_12_posts.ID;
```
