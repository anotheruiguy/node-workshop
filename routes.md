# Fun with Routes

The `app.VERB()` methods provide the routing functionality in Express, where **VERB** is one of the HTTP verbs, such as `app.post()`. Multiple callbacks may be given, all are treated equally, and behave just like middleware, with the one exception that these callbacks may invoke `next('route')` to bypass the remaining route callback(s). This mechanism can be used to perform pre-conditions on a route then pass control to subsequent routes when there is no reason to proceed with the route matched.

The following snippet illustrates the most simple route definition possible. Express translates the path strings to regular expressions, used internally to match incoming requests. Query strings are **not** considered when peforming these matches, for example `GET /` would match the following route, as would `GET /?name=tobi`.

[source](http://expressjs.com/4x/api.html#app.VERB)


```javascript
app.VERB(path, [callback...], callback)
```

Basic example using this syntax that will send a string of text to the browser is:

```javascript
app.get('/', function(req, res){
  res.send('hello world');
});
```

Lets get into setting up some routes. In the `app.js` file the following line is how this comes together:

```javascript
var routes = require('./routes/index');
```

What's happening here? Basically, Express is setting the `var` of `routes` to require the path and file of `./routes.index`.

This var is then used to set the root path of the app

```javascript
app.use('/', routes);
```

Another thing we can do is `res.send()` and what ever we put in there will get sent directly to the browser. For example:

```javascript
res.send('hello world')
```

Using the `res.send()` we can do fun things like even send in JSON objects.

```javascript
res.send({'name':'Bob Goldcat', 'age': '41'})
``

This method allows us to then keep all our routes in the `index.js` file if needed. There are better ways to address a more complicated routing solution, but for the scope of this workshop, this is great.

## What's in the index.js file?

Looking at our `index.js` file you should see the following:

```javascript
var express = require('express');
var router = express.Router();

/* GET home page. */
router.get('/', function(req, res) {
  res.render('index', { title: 'Express' });
});

module.exports = router;
```

##### router.get

This is the function that will 'get' the URL path of `/`. Then we need to create a function that will make a `req` (request) and `res` (response). The is another concept of `next` for chaining events would go here as well, but not shown in this example.

##### What is module.exports?

This is the object that's actually returned as the result of a require call. This is a Node feature, more on this at [nodejs.org/api](http://nodejs.org/api/modules.html#modules_module_exports).

## Build a new route

Looking at the syntax pattern, if we wanted to add a new route to the app, we can simply do something like the following:

```javascript
router.get('/app', function(req, res) {
  res.render('app', { title: 'Express' });
});
```

Keep in mind that the value of the URL, `/app`, does not need to be the same value of the file itself. If the name of the view was `foo.jade` we could do the following:

```javascript
router.get('/app', function(req, res) {
  res.render('foo', { title: 'Express' });
});
```

## It's a route? It's a controller?

What's interesting about this is that the route function is containing logic. Inside the route is a `res.render` function:

```javascript
res.render('foo', { title: 'Express' });
```

In the view template we see this:

```jade
h1= title
p Welcome to #{title}
```

These are two examples of how we can pull data from the 'controller/route' and display in the view. In this example we get the HTML output of:

```html
<h1>Express</h1>
<p>Welcome to Express</p>
```

All of this seems to be a bleed of concerns as the route may also contain controller info? This is true and there is a movement in the community to change the name of the dir from `routes` to `controllers`.

A great example of this can be seen at [Holowaychuk](https://github.com/visionmedia/express/tree/master/examples/mvc)'s Express MVC example repo.

But for the sake of this workshop and consistency, we will keep the current convention.
