# Crate a new Express app

At this point, you should be able to go forth and create an app. In this example, we will create a Node.js app with Express framework.

```
$ express <your-new-app>
```

Running this command (using `demo-app` as the example), you should see the following:

```
 create : demo-app
 create : demo-app/package.json
 create : demo-app/app.js
 create : demo-app/public
 create : demo-app/public/javascripts
 create : demo-app/public/images
 create : demo-app/public/stylesheets
 create : demo-app/public/stylesheets/style.css
 create : demo-app/routes
 create : demo-app/routes/index.js
 create : demo-app/routes/users.js
 create : demo-app/views
 create : demo-app/views/index.jade
 create : demo-app/views/layout.jade
 create : demo-app/views/error.jade
 create : demo-app/bin
 create : demo-app/bin/www

 install dependencies:
   $ cd demo-app && npm install

 run the app:
   $ DEBUG=my-application ./bin/www
```

BOOM! Express takes care of most of the labor. Now, we do what the computer says, change directory into the app dir and run `npm install`.

## What's in the app?

At this point, you should be able to do a `ls` and see the new structure that was created for you.

```
app.js    node_modules/ public/   views/
bin/    package.json  routes/
```

#### app.js

This is the logical starting point for your app. Some of the things in there, lets talk about:

The following lines, for this type of app, we don't need them:

```
var user = require('./routes/user');

app.get('/users', user.list);
```

Sets the path to the dir where the view files are located:

```
app.set('views', path.join(__dirname, 'views'));
```

Sets the path to the dir with static assets:

```
app.use(express.static(path.join(__dirname, 'public')));
```

Sets the root route for the app:

```
app.use('/', routes);
```

#### node_modules/

This is the dir where all your npm packages will reside.

#### public/

Directory for all static assets like images, JavaScript, CSS, fonts, etc ...

#### views/

Where all your layout and view Jade files will live.

#### bin/

There is a single file here, `www` and this is what activate the Node server.

#### package.json

Project description, scripts manager and the app manifest. Notice the following object:

```
"scripts": {
  "start": "node ./bin/www"
},
```

This is the code that allows you to run `npm start` for the app.

#### routes/

This is the directory where you will build out the RESTful routes for your app. With a base install there should be two files in there, `index.js` and `users.js`.
