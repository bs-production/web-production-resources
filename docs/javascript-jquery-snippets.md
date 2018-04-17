# <i class="fab fa-js-square"></i> Javascript & Jquery Snippets
***
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
