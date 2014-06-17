# Add some jQuery magic

Open `layout.jade` and add in the foot of the doc:

```
script(src='//ajax.googleapis.com/ajax/libs/jquery/1.11.0/jquery.min.js')
script(src="/javascripts/app.js")
```

Create the following file:

```
$ touch public/javascripts/app.js
```

Open `app.js` and add the following:

```
// Test for placeholder support
$.support.placeholder = (function(){
  var i = document.createElement('input');
  return 'placeholder' in i;
})();

// Hide labels by default if placeholders are supported
if($.support.placeholder) {
  $('.form li').each(function(){
    $(this).addClass('js-hide-label');
  });
}

$('.form li').find('input, textarea').on('keyup blur focus', function(){

  // Cache our selectors
  var el = $(this),
    parent = el.parent();

    // Add or remove classes
    if( el.val() === '' ) {
        parent.addClass('js-hide-label');
    } else {
        parent.removeClass('js-hide-label');
    }
});
```
