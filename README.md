# embedded-pg-demo

Tiny app demonstrating how to use the embedded Postgres buildpack to
run and query Postgres in a dyno. Useful for CI or other experiments.

### Setup

```console
$ heroku create sushi
$ heroku buildpacks:add https://github.com/ryandotsmith/null-buildpack.git -a sushi
$ heroku buildpacks:add https://github.com/uhoh-itsmaciek/heroku-buildpack-embedded-pg.git -a sushi
$ git push heroku master
$ heroku ps:scale worker=1
$ heroku logs --tail --app sushi
```

You should see the logs of the app querying Postgres for the current
time every second.

You can change the Postgres version that will be used with a config var:

```console
$ heroku config:set PG_VERSION=9.5.0 -a sushi
```
