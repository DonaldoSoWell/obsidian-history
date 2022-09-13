---
tags:
- misc/hebergement
- perm/postgres
- perm/heroku
---
# Managing VACUUM on Heroku Postgres

![rw-book-cover](https://readwise-assets.s3.amazonaws.com/static/images/article4.6bc1851654a0.png)

## Metadata
- Author: [[Rails Support]]
- Full Title: Managing VACUUM on Heroku Postgres
- Category: #articles
- URL: https://devcenter.heroku.com/articles/managing-vacuum-on-heroku-postgres

## Highlights
- heroku pg:bloat DATABASE_URL --app sushi
- heroku pg:vacuum_stats DATABASE_URL --app sushi
- heroku pg:psql => VACUUM users;
