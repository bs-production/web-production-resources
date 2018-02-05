# Chris' Snippet Shack
***
#### Main message color overlay

``` css
#main-message::before {
    content: '';
    position: absolute;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(1, 74, 51, 0.6);
}
```

#### Create caching browser bookmark
``` javascript
javascript:void(location.href=location.href.substring(0,location.href.lastIndexOf('?')) + '/?cache=0&dev_template=1');
```

#### Take down site
``` php
<?php header("HTTP/1.0 503 Service Unavailable"); ?>
The requested page is unavailable. 
```
Delete the contents of the index page  
Redirect: `/(.+) /`

#### Remove Sidebar
``` html
<style media="screen">
#subnav-left {
  display: none;
}
#page-wrap > .row::before {
  display: none;
}
</style>

<script type="text/javascript">
$(document).ready(function(){
  $("#content-wrap").removeClass("medium-9 medium-push-3 large-10 large-push-2").addClass('small-12');
});
</script>
```

#### Mobile Slick slider
``` html
<style>
  /* arrows */
button.slick-arrow{
  background:rgba(0,0,0,.1);
  height:30px;
  width:30px;
  border-radius:50%;
  border-style:none;
  padding:0;
  position:absolute;
  z-index:10;
  -webkit-transform:translateY(-50%);
  transform:translateY(-50%);
  top:50%;
  font-size:0;
  outline:none;
  transition:all .2s ease
}
button.slick-prev{
  left:-30px
}
button.slick-next{
  right:-30px
}
button.slick-arrow::before{
  content:"";
  display:block;
  border-style:solid;
  border-color:rgba(0,0,0,.2);
  transform:rotate(45deg);
  width:12px;
  height:12px;
  transition:all .2s ease
}
button.slick-next::before{
  border-width:3px 3px 0 0;
  margin:0 0 0 7px
}
button.slick-prev::before{
  border-width:0 0 3px 3px;
  margin:0 0 0 10px
}
button.slick-arrow:hover{
  background:rgba(0,0,0,.3)
}
button.slick-arrow:hover::before{
  border-color:rgba(255,255,255,1)
}
</style>

<div class="container show-for-small-only">
  <div class="row">
    <div class="cred">
        <img src="http://d6449bb3dc657045bfc9-290115cc0d6de62a29c33db202ae565c.r80.cf1.rackcdn.com/240/nixa-x.jpg" alt="Nixa Area Chamber of Commerce" style="width: 180px;">
        <img src="http://d6449bb3dc657045bfc9-290115cc0d6de62a29c33db202ae565c.r80.cf1.rackcdn.com/240/lee-x.jpg" alt="Lee's Summit Chamber of Commerce">
        <img src="http://d6449bb3dc657045bfc9-290115cc0d6de62a29c33db202ae565c.r80.cf1.rackcdn.com/240/moberly-2-x.jpg" alt="Moberly Area Chamber of Commerce">
        <img src="http://d6449bb3dc657045bfc9-290115cc0d6de62a29c33db202ae565c.r80.cf1.rackcdn.com/240/bbb-x.jpg" alt="Foundation Recovery Systems BBB Business Review" />
        <img src="http://d6449bb3dc657045bfc9-290115cc0d6de62a29c33db202ae565c.r80.cf1.rackcdn.com/240/lake-area-3-x.jpg" alt="Lake Area Chamber of Commerce">
        <img src="http://d6449bb3dc657045bfc9-290115cc0d6de62a29c33db202ae565c.r80.cf1.rackcdn.com/240/home-advisor-x.jpg" alt="HomeAdvisor">
        <img src="http://d6449bb3dc657045bfc9-290115cc0d6de62a29c33db202ae565c.r80.cf1.rackcdn.com/240/lake-log-3-x.jpg" alt="Camdenton Area Chamber of Commerce">
    </div>
  </div>
</div><!-- end credibility -->

  <script>
    $('.cred').slick({
      dots: false,
      infinite: true,
      speed: 300,
      arrows: true,
      slidesToShow: 2,
      slidesToScroll: 2,
      responsive: [
        {
          breakpoint: 640,
          settings: {
            slidesToShow: 2,
            slidesToScroll: 2,
          }
        },
      ]
    });
 </script>
```