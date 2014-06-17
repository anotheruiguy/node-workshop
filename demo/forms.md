# Forms

Create a new sass file

```
$ touch _forms.scss
```

Create a new forms directory

```
$ mkdir forms
$ midir forms/extends
```

Add the following files:

```
$ touch forms/_manifest.scss
$ touch forms/extends/_default-inputs.scss
$ touch forms/extends/_display-block.scss
$ touch forms/extends/_manifest.scss
```

Add the following to `forms/extends/_manifest.scss`:

```
@import "default-inputs";
@import "display-block";
```

Add the following to `forms/extends/_default-inputs.scss`:

```
%default-inputs {
  width: 100%;
  height: 100%;
  padding: 2.25em 1em 1em;
  outline: none;
  font-size: 1em;
}
```

Add the following to `forms/extends/_display-block.scss`:

```
%display-block {
  width: 100%;
  display: block;
}
```

Add the following to `forms/_manifest.scss`:

```
@import "extends/manifest";
```

Add the following to `_forms.scss`:

```
@import "forms/manifest";

.form {
  ul {
    border-bottom: 1px solid $hotel-gray;
    background-color: $white;
    margin-bottom: 1em;
  }
  li {
    border: 1px solid $hotel-gray;
    border-bottom: 0;
    position: relative;
  }
}

label {
  @extend %display-block;
  position: absolute;
  font-size: em(16);
  top: .5em;
  left: 1em;
  color: orange;
  opacity: 1;
  transition: #{$trans} top, #{$trans} opacity;
  .js-hide-label & {
    opacity: 0;
    top: 1.5em;
  }
}

input[type="text"] {
  @extend %display-block;
  @extend %default-inputs;
}

input[type="email"] {
  @extend %display-block;
  @extend %default-inputs;
}

textarea {
  @extend %display-block;
  @extend %default-inputs;
  height: 8em;
  resize: none;
}
```
