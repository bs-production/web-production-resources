# Site Speed 


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
