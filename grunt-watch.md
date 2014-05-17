# Grunt-watch w/Livereload

Now that we have Grunt set up with Sass, when we run the `grunt` task in the CLI, this will process the edits we have. While in rapid development, going back the the CLI, typing in `grunt` and then refreshing the browser will get old fast.

Thankfully, we have options. `grunt-contrib-watch` is a npm package that will watch our Sass files and when one is touched, it will run the Grunt tasks to process it. To install:

```
npm install --save-dev grunt-contrib-watch
```

As an added bonus, not only can we run a watcher that will process our Sass, but we can also watch `.jade` files for changes as well.


In the `Gruntfile.js` we need to add some Grunt tasks:

```javascript
module.exports = function(grunt) {
  grunt.initConfig({
    sass: {
      dist: {
        files: {
          'public/stylesheets/style.css': 'sass/style.scss'
        }
      }
    },
    watch: {
      source: {
        files: ['sass/**/*.scss', 'views/**/*.jade'],
        tasks: ['sass'],
        options: {
          livereload: true
        }
      }
    }
  });

  grunt.loadNpmTasks('grunt-contrib-watch');
  grunt.loadNpmTasks('grunt-sass');
  grunt.registerTask('default', ['sass']);
};
```

And there we have it. Grunt is installed, we have a functional `Gruntfile.js` and we can start writing some Sass too.

## Add Livereload to layout.jade

In order to get Live reload to fire in the project we need to add a reference to a non-existent JavaScript file in the `layout.jade` file as the last thing in the `<body>` tag.

```jade
script(src='http://localhost:35729/livereload.js')
```

In a new Express project, it would look like this:

```jade
doctype html
html
  head
    title= title
    link(rel='stylesheet', href='/stylesheets/style.css')
  body
    block content

    script(src='http://localhost:35729/livereload.js')
```

After this is added, go back and REFRESH the browser and then any edit in either Sass or Jade should fire the Livereload.
