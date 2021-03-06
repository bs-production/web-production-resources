# <i class="far fa-compass"></i> SuperNav
***
### superSplitAboutWork 

This snippet will allow you to add top level items to the superNav even with Super Split set to true.

```php
'superSplitDisplay' => true

//Example
70032 => array(
      'grandchildren' => true,
      'superSplitDisplay' => true
    ),
```
## De-Mega Services Mega Nav

If the Services dropdown has very few links, try this:

Add this JS to borders inside ```</body>```:
```js
$('ul#top-nav-list li:first-child .dropdown.m-menu ').addClass('short');
```
Add this CSS override:
```css
li.has-dropdown.not-click {
    position: relative !important;
}
```
example site: https://gutterguardsinpa.com

## Misaligned Dropdown:not(Services)

If your "Our Company" dropdown has lots of links and is misaligned and missing the "short class", try this:

```css
@media screen and (min-width: 641px){
    li.has-dropdown.not-click {
        position: static !important;
    }

    ul.dropdown.m-menu {
        left: 0 !important;
    }
}
```
example site: https://www.ottawafoundationsupportworks.ca/

### Mega Nav Link Columns

In some cases, when your mega nav links dont' flow into nice even columns, try this fix:

```css
ul.m-menu ul li {
        margin-bottom: 20px;
        float: none;
        -webkit-column-break-inside:avoid;
        column-break-inside:avoid;
	page-break-inside:avoid;
	break-inside:avoid;
    }
```


### Default Snippet 
Example http://www.connecticutbasementsystems.com/

This snippet will output the entire Nav chunk

```php
  <?php
    $superNav = new nav();
    $superNav->superMode = 'top';
    echo $superNav->generateSuperMarkup();
?>
```

## Custom Top 

When you go Custom there are a few options. There are three targets: services, about, map. If you need to add a special page to the supernav you can add its page ID and move it around in the array. 

```php
<?php
$superNav = new nav();
$superNav->superMode = 'top';
$superNav->superItems = array(
    'Services' => array(
        'target' => 'services'
    ),
    'Our Company' => array(
        'target' => 'about',
        'show_about_link' => true
    ),
    'Service Area' => array(
        'target' => 'map',
    ),
    'Free Quote' => array(
        'class' => 'quote',
        'target' => 'contact'
    ),
    43049 => array(
        'grandchildren' => true
    )
);

echo $superNav->generateSuperMarkup();
?>

```

### You can force child pages


```php
<?php
$superNav = new nav();
$superNav->superMode = 'top';
$superNav->superItems = array(
    'Services' => array(
        'target' => 'services'
    ),
    'Free Quote' => array(
        'class' => 'quote',
        'target' => 'contact'
    ),
    43049 => array(
        'children' => array(1,23234,23423)
    )
);

echo $superNav->generateSuperMarkup();
?>

```
##Version 2 Top Nav with Sliding sticky bar
```php
<?php
$superNav = new nav();
$superNav->superTemplateId = 3;
$superNav->superMode = 'top';
$superNav->superItems = array(
	'Services' => array(
        'target' => 'services'
    ),
    'Our Work' => array(
        'target' => 'about',
        'show_about_link' => false
    ),
    //Replace With Page ID of Financing Page
    12345 => array(
        'grandchildren' => false
    ),
    //Replace with Page ID of Reviews Page
    12345 => array(
        'grandchildren' => false
    ),
    'Service Area' => array(
        'target' => 'map',
    ),
    //Replace with Page ID of About Us Page
    12345 => array(
        'grandchildren' => false
    )
);

echo $superNav->generateSuperMarkup();
?>
```


### If you need Our Work and About Us 

look at the reviews for example. 

```php
		<?php
    		$superNav = new nav();
                $superNav->superSplitAboutWork = true;
                $superNav->superMode = 'top';
                $superNav->superItems = array(
                    'Services' => array(
                        'target' => 'services'
                    ),
                    'Reviews' => 159326,
                    'Our Work' => array(
                        'target' => 'work'
                    ),
                    159322 => array(
                        'target' => 'about',
                        'show_about_link' => true
                    ),
                    'Service Area' => array(
                        'target' => 'map',
                    ),
                    'Free Quote' => array(
                        'class' => 'quote',
                        'target' => 'contact'
                    )
                );

                echo $superNav->generateSuperMarkup();
		?>

```

####Use this script to make Services top nav dropdown full width if it only displays top level service links and no children
<!-- For this site - remove .short class on service dropdown until we figure it out dynamically -->
```
<script>
    $('ul#top-nav-list li:first-child .short').removeClass('short');
</script>
```

##Super Footer
```php
 <div id="footer-links">
    <?php
    $superNav = new nav();
    $superNav->superMode = 'bottom';
    echo $superNav->generateSuperMarkup();
    ?>
      <div class="social-footer"> <?php echo $socialFooter ?></div>
</div>

```


