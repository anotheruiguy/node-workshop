# Bower all the things

Unless you live in a hole, you are well aware that the JavaScript revolution is all around us. Many of the amazing concepts I discovered in the Rails ecosystem are now bursting out into the JavaScript space allowing for a greater distribution of awesome. The three pillars are; Yeoman, Bower and Grunt.

The problem I need to solve is; what is the best way to get some library code up on Github and make it easily accessible to users without having to clone the project? Because, that's pretty lame, right?

## Yeoman generators

Initially I came across [generator-sass-boilerplate](https://github.com/srsgores/generator-sass-boilerplate), a 'Yeoman generator for quickly scaffolding out Sass styles'. This is a very interesting approach for creating a complex library and allowing the user to customize the install. But for a simpler library of code, maybe just some functions and mixins, this is way to much overhead.

## Bower is the answer

Fast forward to now. I recently came across new posts that really break down what Bower is and what it is best at. And it hit me, this IS the answer!

For those not in the know, Bower is an extremely simple solution for front-end package management.

> It offers a generic, unopinionated solution to the problem of front-end package management, while exposing the package dependency model via an API that can be consumed by a more opinionated build stack.

The beauty of Bower is held within it's simplicity. Bower has a registry, but it's not 100% necessary. The common command is `bower install <package>` where `<package>` can refer to a [large number of options](http://bower.io/#using-a-different-name-and-a-specific-version-of-a-package), thus making it dirt simple to just share some code. NICE!

Sticking with the 'dirt simple' theme, you can use Bower to easily pull a repo into your project without having to clone it. Even if it doesn't have a `bower.json` file.

For example Stipe, a Compass Extension library I wrote, is not Bower aware at all.

```
$ bower install git://github.com/Toadstool-Stipe/stipe.git
```

Run that command in any folder and you will pull in the entire repo with no Github history. This alone is pretty interesting.

## Getting started with Bower

To get started, it's simple really. Assuming that Node and npm is installed on your local box, run:

```
$ npm install -g bower
```

### Install Bower package

I won't go into exhaustive detail here, but 99% of the time you simply need to run:

```
$ bower install <package>
```

As stated above, there are alternate install options, but the primary solution is to have a `bower.json` file in the repo and have it registered with Bower.

If you have a `bower.json` file in your project, explained in the next section, you can add the `--save` flag with the install and this will add the library as a dependency in your project. Sweet.

When you distribute the project, a user who clones it only has to run `$ bower install` and it will pull in all the external resources. Nice!

## Commit or not to commit!?

This new system of creating and distributing resources raises an interesting question; do you commit all your bower packages or not? In the Ruby world, Gems are not actually part of the project, but dependencies of the project, and never committed to the project's version control. In this new JavaScript world, Node and Bower package dependencies are referenced via a manifest, much like the Gemfile in Ruby, but are actually installed into the root of the project directory.

There is a [whole discussion](http://addyosmani.com/blog/checking-in-front-end-dependencies/) on this topic. I look at it this way, when you install  a Bower library, are you leaving this as a dependency or are you making modifications?

The choice is up to you, the arguments are strong on either side. In a situation where you are actually forking the code you installed, then the answer is pretty clear, it should be committed to the project or you need to fork the dependency.

## Generate new Bower package

Creating a new Bower package is again, really simple.

```
$ bower init
```

In the CLI, this will initiate a series of questions, the answers of which will be plugged into the new `bower.json` file it creates. Put as much in as you want, but all you really need is:

```
{
  "name": "your-project",
  "version": "0.1.0"
}
```

And that's it really. You have just created your first Bower resource library. Now go forth and build! Build out your resources, documentation, etc ... your package is ready to go at any time.

For easy testing, remember the `$ bower install git://github.com/ ...` trick? Run this against a new repo and see how it installs.

Be mindful of this step and what the package contains. In my opinion, I see Bower as a great way to distribute smaller, specific libraries of code. When I pull in your Bower package, do I really want all your documentation, tests, demonstration resources, etc ... As an example, I am going to pick on the Bourbon kids here, run:

```
$ bower install bourbon
```

Running this installer, you will get the whole repo. I don't want the whole repo, all I really want is what is in the `dist/` dir. To solve this, another developer forked Bourbon and created a new repo called [bower-bourbon](https://github.com/hmps/bourbon):

```
$ bower install bower-bourbon
```

Running this install you actually only get what is in the `dist/` dir. But are these forks reliable? Ohh open source, you are a wild one.

**UPDATE:** It's been brought to my attention that using the Bower install of Bourbon pulls in it's 3.2 Beta and appears not to be fully functional. This section was not intended to say "bad Bourbon" but to simply illustrate that in some cases, using Bower, you will get more of the library then you really want.

## Bower registration

Once you are ready for release, [register it with Bower](http://bower.io/#registering-packages). The criteria is pretty simple:

1. Make sure your repo has the `bower.json` file
1. You must use [semantic versioning](http://semver.org/)
1. Your package must be available at a Git endpoint, e.g. Github

Once you have all of that, run this command with your new package name and the Git endpoint:

```
$ bower register <my-package-name> <git-endpoint>
```

Registration is painless. Once you get the green light on everything, give it a test and do a `$ bower install <my-package-name>`


## Bower and Sass

Bower and Sass libraries are an amazing pairing. There are small repos all over Github where the complexity of making them a Ruby Gem/Compass Extension was just to much overhead. You are required to either fork, clone, or god forbid, copy and paste code into your project. What? Are we not civilized?

In the Ruby world, developers are used to having Gems and Compass Extensions installed in a safe, *untouchable location. The new Gem is added to the Gemfile and we simply reference the library in the project.

##### *Untouchable is a frustration with many developers. Importing Sass libraries that they did not have control over, or were unable to modify, that actually output CSS can be very frustrating.

In the new JavaScipt world, the library is added to the `bower.json` manifest or simply installed, but instead of it being in a obscured location, it is installed into the root of the project. This keeps things simple from an install perspective, but this means our Sass imports are in relative directories. Not a big deal, but different from what we are used to.

So, what does a Sass Bower package look like? Let's take a simple project I created called, [sass-icon-fonts](https://github.com/anotheruiguy/sass-icon-fonts). This package is simply a couple of mixins, one that allows the developer to easily create a `@font-face` set of rules and another is the ability to quickly generate a series of icon-font rules. The mini library comes with instructions and a very simple API.

Now, let's imagine you are building a Node project and you want to use this package as a resource, run:

```
$ bower install sass-icon-fonts --save
```

This installs the package and adds the dependency to your `bower.json` file. Located at the root level of the project is your `sass/` directory, within that is your `application.scss` file. At your root is the `bower_components` directory. For your `application.scss` file to access the new library, you will need to import a relative path to the library, as illustrated in the following:

```
@import "../bower_components/sass-icon-fonts/_ico-font.scss";
```

While the previous example works, while I found this acceptable, I didn't really find it awesome. Digging more into the Grint-Sass API I discovered the [includePaths](https://github.com/sindresorhus/grunt-sass#includepaths) function. This allows you to set an import path to include.

```
options: {
  includePaths: [
    './bower_components/bower-bourbon'
  ]
}
```

Now that you have this in your Grunt file, you can simply reference the library's main manifest file with a simply Sass import, like so:

```
@import "bourbon";
```

## Bower behind the firewall
If you find yourself behind a firewall that does not allow for the `git://[repo]` protocol, there is a fix for this. First, I suggest maually doing a clone using the `https://[repo]` protocol to make sure that this is really the issue. If the `https://[repo]` protocol works, then you may want to make the following update:

```
git config --global url."https://"
```

Thank you [Stack Overflow](http://stackoverflow.com/questions/15669091/bower-install-using-only-https)!

## Summary

When I say I want to Bower all the things, I mean just that. Now understanding Bower, I am looking at simple package management in a whole new light and I hope that you do to.

No more forking, cloning, deleting `.git/` directories just to include a library into a project. I am looking at creating Sass modules in a whole new light as well. Not that Compass extensions were difficult, but Bower frees me of multiple dependencies. Something that has been a real issue on many projects.
