---
layout: post
title: "How to store and load ENV variables in dev "
---

It is very common to use an env variable in ours projects, specialy when we are using Docker ou Heroku. In this case several configurations will be done using ENV vars. but we want to be able to use that without so much work in our development enviroment.
We could do some script in shell setting all this variables to us and use this script to start our application

```
export FACEBOOK_APP_ID="<FACEBOOK_APP_ID>"
export FACEBOOK_APP_SECRET="<FACEBOOK_APP_SECRET>"
export GOOGLE_APP_ID="<GOOGLE_APP_ID>"
export GOOGLE_APP_SECRET="<GOOGLE_APP_SECRET>"

bundle exec rails server
```

Or you can use the [dotenv](https://github.com/bkeepers/dotenv), a very simple and cool gem that does this work for you.

To use it follow the instructions in [https://github.com/bkeepers/dotenv](https://github.com/bkeepers/dotenv), create you .env with all env variables needed in development and just execute your project using ``bundle``.

