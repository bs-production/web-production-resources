# <i class="fas fa-align-left"></i> Photo Upload
***

``` php
<?php
  if (!empty($_POST))
  {
    if (isset($_FILES['form_logger_Photo']['name']) and !empty($_FILES['form_logger_Photo']['name'])) {
      	   // create and return temp url
      	    require_once(ENV_ROOT.'/portal/config/cloudfiles_config.php');
      	    require_once(ENV_ROOT.'/vendor/omissis/php-cloudfiles/cloudfiles.php'); //use the cloudfiles library
      	    $key = '4975b742ce26416b9b22373ea2f911b3';
      	    $maxUploadSize = 104857600; //100MB
      	    $auth = new CF_Authentication($cloudfilesConfig['username'], $cloudfilesConfig['password']); //set up to connect to the cloudfiles server with our API key
      	    $auth->authenticate(); //do the authentication
      	    $conn = new CF_Connection($auth); //set up for a new connection to the CloudFiles server with our auth
      	    $container = $conn->get_container('dealer-forms');
            $company = 'Company';
      	    $filename = $company .'-'. uniqid().'-'.$_FILES['form_logger_Photo']['name'];
            $filename = str_replace(' ', '-', $filename);
            $filename = preg_replace('/\s+/', '-', $filename);
      	    $file = $container -> create_object($filename);
            $fp = file_get_contents($_FILES['form_logger_Photo']['tmp_name'], "r"); //open the file into PHP
            $size = $_FILES['form_logger_Photo']['size']; //put file size here
            if ($_FILES['form_logger_Photo']['size'] < $maxUploadSize) {
                $file->write($fp, $size);
            }
      	   $timeout = 600*5;
      	   $fullURL = $file->public_uri($key, $timeout, 'PUT');
      	   $rack_url = preg_replace('#^http?://#', '', rtrim($fullURL,'/'));
      	   $_POST['form_logger_Message'] .= "
<br><br>" . "<strong>Image or Video URL:</strong> " . $fullURL;
      }
  require_once ENV_ROOT.'/vendor/swiftmailer/swiftmailer/lib/swift_required.php';
  $emailBody = '
     <p><strong>Full Name:</strong> '.$_POST['form_logger_Full_Name'].'</p>
     <p><strong>Address:</strong><br> '.$_POST['form_logger_Street'].'<br>
     '.$_POST['form_logger_City'].', '.$_POST['form_logger_State'].', '.$_POST['form_logger_Zip_Code'].'</p>
     <p><strong>Phone:</strong> '.$_POST['form_logger_Phone'].'</p>
     <p><strong>Email:</strong> '.$_POST['form_logger_Email_Address'].'</p>
     <p><strong>Phone:</strong> '.$_POST['form_logger_Phone'].'</p>
     <p><strong>Warranty Work Needed:</strong> '.$_POST['form_logger_Message'].'</p>
     <p><strong>Photo:</strong> '.$_POST['form_logger_Photo'].'</p>
  ';
    $mailer = Swift_Mailer::newInstance(Swift_MailTransport::newInstance());
    $message = Swift_Message::newInstance();
    $message->setFrom(array('no-reply@recipient.com' => 'Subject'));
    $message->setTo(array('recipient@xxx.com' => 'Recipient'));
    $message->setBcc('basementsystems.emailcache@gmail.com');
    $message->setSubject('Subject: '.$_POST['form_logger_Name'].'');
    $message->setBody($emailBody, 'text/html');
    $mailer->send($message);
  // Store data in logger image won't be saved
          global $siteData, $siteDefineData;
          require_once ENV_ROOT.'/portal/libraries/formLogger.api.php';
          $logger = new formLoggerApi();
          $logger->setSiteId($siteData['site.id']);
          $logger->setSessionId($siteDefineData['cms_tracking_sessions']['session.id']);
          $logger->setFormId('form_logger_');
          $logger->setFormName('College_Scholarship');
          $logger->setcustomEmailSubject('Building Solid Foundations Scholarship submission');
      if ($logger->saveData($_POST)) {
            echo '<h1>Thank you ' . $name . ' for your submission!</h1><p>We have received your entry, and will be reviewing your information.</p><style>.contact_form {display:none;}</style>';
        } else {
            echo '<div><h1 class="oops">Oops, it looks like something went wrong.</h1>
            <a class="button" href="[page_url:152763]">Please resubmit your entry</a></div>';
        }
  }
?>
<style>
  .contact_form form {
    width: 100%;
}
.contact_form.module, .contact_form.page_widget {
    float: none;
}
.contact_form.module .fname, .contact_form.page_widget .fname {
    padding-right: 2%;
}
.contact_form.module .address input, .contact_form.page_widget .address input {
    width: 98%;
}
.contact_form.module .zip input, .contact_form.page_widget .zip input {
    width: 107%;
}
.contact_form .form_fields input, .contact_form textarea {
    width: 98% !important;
}
</style>
<div class="row">
<div class="small-3 columns">
  <img src="http://d6449bb3dc657045bfc9-290115cc0d6de62a29c33db202ae565c.r80.cf1.rackcdn.com/283/Warranty_Page_FBP.jpg" alt="">
  </div>
  <div class="small-9 columns">
  <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatibus exercitationem omnis rerum non repellat, placeat est suscipit accusamus vitae sapiente neque odit inventore porro ducimus! Natus aliquam libero voluptatem corporis.
  </div>
</div>
<div class="row">
<div class="contact_form page_widget">
<h3>Please Enter Your Information</h3>
<form action="" method="post" id="contact_form" enctype="multipart/form-data">
        <div class="fname">
            <label for="Full_Name">Full Name: <span>*</span></label>
            <input type="text" name="form_logger_Full_Name" maxlength="50" class="required" id="Full_Name">
        </div>
        <div class="email">
            <label for="Email_Address">Email: <span>*</span></label>
            <input type="text" name="form_logger_Email_Address" maxlength="50" class="required email" id="Email_Address">
        </div>
        <div class="address">
            <label for="Street">Street: <span>*</span></label>
            <input type="text" name="form_logger_Street" maxlength="50" class="required" id="Street">
        </div>
        <div class="city">
            <label for="City">City: <span>*</span></label>
            <input type="text" name="form_logger_City" maxlength="50" class="required" value="" id="City">
        </div>
        <div class="state">
            <label for="State">State: <span>*</span></label>
            <select name="form_logger_State" class="required" id="State">
                <option value="" selected="selected">Please select...</option>
                <option value="AL">Alabama</option>
                <option value="AK">Alaska</option>
                <option value="AZ">Arizona</option>
                <option value="AR">Arkansas</option>
                <option value="CA">California</option>
                <option value="CO">Colorado</option>
                <option value="CT">Connecticut</option>
                <option value="DE">Delaware</option>
                <option value="DC">District Of Columbia</option>
                <option value="FL">Florida</option>
                <option value="GA">Georgia</option>
                <option value="HI">Hawaii</option>
                <option value="ID">Idaho</option>
                <option value="IL">Illinois</option>
                <option value="IN">Indiana</option>
                <option value="IA">Iowa</option>
                <option value="KS">Kansas</option>
                <option value="KY">Kentucky</option>
                <option value="LA">Louisiana</option>
                <option value="ME">Maine</option>
                <option value="MD">Maryland</option>
                <option value="MA">Massachusetts</option>
                <option value="MI">Michigan</option>
                <option value="MN">Minnesota</option>
                <option value="MS">Mississippi</option>
                <option value="MO">Missouri</option>
                <option value="MT">Montana</option>
                <option value="NE">Nebraska</option>
                <option value="NV">Nevada</option>
                <option value="NH">New Hampshire</option>
                <option value="NJ">New Jersey</option>
                <option value="NM">New Mexico</option>
                <option value="NY">New York</option>
                <option value="NC">North Carolina</option>
                <option value="ND">North Dakota</option>
                <option value="OH">Ohio</option>
                <option value="OK">Oklahoma</option>
                <option value="OR">Oregon</option>
                <option value="PA">Pennsylvania</option>
                <option value="RI">Rhode Island</option>
                <option value="SC">South Carolina</option>
                <option value="SD">South Dakota</option>
                <option value="TN">Tennessee</option>
                <option value="TX">Texas</option>
                <option value="UT">Utah</option>
                <option value="VT">Vermont</option>
                <option value="VA">Virginia</option>
                <option value="WA">Washington</option>
                <option value="WV">West Virginia</option>
                <option value="WI">Wisconsin</option>
                <option value="WY">Wyoming</option>
            </select>
        </div>
        <div class="zip">
            <label for="Zip">Zip Code: <span>*</span></label>
            <input type="text" name="form_logger_Zip_Code" maxlength="10" class="required zipcode" value="" id="Zip">
        </div>
        <div class="phone">
            <label for="Phone">Phone: <span>*</span></label>
            <input type="text" name="form_logger_Phone" maxlength="50" class="required phone" id="Phone">
        </div>

        <div class="comment">
        <h3>Warranty Work Needed</h3>
            <label for="Message">Please provide us more information on your warranty request: <span>*</span> </label>
            <textarea value="Comments:" name="form_logger_Message" id="Message"></textarea>
        </div>
        <div class="photos">
        <h3>Submit Photos Related To Your Request</h3>
            <label for="Message">Select photos from your computer: <span>*</span></label>
            <input class="photo" name="form_logger_Photo" type="file" value="photo" id="photo">
        </div>
        <div class="submit">
            <input class="submit" name="send" type="submit" value="Send" id="save">
        </div>
    </form>
</div>
</div>
<hr>
```