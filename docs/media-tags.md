# <i class="fas fa-video"></i> Media Tags
***
The audio and video html 5 tag has support from IE 9 and up and really good support on mobile. You can use these tags if we can’t use a third party to host the media like YouTube. 

### Audio <i class="fab fa-html5"></i>  

    <audio src="filename.mp3"></audio>

### Video <i class="fab fa-html5"></i>  

    <video src="filename.mp4" autoplay poster="posterimage.jpg"></video>

Please make sure all of the videos you embed are .mp4 before uploading them in the CMS. 

#### Show controls on mouseOver

``` html
<video id="myvideo" width="560" height="315" src="your.mp4"
  controlsList="nodownload" poster="your.jpg">
</video>

<script>
  $('#myvideo').hover(function toggleControls() {
    if (this.hasAttribute("controls")) {
      this.removeAttribute("controls")
    } else {
      this.setAttribute("controls", "controls")
    }
  })
</script>
```
