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

Notice the trailing comma? This is because we are going to add more stuff. After that, add in the `engines` object and the specific engines we need to run this app:

```
"engines": {
  "node": "0.10.26",
  "npm": "1.4.3"
}
```

You should have something that looks like the following:

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

### Don't forget the Grunt + Bower

If at this time you do not have any of the Grunt packages or Bower in the `dependenciess` object, we need to get that in there.

You can either add them manually to the `package.json` file or dun:

```
$ npm install --save grunt
$ npm install --save grunt-sass
$ npm install --save bower
```

Something that you probably don't have is the ability for the deployed server to run the Grunt tasks. For this we need Grunt-CLI.

```
$ npm install --save grunt-cli
```

Right about now, you should be looking pretty good.

### Postinstall instructions

When we deploy the codes to Heroku, we have to tell it to run some commands, basically install the Bower packages and run the Grunt tasks. To do this, we need to add the instructions within the `scripts` object of the `package.json` file.

Directly under the `"start": "node ./bin/www"`, add:

```
"postinstall": "./node_modules/.bin/bower install && ./node_modules/.bin/grunt"
```

There, now we have everything that Heroku needs to install the packages and run the scripts.

## Add the Procfile

This is a file that Heroku needs in order to start the app.

```
$ touch Procfile
```

Add the following code:

```
web: npm start
```

Heroku will use this to kick start the app.


## Make this a Git repo

It is important to make this a git repo BEFORE you create the Heroku server. **WAIT!** Before you go all crazy on the Git, there are some things we need to do.

You should have a `.gitignore` file in your repo at this point. open that up and make sure you are ignoring all the `node_modules`, all the `bower_components` and anything in the `/stylesheets/*.css` spectrum.

```
node_modules
public/stylesheets/*.css
bower_components
```

Great. Now you can `git init` your repo.

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
