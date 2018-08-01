# No longer a dealer

1.  **Site Content > Site Template > Borders tab**  
Replace all existing code in `Borders` tab with below PHP snippet along with "The requested page is unavailable."  
Make sure it's pushed live.  
```php
<?php
header("HTTP/1.0 503 Service Unavailable");
?>
The requested page is unavailable. 
```

2. **Site Content > Content Management > Home page**  
Delete the contents of the `Home` page.  
Make sure to push it live.

3. **Site Content > Site Rewrites > Advanced Rewrites tab**  
Replace any existing reirects in the text box with `/(.+) /`

4. Navagate to the site's home page and refresh with `?cache=0`  
Page should display nothing but `The requested page is unavailable.`
