# Introduction to Node

There is more then enough documentation out there that supports the question, "Why Node?". Something that really rings true with me is not where Node is today, but where Node is going. Without a doubt, the Rails community has brought a lot to the table, but what made all those awesome ideas hard to swallow was the fact that they were locked inside Ruby. As amazing as Ruby is, not everyone wants to be a Ruby developer.

I particularly like this quote from _Why The Hell Would I Use Node.js? A Case-by-Case Introduction_ [[reference](http://www.toptal.com/nodejs/why-the-hell-would-i-use-node-js)] by [Tomislav Capan](http://www.toptal.com/resume/tomislav-capan)

> ... it’s worth noting that Ryan Dahl, the creator of Node.js, was aiming to create real-time websites with push capability, “inspired by applications like Gmail”. In Node.js, he gave developers a tool for working in the non-blocking, event-driven I/O paradigm.


## Install Node

Before you run any installers, make sure you know what is on your computer. To see the version, simply run:

```
node --version
```

Of course to create and run a Node app, you need to have Node installed. To install Node, you can run the [installer from their site](http://nodejs.org/).

[Installing Node and npm](http://www.joyent.com/blog/installing-node-and-npm/) is a great article on all the ways to get this set up. Pay attention to Step 4 where there are some pretty solid opinions on how to set things up.

A [gist](https://gist.github.com/579814) is made available that illustrates a series of ways to install node.

The article does state a personal opinion against using Homebrew. Brew has worked for me rather well, but this is an opinion you may need formulate on your own.


## Node Package Manager (npm)

> npm is a NodeJS package manager. As its name would imply, you can use it to install node programs. Also, if you use it in development, it makes it easier to specify and link dependencies.

[Learn more](http://howtonode.org/introduction-to-npm) about npm

Depending on your install process you may or may not have NPM installed. To check, simply run:

```
npm --version
```

#### If you do not have npm installed, run the following:

Note: npm is the package manager for Node, so you can't use the package manager to install the package manager o_O

```
curl http://npmjs.org/install.sh | sh
```

## Using npm

Now that you have npm installed, all registered packages are a simple command away. For a basic package install, run:

```
npm install <package>
```

This install method will install the package in a directory (`node_modules/`) relative to your project. At times you will need to install libraries globally so that you can access their code from any application that doesn't necessarily require them as a dependency.

To do this, you need to add the `-g` flag n the install process:

```
npm install -g <package>
```

### Using npm with a project

The most common use case for npm is to maintain a manifest of dependencies for your project. This is maintained with a [package.json](https://www.npmjs.org/doc/json.html) file.

You can either crate this file yourself, or there are ways to generate this file too. In any directory simply run `npm init` and the CLI will walk you through a series of questions and out put something like the following:

```
{
  "name": "toss-this",
  "version": "0.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}
```

Once you have this in your project adding to it using `npm install` is very easy. Simply add the `--save` flag to the command like the following:

```
npm install <package> --save
```

Adding Grunt to the project would update the `package.json`  by adding a `dependencies` object in the json file:

```
{
  "name": "toss-this",
  "version": "0.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "grunt": "^0.4.5"
  }
}
```

Adding to this, if you wanted to add a dependency that is only for development versus production, you pass in the `-dev` flag:

```
npm install <package> --save-dev
```

Adding Gulp as a development dependency we get the following update to the `package.json` file by adding a `devDependencies` object:

```
{
  "name": "toss-this",
  "version": "0.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "grunt": "^0.4.5"
  },
  "devDependencies": {
    "gulp": "^3.6.2"
  }
}
```
