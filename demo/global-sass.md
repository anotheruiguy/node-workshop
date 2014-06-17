# Start with the global layout

```
$ mkdir layouts
$ touch layouts/_global.scss
$ touch layouts/_manifest
```

## Add to _global.scss

```
body {
  background-color: $delta-scale-juliet;
}
```

## Add to application.scss

```
/////// Layouts
@import "layouts/manifest";
```
