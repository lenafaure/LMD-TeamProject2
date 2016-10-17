
#The `<form>` Element Explained
The HTML `<form>` tag is used to create any form that requires user input. The form section of a document can contain markup, normal content, special elements called controls, which include checkboxes, radio buttons, menus, textfields and more.

Forms are primarily used to pass user-data to a specifed URL. In layman's terms, forms are how we get input from the user, i.e. names, emails, contact information, birthdays, etc. 

You've probably filled out a thousand forms before, they all too common. But making them is a different story. 

###Understanding the Lingo
Let's first get acquainted with the elements you'll have at your disposal, when building forms of all sorts.

All forms start and end with a `<form>` and `</form>`, repectively.

You will add any elements you use, within the `<form></form>` markup.

```
<form>
	<!-- form elements go here. -->
</form>
```

##List of HTML Form Elements
Forms can have quite a few input options you can utilize, as mentioned above. Let's break down all the options available :

| Tag           | Description   |
| ------------- |:-------------:|
| `<button>`     | Defined clickable button |
| `<datalist>`| Specifies list of pre-defined options for input controls ![](https://developer.blackberry.com/html5/files/apis/v2_2/images/html5_logo_16x16.png) |
| `<fieldset>`| Groups related elements in form  |
| `<form>`| Defines HTML form for user input  |
| `<input>`| Defines input control  |
| `<keygen>`| Defines key-pair generator field ![](https://developer.blackberry.com/html5/files/apis/v2_2/images/html5_logo_16x16.png)  |
| `<label>`| Defines label for `<input>` element  |
| `<legend>`| Defines caption for `<fieldset>` element  |
| `<optgroup>`| Defines group of related options in dropdown list  |
| `<option>`| Defines option in dropdown list       |
| `<output>`   | Defines result of a calculation ![](https://developer.blackberry.com/html5/files/apis/v2_2/images/html5_logo_16x16.png)  |
| `<textarea>`| multi-line text input control      |



##Element Examples
Here are some HTML form element examples to give you an idea of what simple and slightly more complex forms could like.  

######Input Text Example
this: 

```
 <input type="text" name="name" class="name" placeholder="McLuvin" pattern="^[( )a-zA-Z]+$" required />
```
translates to this:

 <input type="text" name="name" class="name" placeholder="McLuvin" pattern="^[( )a-zA-Z]+$" required />
 
####Optin Form HTML Example
this: 

```
<form>
  <fieldset class="account-login">
    <label>Username</label>
    <input type="text" name="username">
    <label>Password</label>
    <input type="text" name="password">
  </fieldset>
  <fieldset class="account-action">
    <input type="submit" class="btn" name="submit" value="Login">
    <label>
      <input type="checkbox" name="remember-me" checked> Stay logged in
    </label>
  </fieldset>
</form>
```
translates to this: 
<form>
  <fieldset class="account-login">
    <label>Username</label>
    <input type="text" name="username">
    <label>Password</label>
    <input type="text" name="password">
  </fieldset>
  <fieldset class="account-action">
    <input type="submit" class="btn" name="submit" value="Login">
    <label>
      <input type="checkbox" name="remember-me" checked> Stay logged in
    </label>
  </fieldset>
</form>



#### Contact Form
this: 

```
<form>
	<input name="name" placeholder="What is your name?" class="name" required />
	<input name="emailaddress" placeholder="What is your email?" class="email" type="email" required />
    <textarea rows="4" cols="50" name="subject" placeholder="Please enter your message" class="message" required></textarea>
    <input name="submit" class="btn" type="submit" value="Send" />
</form>
```
translates to this:

<form>
	<input name="name" placeholder="What is your name?" class="name" required />
	<input name="emailaddress" placeholder="What is your email?" class="email" type="email" required />
    <textarea rows="4" cols="50" name="subject" placeholder="Please enter your message" class="message" required></textarea>
    <input name="submit" class="btn" type="submit" value="Send" />
</form>

#### SignUp Form HTML Example
this:

```
<form>   
    <fieldset class="account-info">  
    <input type="text" name="first-name" placeholder="First Name">
    <input type="text" name="last-name" placeholder="Last Name">
    <input type="email" name="email-address" id="email" placeholder="name@example.com" required>
    <input type="tel" name="phone-number" id="tel" placeholder="Phone Number">
    <input type="text" name="password" placeholder="Password (At least 7 characters)">
    <input type="text" name="city" placeholder="City">
    <input type="text" name="invite-code" placeholder="Invite Code (optional)">
    </fieldset>
  <fieldset class="account-action">
    <input type="submit" class="btn" name="next" value="Next">
  </fieldset>
</form>

```

translates to this:

<form>   
    <fieldset class="account-info">  
    <input type="text" name="first-name" placeholder="First Name">
    <input type="text" name="last-name" placeholder="Last Name">
    <input type="email" name="email-address" id="email" placeholder="name@example.com" required>
    <input type="tel" name="phone-number" id="tel" placeholder="Phone Number">
    <input type="text" name="password" placeholder="Password (At least 7 characters)">
    <input type="text" name="city" placeholder="City">
    <input type="text" name="invite-code" placeholder="Invite Code (optional)">
    </fieldset>
  <fieldset class="account-action">
    <input type="submit" class="btn" name="next" value="Next">
  </fieldset>
</form>








