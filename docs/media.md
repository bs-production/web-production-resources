# <i class="fas fa-video"></i> Media
***
The audio and video html 5 tag has support from IE 9 and up and really good support on mobile. You can use these tags if we can’t use a third party to host the media like YouTube. 

### Audio <i class="fab fa-html5"></i>  

    <audio src="filename.mp3"></audio>

### Video <i class="fab fa-html5"></i>  

    <video src="filename.mp4" autoplay poster="posterimage.jpg"></video>

Please make sure all of the videos you embed are .mp4 before uploading them in the CMS. 

#### Responsive YouTube CSS
``` html
<div class="video-responsive">[yt_embed_code]</div>
```
```css
.video-responsive{
    overflow:hidden;
    padding-bottom:56.25%;
    position:relative;
    height:0;
}
.video-responsive iframe{
    left:0;
    top:0;
    height:100%;
    width:100%;
    position:absolute;
}
```

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

### <i class="fab fa-youtube"></i> Custom Poster
Example: https://www.atticsystemsdealerships.com

``` html
<style>
.videoWrapper {
  position: relative;
  width: 100%;
  height: 0;
  background-color: #000;
}
.videoWrapper43 {
  padding-top: 75%;
}
.videoWrapper169 {
  padding-top: 56%;
}
.videoIframe {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: transparent;
}
.videoPoster {
  position: absolute;
  top: 0;
  right: 0;
  left: 0;
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
  cursor: pointer;
  border: 0;
  outline: none;
  background-position: 50% 50%;
  background-size: 100% 100%;
  background-size: cover;
  text-indent: -999em;
  overflow: hidden;
  opacity: 1;
  -webkit-transition: opacity 800ms, height 0s;
  -moz-transition: opacity 800ms, height 0s;
  transition: opacity 800ms, height 0s;
  -webkit-transition-delay: 0s, 0s;
  -moz-transition-delay: 0s, 0s;
  transition-delay: 0s, 0s;
}
.videoPoster:before {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 80px;
  height: 80px;
  margin: -40px 0 0 -40px;
  border: 5px solid #fff;
  border-radius: 100%;
  -webkit-transition: border-color 300ms;
  -moz-transition: border-color 300ms;
  transition: border-color 300ms;
}
.videoPoster:after {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 0;
  height: 0;
  margin: -20px 0 0 -10px;
  border-left: 40px solid #fff;
  border-top: 25px solid transparent;
  border-bottom: 25px solid transparent;
  -webkit-transition: border-color 300ms;
  -moz-transition: border-color 300ms;
  transition: border-color 300ms;
}
.videoPoster:hover:before, .videoPoster:focus:before {
  border-color: #f00;
}
.videoPoster:hover:after, .videoPoster:focus:after {
  border-left-color: #f00;
}
.videoWrapperActive .videoPoster {
  opacity: 0;
  height: 0;
  -webkit-transition-delay: 0s, 800ms;
  -moz-transition-delay: 0s, 800ms;
  transition-delay: 0s, 800ms;
}
</style>


  <div class="videoWrapper videoWrapper169 js-videoWrapper">
    <iframe class="videoIframe js-videoIframe" src="" frameborder="0" allowTransparency="true" allowfullscreen data-src="YOUR-YOUTUBE-VIDEO"></iframe>
    <!-- the poster frame - in the form of a button to make it keyboard accessible -->
    <button class="videoPoster js-videoPoster" style="background-image:url(YOUR-POSTER-ART);">Play video</button>
  </div>

  <!-- Optional stop button -->
  <!-- <button onclick="videoStop()">external close button</button> -->


<script>
// poster frame click event
$(document).on('click','.js-videoPoster',function(ev) {
  ev.preventDefault();
  var $poster = $(this);
  var $wrapper = $poster.closest('.js-videoWrapper');
  videoPlay($wrapper);
});

// play the targeted video (and hide the poster frame)
function videoPlay($wrapper) {
  var $iframe = $wrapper.find('.js-videoIframe');
  var src = $iframe.data('src');
  // hide poster
  $wrapper.addClass('videoWrapperActive');
  // add iframe src in, starting the video
  $iframe.attr('src',src);
}

// stop the targeted/all videos (and re-instate the poster frames)
function videoStop($wrapper) {
  // if we're stopping all videos on page
  if (!$wrapper) {
    var $wrapper = $('.js-videoWrapper');
    var $iframe = $('.js-videoIframe');
  // if we're stopping a particular video
  } else {
    var $iframe = $wrapper.find('.js-videoIframe');
  }
  // reveal poster
  $wrapper.removeClass('videoWrapperActive');
  // remove youtube link, stopping the video from playing in the background
  $iframe.attr('src','');
}
</script>
```
