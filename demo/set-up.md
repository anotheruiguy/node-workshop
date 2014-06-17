# Getting libsass set up

<!-- ## Using nodemon

Use `nodemon` to start the Node server so that you don't need to keep restarting the server with updates to key `*.js` files.

```
$ npm install -g nodemon
```

Nodemon is not a production server tool. Only to be used in development environments.

With Express 4.0, the server code was moved to a new location within a `/bin/` dir. A simple way to hack on this is to update the `package.json` file in the following way:

```
"start": "nodemon ./bin/www"
```

When completed, you can still use the npm start command, but this will activate Nodemon instead. -->

Install libsass with Grunt Sass and add Bourbon. Node-Sass is installed as a dependency of Grunt-Sass

```
$ npm install grunt-sass --save
$ npm install node-bourbon --save
```

## Add bower.json file

```
{
  "name": "class-demo",
}
```

Add some Bower packages

```
$ bower install color-scale --save
$ bower install type-rhythm-scale --save
$ bower install rwd-toolkit --save
```

## Install Grunt

```
npm install grunt --save
```

## Install Grunt Watch

```
npm install grunt-contrib-watch --save-dev
```

Add `gruntfile.js`

```
module.exports = function(grunt) {
  grunt.initConfig({
    sass: {
      dist: {
        files: {
          'public/stylesheets/application.css': 'sass/application.scss'
        },
        options: {
          sourceMap: true,
          includePaths: [
            require('node-bourbon').includePaths,
            './bower_components/color-scale',
            './bower_components/type-rhythm-scale',
            './bower_components/rwd-toolkit'
          ]
        }
      }
    },
    watch: {
      source: {
        files: ['sass/**/*.scss', 'views/**/*.jade'],
        tasks: ['sass'],
        options: {
          livereload: true, // needed to run LiveReload
        }
      }
    }
  });

  grunt.loadNpmTasks('grunt-contrib-watch');
  grunt.loadNpmTasks('grunt-sass');
  grunt.registerTask('default', ['sass']);
};
```

## Create new Sass file

Create the following directory and file, then add some sass to the file.

```
$ mkdir sass
$ touch sass/application.scss
```

## Install library dependencies

Add these to the `application.scss` manifest to make Sass aware of these dependencies.

```
@import "bourbon";
@import "type-rhythm-scale";
@import "rwd-toolkit";
```


## Get grunt started

```
$ grunt
$ grunt watch
```
