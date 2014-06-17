# Add Reset

Add the file

```
$ touch _reset.scss
```

Add to the `application.scss`

```
/////// Standard CSS reset stuff here
// *-------------------------------------------------
@import "reset";
```

Add the following code:

```
// * Let's default this puppy out
// *-------------------------------------------------

html, body, div, span, object, iframe, h1, h2, h3, h4, h5, h6, p, blockquote, pre, abbr, address, cite, code, del, dfn, em, img, ins, kbd, q, samp, small, strong, sub, sup, var, b, i, dl, dt, dd, ol, ul, li, fieldset, form, label, legend, table, caption, tbody, tfoot, thead, tr, th, td, article, aside, figure, footer, header, hgroup, menu, nav, section, menu, time, mark, audio, video {
  margin: 0;
  padding: 0;
  border: 0;
  vertical-align: baseline;
  background: transparent;
}

* {
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

body {
  font-size: 100%;
  -webkit-font-smoothing: antialiased;
}

article, aside, figure, footer, header, hgroup, nav, section {
  display: block;
}

// * Responsive images and other embedded objects
// * Note: keeping IMG here will cause problems if you're using foreground images as sprites, like, say for Google Maps custom placemarkers.
// * There has been a report of problems with standard Google maps as well, but we haven't been able to duplicate or diagnose the issue.

img, object, embed {
  max-width: 100%;
}

img {
  border-style: none;
  border-color: transparent;
  border-width: 0;
}

// * we use a lot of ULs that aren't bulleted.
// * don't forget to restore the bullets within content.

ol,ul {
  list-style: none;
}

blockquote, q {
  quotes: none;

  &:before, &:after {
    content: '';
    content: none;
  }
}

a {
  margin: 0;
  padding: 0;
  font-size: 100%;
  vertical-align: baseline;
  background: transparent;
  &:focus {
    text-decoration: underline ;
    outline: none;
  }
}

del {
  text-decoration: line-through;
}


pre {
  //white-space: pre
  // * CSS2
  white-space: pre-wrap;
  // * CSS 2.1
  //white-space: pre-line
  // * CSS 3 (and 2.1 as well, actually)
  word-wrap: break-word;
  // * IE
}

input {
  &[type="radio"] {
    vertical-align: text-bottom;
  }
}

input, textarea, select, button {
  font-family: inherit;
  font-weight: inherit;
  background-color: #fff;
  border: 0;
  padding: 0;
  margin: 0;
}

table {
  font-size: inherit;
}

sub, sup {
  font-size: 75%;
  line-height: 0;
  position: relative;
}

sup {
  top: -0.5em;
}

sub {
  bottom: -0.25em;
}

// * standardize any monospaced elements

pre, code, kbd, samp {
  font-family: monospace, sans-serif;
}

input {
  &[type=button], &[type=submit] {
    @extend %stipe-cursor-pointer;
  }
}

button {
  cursor: pointer;
  margin: 0;
  width: auto;
  overflow: visible;
}

a.button {
  display: inline-block;
}

// * scale images in IE7 more attractively

.ie7 img {
  -ms-interpolation-mode: bicubic;
}

// * Ok, this is where the fun starts.
// *-------------------------------------------------

a:link {
  -webkit-tap-highlight-color: $webkit-tap-hightlight;
}

ins {
  background-color: $ins-color;
  color: black;
  text-decoration: none;
}

mark {
  background-color: $mark-color;
  color: $primary-text;
  font-style: italic;
  font-weight: bold;
}

::selection {
  background: $selection-color;
  color: $selection-text-color;
}

::-moz-selection {
  background: $selection-color;
  color: $selection-text-color;
}
```
