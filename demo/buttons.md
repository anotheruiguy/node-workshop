# Buttons

Add the following file:

```
$ touch _buttons.scss
```

Add to `application.scss` under the forms import

```
@import "buttons";
```

Open and add the following code:

```
button {
  @extend %default-inputs;
  -webkit-appearance: none;
  background: orange;
  color: white;
  border-radius: em(3);
  padding: 1em;
}
```
