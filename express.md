# Express, the Node framework

[Expressjs](http://expressjs.com/) is the web application framework for Node.js apps.

> Express is a minimal and flexible node.js web application framework, providing a robust set of features for building single and multi-page, and hybrid web applications.

It has a wealth of [APIs](http://expressjs.com/4x/api.html) and is FAS AS HELL!!

Express is well known for NOT following offer Rails as far as frameworks go, but more so it takes after another Ruby framework called [Sinatra](http://www.sinatrarb.com/). The concept is simple, the framework gives you enough to get things up and running as fast as possible and all without getting in your way.

For the most part, Express continues to live up to this statement.

For this workshop, we will be using Express as the core tool for getting a web app up and running with a server, route support, error pages, loggers, etc ...


## Install Express

Installing Express with npm is really easy. Keep in mind that there are two parts to Express, the library that runs it and an awesome generator.

To install Express:

```
$ npm install express -g
```

To install the generator:

```
$ npm install express-generator -g
```

## Generator version

Express 4.0 was recently released and there are some who are not jiggy with that. So, npm has a way of specifying the version of generator you install.

```
$ npm install -g express-generator@3
```
