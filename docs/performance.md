# <i class="fas fa-tachometer-alt"></i> Performance
***
Example site: http://www.weathertitesystems.com/

## Our Goal 

First meaningful paint under 1.25 seconds. 

### Tools 

https://www.webpagetest.org/

### Scripts 
Defer and async as many scripts as possible. 

Defer means script is executed when the page has finished parsing.
Async means script will be executed while the page continues the parsing.


```html
<script src="demo_defer.js" defer></script>
<script src="demo_async.js" async></script>
```

### Image Compression 
https://www.jpeg.io/

https://tinypng.com/

https://imageoptim.com/mac

http://getoptimage.com/



### Responsive Images
http://www.responsivebreakpoints.com/

### SVG Compression
https://jakearchibald.github.io/svgomg/


### Accessibiity 

If the image is decorative and does not convey any information to the surrounding content, however, you may leave this "alt" attribute empty, or specify a "role" attribute with a value of "presentation."

```
<img src="http://0a7fabe38ae1ce229b14-5c67249f93bb503413209d779c0cd266.r58.cf1.rackcdn.com/7.png" alt="">
<img src="http://0a7fabe38ae1ce229b14-5c67249f93bb503413209d779c0cd266.r58.cf1.rackcdn.com/7.png" role="presentation">
```




## Site Speed Optimzations


Add these to your header just before ```</head> ``` Lighthouse can tell you which ones. 


```html
             <!--Preconnect Common -->
            <link rel="preconnect" href="https://maps.googleapis.com">
            <link rel="preconnect" href="https://use.typekit.net">
              <!--Preconnect Site Level -->
            <link rel="preconnect" href="https://pixel.dsp.townsquaremedia.com">
            <link rel="preconnect" href="https://pixel.sitescout.com">
 ```


## Images
1) Make sure everything is compressed 
2) If It is below Main Message change image to ```<img data-src="test.jpg">```

