## Making fixed cover sized background images work on mobile devices

In iOS a fixed cover background is handled using the whole document height instead of using only the viewport's height. 

Example of an error: [erroneous working](https://sztojka.github.io/fixed-cover-background/index-wrong.html)
Solution: [fixed with CSS](https://sztojka.github.io/fixed-cover-background/)

This will be stretched as big as the document's height, so the background image will displayed zoomed:

```
body {
      background: url(https://newevolutiondesigns.com/images/freebies/nature-hd-background-9.jpg) no-repeat center center fixed;
      -webkit-background-size: cover;
      -moz-background-size: cover;
      -o-background-size: cover;
      background-size: cover;
}
```

However if you make the element itself fixed, this code works like a charm, by using only one CSS rule:

```
body:after{
      content:"";
      position:fixed; /* stretch a fixed position to the whole screen */
      top:0;
      height:100vh; /* fix for mobile browser address bar appearing disappearing */
      left:0;
      right:0;
      z-index:-1; /* needed to keep in the background */
      background: url(https://newevolutiondesigns.com/images/freebies/nature-hd-background-9.jpg) center center;
      -webkit-background-size: cover;
      -moz-background-size: cover;
      -o-background-size: cover;
      background-size: cover;
}
```


More info: [Background-image size cover not working on IOS](http://stackoverflow.com/questions/24154666/background-image-size-cover-not-working-on-ios/43058483#43058483)

Live demo of the solution: [Doklist.com](https://www.doklist.com)
