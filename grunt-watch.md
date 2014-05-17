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
