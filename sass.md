# Add libsass

Sass, and it's port libsass, is the leading CSS pre-processor and by far the most feature rich. But one thing that separates libsass from others in the JavaScript community is that it's not written in JavaScript. It's actually written in C/C++. So, the same library is portable to just about any language that a wrapper can be written for. And by far the most popular wrapper is `node-sass`.

All of this doesn't really matter. The only thing this means is that we need to go through some additional, although extremely simple, setup steps.

First, let's install Node-Sass:

```
$ npm install --save node-sass
```

This will install the Node wrapper for Sass and the C/C++ libsass library. Next, in order for Grunt to make use of the library, we need to add the Grunt-Sass package.

```
$ npm install grunt-sass --save
```

To get all of this integrated into the project, we simply need to update the `Gruntfile.js`.

```javascript
module.exports = function(grunt) {
  grunt.initConfig({
    sass: {
      dist: {
        files: {
          'public/stylesheets/style.css': 'sass/style.scss'
        }
      }
    }
  });

  grunt.loadNpmTasks('grunt-sass');
  grunt.registerTask('default', ['sass']);
};
```

In the `files:` object you will list the path to the output CSS and then the path to the input SCSS file.

At this point we are ready to run a `grunt` command and process some Sass.
