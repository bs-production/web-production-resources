# <i class="fab fa-js-square"></i> Javascript Snippets
***

#### Scroll to snippets

This one will gently slide to an anchor link on a page

```js
$('.send-me-to-here').click(function(e) { 
  e.preventDefault(); var dest = $(this).attr('href'); console.log(dest); $('html,body').animate({ scrollTop: $(dest).offset().top -25 }, 'slow'); 
  $('.send-me-to-here').fadeOut( 500 );
});
```

This one will fade in an element on scroll UP - Opposite action of the scroll to on our sites

```js
$(window).scroll(function(){ 
    if ($(this).scrollTop() < 500) {
        $('.send-me').show();
    } else  {
        $('.send-me').hide();
    }
})
```

#### Sticky Navbar

Here's some code to create a Sticky Navbar.

```js
    $(document).ready(function() {
      $(window).bind('scroll', function () {
          if ($(window).scrollTop() > 140) { // Match number to height of header
              $('.top-nav').addClass('fixed');
          } else {
              $('.top-nav').removeClass('fixed');
          }
      });
    });
```

Add CSS class to style sheet only.

```css

    .fixed {
    position: fixed;
    top: 0;
    }
```
#### Remove Testimonial Title and link for homepage
```js
  $( document ).ready(function() {
  $('.more-assets').hide();
  $('.widget-title').hide();
});
```

#### Print image
```html
<img src="IMAGE-URL" />
<div class="center">
  <a href="#" class="button" onclick="printImg('IMAGE-URL')">Print</a>
</div>

<script>
function printImg(url) {
  var win = window.open('');
  win.document.write('<img src="' + url + '" onload="window.print();window.close()" />');
  win.focus();
}
</script>
```


### Custom Video Player 
<iframe height='300' scrolling='no' title='Custom Video Player' src='//codepen.io/siwicki/embed/zPMezw/?height=300&theme-id=17398&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='https://codepen.io/siwicki/pen/zPMezw/'>Custom Video Player</a> by John Siwicki (<a href='https://codepen.io/siwicki'>@siwicki</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>
