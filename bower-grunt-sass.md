# Bower - Grunt - Sass

Now that we know the powers of Bower to easily manage our front-end development dependencies, what do we need to do to add a Bower package of Sass code to our project?

## Bower install

First off, let's install a simple Bower package for illustration:

```
$ bower install css-calc-mixin --save
```

There, we now have the library of code in our project.

## Update Gruntfile.js

Next we want to update the `Gruntfile.js` so that we can easily include the library into our Sass files. Without this step, we would need to write fill paths in our Sass file to this and that's simply lame.

In the Grunt-Sass API we have options and the one we need to use is `includePaths`. Here we can pass in a string that is the full path from root to the Bower package into an array.

```javascript
module.exports = function(grunt) {
  grunt.initConfig({
    sass: {
      dist: {
        files: {
          'public/stylesheets/style.css': 'sass/style.scss'
        }
      },
      options: {
        includePaths: [
          './bower_components/css-calc-mixin'
        ]
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

## Update style.scss

To make use of this new Bower package library, we simply need to use a Sass convention to import the code.

```sass
@import "css-calc-mixin";
```

To test that this is working, let's add a little bit of code that references the Bower library.

```sass
.block {
  @include calc(width, 220px);
}

.block {
  @include calc(margin, 220px, 0);
}

.block {
  @include calc(width, 220px, true, 0);
}

.block {
  @include calc(width, 220px, true, 0, 50%, '+');
}
```

Back in the CLI, run `grunt` and we should see green lights all day long!
