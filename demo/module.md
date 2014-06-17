# Create a module

In the Sass directory, lets create a module directory with the necessary files inside:

```
$ mkdir modules
$ mkdir modules/message-container
$ touch modules/message-container/_module-message-container.scss
$ touch modules/message-container/_manifest.scss

```

Add the following to the `_module-message-container.scss` file:

```
.message-container {
  margin: 1em auto;
  width: 90%;
  padding-bottom: 100px;
  @media #{$tablet} {
    width: 75%;
  }
  @media #{$desktop} {
    width: 50%;
  }
}
```

## Add to _manifest.scss

```
@import "module-message-container";
```

## Add to application.scss

```
/////// Modules
@import "modules/message-container/manifest";
```

## Central module manifest

In the `application.scss` we could enter each module on-by-one as described above, but we could also add a manifest at the root of `modules` that will import all the manifests contained within.

So in the `application.scss` we do the following:

```
/////// Modules
@import "modules/manifest";
```

Then in  `modules/manifest.scss` we do this:

```
/////// Sub-Modules
@import "message-container/manifest";
```

This helps keep things easier to manage as the we never need to update the `application.scss` file and at the root of the modules directory, where we are working, we just need to add a new listing there. Everything is imported and everything just works.

Our folder structure would look like the following:

```
|- application.scss
|--- modules/
|----- _manifest.scss
|----- message-container/
|------- _manifest.scss
|------- _module-message-container.scss
```
