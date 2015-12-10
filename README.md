# Finatra Hello World Heroku Example

Press this button to deploy the app:

[![Deploy to Heroku](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy)

## Overview

* A simple example finatra application that is deployable to [Heroku](https://heroku.com) and [integrates](https://github.com/rlazoti/finagle-metrics) with [Dropwizard/Codahale metrics](https://github.com/dropwizard/metrics).
* This app is borrowed from the [Finatra repository](https://github.com/twitter/finatra/tree/master/examples/hello-world-heroku).

## Deploy manually

Clone this app:

```
$ git clone https://github.com/kissaten/finatra-hello-world
$ cd finatra-hello-world
```

Make sure you have the [Heroku Toolbelt](https://toolbelt.heroku.com/) [installed](https://devcenter.heroku.com/articles/getting-started-with-scala#set-up).

Create a new app in Heroku:

```
$ heroku create
Creating nameless-lake-8055 in organization heroku... done, stack is cedar-14
http://nameless-lake-8055.herokuapp.com/ | https://git.heroku.com/nameless-lake-8055.git
Git remote heroku added
```

Then deploy the example application to Heroku:

```
$ git push heroku master
Counting objects: 480, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (376/376), done.
Writing objects: 100% (480/480), 27.68 MiB | 16.24 MiB/s, done.
Total 480 (delta 101), reused 0 (delta 0)
remote: Compressing source files... done.
remote: Building source:
	...
```

You can then open the application in a browser with `heroku open`, e.g.:

```
$ heroku open hi?name=foo
```

## Run the example locally with Forego

Build the app:

```
$ sbt stage
```

Run the app:

```
$ heroku local web
19:47:56 web.1  | started with pid 77663
19:47:59 web.1  | I 0528 02:47:59.058 THREAD1: HttpMuxer[/admin/metrics.json] = com.twitter.finagle.stats.MetricsExporter(<function1>)
19:47:59 web.1  | I 0528 02:47:59.096 THREAD1: HttpMuxer[/admin/per_host_metrics.json] = com.twitter.finagle.stats.HostMetricsExporter(<function1>)
19:47:59 web.1  | I 0528 02:47:59.183 THREAD1: Serving admin http on 0.0.0.0/0.0.0.0:0
19:47:59 web.1  | I 0528 02:47:59.218 THREAD1: Finagle version 6.25.0 (rev=78909170b7cc97044481274e297805d770465110)
19:48:00 web.1  | 2015-05-27 19:48:00,550 INF            HttpRouter                Adding routes
19:48:00 web.1  | GET     /hi
```

The app will now be running at [http://localhost:5000/hi?name=foo](http://localhost:5000/hi?name=foo). `Ctrl-C` to exit.
