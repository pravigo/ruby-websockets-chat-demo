# Ruby WebSockets Chat Demo

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy)

This is a simple application that serves tasty WebSockets to your users with [faye-websocket](https://github.com/faye/faye-websocket-ruby), [Puma](https://github.com/puma/puma), and [Sinatra](https://github.com/sinatra/sinatra).

Check out the [live demo](https://pravigo-chat.herokuapp.com/) .

## Setup

Credit: [install OpenSSL and Puma](https://github.com/hicknhack-software/rails-disco/wiki/Installing-puma-on-windows)

unpack the [OpenSSL Developer Package](http://packages.openknapsack.org/openssl/openssl-1.0.0k-x86-windows.tar.lzma), e.g. in D:\openssl (use 7Zip or PeaZip)

```
gem install puma -v '2.6.0' -- --with-opt-dir=d:\openssl
```

To install all the dependencies, run:

```
bundle install
```

Next the app requires some env vars for configuration. A sample `.env.sample` is provided for running the app locally. You can copy `.env.sample` to `.env` which foreman will pick up.

Ensure your local redis is running.  I am using redis-server.exe on Windows.  To set up download redis-2.4.6-setup-32-bit.exe from [https://github.com/rgl/redis/downloads](https://github.com/rgl/redis/downloads)

Using foreman we can boot the application.

```
$ foreman start
```

You can now visit <http://localhost:5000> to see the application.

Open in multiple browser tabs to test.

## Install to Heroku

Broadly speaking you can follow the instructions in [the docs](https://devcenter.heroku.com/articles/ruby-websockets)

However, this example uses Redis so won't work unless you have added Redis Cloud add on before starting your dyno.  You'll need to have added a credit card to your Heroku account first -even for the free tier.

When added you'll get a Redis Cloud connection string in ENV[REDISCLOUD_URL] under Settings->Config Variables.  (You can use this in your local version .env file first to test it is working).  

## Mills-tracker branch

This branch receives GPS data and plots it onto a map (Mapbox API key required)