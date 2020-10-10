---
title: MySQL commands for common WordPress tasks
description: Updating as I find or learn SQL that can help make life with WordPress easier.
layout: layouts/post.njk
date: 2020-10-09T21:58:56.881Z
tags:
  - mysql
  - wordpress
---
These are some handy SQL commands I'm keeping track of. I typically use these in the SQL window in [Sequel Pro](https://www.sequelpro.com/) as it enables me to export a CSV for use in other places, or sharing with python developers.

## Find specific meta key for posts

```sql
SELECT wp_12_posts.ID, wp_12_posts.post_name, wp_12_posts.post_type, wp_12_posts.post_title, wp_12_postmeta.meta_value
FROM wp_12_posts, wp_12_postmeta
WHERE wp_12_postmeta.post_id = wp_12_posts.id AND meta_key = 'reference_id'
ORDER BY wp_12_posts.ID;
```

## Find a string

Find a string in post content, and print out some other useful table columns along with it

```sql
SELECT wp_12_posts.ID, wp_12_posts.post_name, wp_12_posts.post_type, wp_12_posts.post_title, wp_12_posts.post_content
FROM wp_12_posts
WHERE wp_12_posts.post_content LIKE '%words to find%'
ORDER BY wp_12_posts.ID;
```