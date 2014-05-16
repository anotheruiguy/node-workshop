# Deploy your first app

At this point, you should have an app that works locally on your computer. The following steps outline updates you need to make in order to deploy the codes.


## Update package.json

In this step, we need to add some code to the `package.json` file so that we can run the app from a remote server.

Right now, there is a good chance that the file will look like this:

```
{
  "name": "application-name",
  "version": "0.0.1",
  "private": true,
  "scripts": {
    "start": "node ./bin/www"
  },
  "dependencies": {
    "express": "~4.0.0",
    "static-favicon": "~1.0.0",
    "morgan": "~1.0.0",
    "cookie-parser": "~1.0.1",
    "body-parser": "~1.0.0",
    "debug": "~0.7.4",
    "jade": "~1.3.0"
  }
}
```

At the end of the `dependencies": { ... }` object, you need to add a comma `,` so that we can add more code.  First let's add the `main` keyword:

```
"main": "app.js",
```

Notice the trailing comma? This is because we are going to add more stuff. After that, add in the `engines` keyword and the specific engines we need to run this app:

```
"engines": {
  "node": "0.10.26",
  "npm": "1.4.3"
}
```

Notice, this is the last line, so no trailing comma. We want it all to look like the following:

```
{
  "name": "application-name",
  "version": "0.0.1",
  "private": true,
  "scripts": {
    "start": "node ./bin/www"
  },
  "dependencies": {
    "express": "~4.0.0",
    "static-favicon": "~1.0.0",
    "morgan": "~1.0.0",
    "cookie-parser": "~1.0.1",
    "body-parser": "~1.0.0",
    "debug": "~0.7.4",
    "jade": "~1.3.0"
  },
  "main": "app.js",
  "engines": {
    "node": "0.10.26",
    "npm": "1.4.3"
  }
}
```

## Add the Procfile

This is a file that Heroku needs in order to start the app.

```
$ touch Procfile
```

Add the following code:

```
web: npm start
```


## Make this a Git repo

It is important to make this a git repo BEFORE you create the Heroku server.

```
$ git add .
$ git commit -m "initial commit"
```

It is not required at this time to make this a Github repo, but you may want to do this if you make this a real app.

## Deploy the codes

This is pretty hard here. Make sure to follow the commands specifically:

```
$ heroku create <your-app-name>
$ git push heroku master
```

## Rejoice

If all is well, you should see a return like this:

```
http://<your-new-app>.herokuapp.com/ deployed to Heroku
```

Go to that URL and REJOICE!!!!!
