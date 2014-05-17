# Install and set up Grunt

Grunt is the workhorse of the Node world. You need tasks run, then you put Grunt to work. If you are from the Rails world, Grunt is much like make or Rake. There is a TOM of documentation out there on this task runner, but in this workshop, I will focus on the basics that will get you up and running with an application.

Grunt is pretty simple to set up, create a new `Gruntfile.js` file in the root of your project and add the following shell syntax:

```javascript
module.exports = function(grunt) {
  grunt.initConfig({

    ...

  });

  grunt.loadNpmTasks('<package>');
};
```

To run Grunt, it is typical to install Grunt globally:

```
npm install grunt -g
```

BUT WAIT!! What about deployment? If we create tasks that require Grunt to run on the server, we need this to be a dependency on the app. So, let's install this as a local dependency:

```
npm install --save grunt
```

Using this base structure and Grunt installed, we can now begin to add new features to our app.
