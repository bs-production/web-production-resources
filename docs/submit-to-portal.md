# <i class="fas fa-align-left"></i> Submit to Portal
``` html
<form action="/free-estimate/confirmation.html" method="post" id="contact_form">
    <div class="name">
        <input placeholder="First Name" type="text" name="First_Name" maxlength="50" class="required" id="First_Name">
        <input placeholder="Last Name" type="text" name="Last_Name" maxlength="50" class="required" id="Last_Name">
    </div>
    <div class="address">
        <input placeholder="Street" type="text" name="Street" maxlength="50" class="required" id="Street">
        <input placeholder="City" type="text" name="City" maxlength="50" class="required" value="" id="City">
    </div>
    <div class="state">
        <select name="State" class="required" id="State" style="width: 185px">
            <option value="" selected="selected">State</option>
            <option value="CO">Colorado</option>
            <option value="NE">Nebraska</option>
        </select>
        <input placeholder="Zip Code" type="text" name="Zip_Code" maxlength="10" class="required zipcode" value="" id="Zip">
    </div>
    <div class="phone">
        <input placeholder="Phone" type="text" name="Phone" maxlength="50" class="required phone" id="Phone">
    </div>
    <div class="email">
        <input placeholder="Email" type="text" name="Email_Address" maxlength="50" class="required email" id="Email_Address">
    </div>
    <input type="hidden" name="save" value="save">
    <div class="submit">
        <input class="submit" name="send" type="submit" value="Send" id="save">
    </div>
</form>
```
