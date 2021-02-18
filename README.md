# notes

We are providing all assets from the start, including fonts and accounts. We shouldn't be using our fonts or accounts for any part of a client's site from day one. It leads to all sorts of problems, and it's double the work. (HARD FOOT "ACCEPTED" ON FLOOR)

# NOTABLE ISSUE ON THIS PROJECT
- Fonts were wrong and needed to be reset everywhere to fix the difference, which had to do with not getting the correct fonts from the start.
- Google Map, a Huge bug in the backend, took a while to sort out that my API was still being used and only once notice because I killed my google API.
- Images used wrong naming conventions and were not cropped correctly.
- The Grid of the Invision was off on a lot of the pages.
- Assets Were not available in the Invision assets folder.
- Padding was off in a lot of places, and the tablet had to be done manually with nick.
- Some fonts were wrong or at least broken to mobile wrong.
- We need a guideline on how to figure out the image and video specs.


### THE INITIAL (Developer)
- Make sure all variables are setup
- Make sure all padding and margins are set up that is needed.
- Make sure all fonts options are setup. h1-h6, a, p, li etc


### Images (Designer)
- Make sure you're using the correct format SVG, PNG, JPG
- Make sure that the image is cropped around the clipboard. So there isn't extra spacing around it. Including SVG
- Compress all the images.
- Naming convention keep it consistent and also use underscore for spaces I.E (image_height.jpg)
- Put files in the respect folders. Icons, go into icons folder.
- Double-check that all images are in their respective folder.



    ├── build                   
      ├── icon  
        ├── arrow_down.svg
    ├── meta                 
    ├── bg   
      ├── white.jpg
      ├── pink.jpg




### Padding (Developer)

![Screen Shot 2021-02-15 at 2 31 37 PM](https://user-images.githubusercontent.com/22859725/108376164-4d58df80-71c8-11eb-9f66-d99696b415aa.jpg)



```sh
$x: 16px;
@mixin padding-top-bottom($n, $inherit: false) {
  @if $inherit {
  padding: $n * $x .9375rem;
  } @else {
    padding: $n * $x 0;
  }
}
 #section {
 <!-- Mobile -->
  @include padding-top-bottom(3);
 <!-- tablet -->
  @include breakpoint(medium) {
    @include padding-top-bottom(4);
  }
 <!-- ipad -->
  @include breakpoint(large) {
   @include padding-top-bottom(5);
  }
 <!-- Ipad Pro + -->
  @include breakpoint(xlarge) {
    @include padding-top-bottom(6);
  }
 ```
  ### Add your own grid outside of Foundation
  ```sh
  $padding: 16px;
  @mixin double {
    padding-right: $padding * 2;
    padding-left: $padding * 2;
 }

 @mixin single {
    padding-right: $padding;
    padding-left: $padding;
 }

  .special-three-grid {
    > .column {
      @include double;

      @include breakpoint(medium) {
        &::nth-child(even) {
          padding-left: $padding;
          padding-right: $padding * 2;
        }
        &:nth-child(odd) {
          padding-left: $padding * 2;
          padding-right: $padding;
        }
      }

      @include breakpoint(large) {
        &::nth-child(3n+1),
        &:nth-child(3n+2),
        &:nth-child(3n),
        &:nth-child(2),
        &:nth-child(3) {
          @include single;
       }
     }
    }
}
```


  # SCSS Variables(Developer)

```sh
$primary: #1AAFF2;
$secondary-blue: #6DCAC7;
$border-color: #E6ECF1;

/************************************
* IMG Path
************************************/
$theme-path: '/wp-content/themes/Site-name/library/img/';

/************************************
* Default Content Transition
************************************/
$content-bez-default: cubic-bezier(0.23, 1, 0.32, 1);
$content-t-duration: 1250ms;

/************************************
* Default Button Transition
************************************/
$btn-bez-default: cubic-bezier(0.23, 1, 0.32, 1);
$btn-t-duration: 1250ms;

$distance: 30px;
$distance-delay: 75ms;
/************************************
* Special Breaks
************************************/
$tabletNav: 1490;

 ```

  # SCSS Transtions Variables (Developer)

  ```s
.home-section {
  &.js-show {
    .content {
      h1 {
        opacity: 1;
        transform: translateY(0);
      }

      ul {
        li {
          opacity: 1;
          transform: translateY(0);
        }
      }
    }
  }
    .content {
      h1 {
        transition-delay: 0;
      }
      ul li {
         @for $i from 1 to 20 {
           &:nth-child(#{$i}) {
            transition-delay: $i * $distance-delay;
          }
        }
      }

      h1,
      ul li {
        opacity: 0;
        transform: translateY($distance);
        transition: transform, opacity;
        transition-duration: $content-t-duration;
        transition-timing-function: $content-bez-default;
      }
    }

    .btn {
      transform: translateY(0);
      transition: transform, color;
      transition-timing-function: $btn-bez-default;
      transition-duration: $btn-t-duration: 1250ms;
    }

```
 # Colors in Invision that are using opacitys on colors.

```sh
$base-color: #fff;
color: rgba( $base-color, .7 )
 ```
