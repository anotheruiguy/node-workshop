
# Typography

Create new sass file

```
$ touch _typography.scss
```

Add the following code:

```
html {
  font: em($font-size, 16) $primary-font-family;
  line-height: baseline($font-size);
  color: $primary-text
}

h1, h2, h3, h4, h5, h6, [role=heading] {
  @include heading();
}

.title {
  margin-bottom: em(5);
  padding: 0.25em 0;
  text-align: center;
  background-color: $delta-scale-bravo;
  color: $white;
  border-radius: em(5) em(5) 0 0;
}
```

## Add below the reset in application.scss

```
/////// Base
@import "typography";
```
