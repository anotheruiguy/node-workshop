# Build the UI config file

Create the file

```
$ touch _config.scss
```

Add the following code:

```
/////// Typography configuration
// *----------------------------------------
$font-size: 16;

$heading-1: 36;
$heading-2: 32;
$heading-3: 28;
$heading-4: 18;
$heading-5: 18;
$heading-6: 18;

$line: $font-size * 1.5;
$small-point-size: 10;
$large-point-size: 14;

$primary-font-family: #{"Helvetica Neue", Arial, sans-serif};
$secondary-font-family: #{"Helvetica Neue", Arial, sans-serif};
$heading-font-family: #{"Helvetica Neue", Arial, sans-serif};


/////// Default webfont directory
// *----------------------------------------
$fontDir: "fonts/";

/////// Default image directory
// *----------------------------------------
$imgDir: "images/";

/////// OOCSS generic base colors
// *----------------------------------------
$alpha-primary:   #5a2e2e;        // red
$bravo-primary:   #3e4147;        // green
$charlie-primary: #fffedf;        // yellow
$delta-primary:   #2a2c31;        // blue
$echo-primary:    #dfba69;        // accent

$alpha-gray:      #333;           //black

/////// Color math
// *----------------------------------------
@import "color-scale";


/////// Semantic variables
// *----------------------------------------
// abstract 'white' value to easily applied to semantic class objects
$white:                                #fff;

// primary header font color
$primary-header-color:                 $alpha-gray;

// default heading font weight
$heading-font-weight:                  normal;

// primary font color for the app
$primary-text:                         $alpha-gray;

// default `href` link color
$href-color:                           $delta-color;

// default shadow colors
$shadow-color:                         fade-out($alpha-color, 0.5);

// default border color
$border-color:                         $alpha-color;



/////// HTML 5 feature colors
// *----------------------------------------
// used with the `ins` tag
// http://www.w3schools.com/tags/tag_ins.asp
$ins-color:                            $charlie-color;

// used with the `mark` tag
// http://www.w3schools.com/html5/tag-mark.asp
$mark-color:                           $charlie-color;

// webkit tap highlight color
$webkit-tap-hightlight:                $delta-color;

// overrides the default content selection color in the browser
$selection-color:                      $charlie-color;
$selection-text-color:                 $primary-text;



//////// Default animation properties
// *----------------------------------------
$trans: .333s ease;
```



Add to the `application.scss` file

```
/////// App Config - this is where most of your magic will happen
// *----------------------------------------
@import "config";
```
