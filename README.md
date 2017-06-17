# DEVHELPER
General snippets and tips for quick development

# Sumary
- HTML
- CSS
    - SASS
- [Javascript](#javascript)
    - [General](#javascriptgeneral)
        - [Functions to manage cookies easily](#javascriptmanagecookie)
        - Parsing and using JSON
    - jQuery
    - jQuery Validate
        - Translating error messages
- PHP
    - General
        - Using Try/Catch
        - Forcing Charset
- RUBY
- HOSTING
    - Hostgator
        -- Configuring PHPMailer

# Javascript<a name="javascript"></a>
## General<a name="javascriptgeneral"></a>
### Functions to manage cookies easily<a name="javascriptmanagecookie"></a>
```javascript
function setCookie(name, value, days) {
    var expires;

    if (days) {
        var date = new Date();
        date.setTime(date.getTime() + (days * 24 * 60 * 60 * 1000));
        expires = "; expires=" + date.toGMTString();
    } else {
        expires = "";
    }
    document.cookie = encodeURIComponent(name) + "=" + encodeURIComponent(value) + expires + "; path=/";
}

function getCookie(name) {
    var nameEQ = encodeURIComponent(name) + "=";
    var ca = document.cookie.split(';');
    for (var i = 0; i < ca.length; i++) {
        var c = ca[i];
        while (c.charAt(0) === ' ') c = c.substring(1, c.length);
        if (c.indexOf(nameEQ) === 0) return decodeURIComponent(c.substring(nameEQ.length, c.length));
    }
    return null;
}

function delCookie(name) {
    setCookie(name, "", -1);
}
```
### Parsing and using JSON
```javascript
var data = '{"message":"something here.."}';
data = JSON.parse(data);
console.log(data.message);
```
## jQuery Validate
### Translating error messages
```javascript
jQuery.extend(jQuery.validator.messages, {
    required: "Campo Obrigatório.",
    email: "Email inválido.",
});
```   
# PHP
## General
### Using try/catch
```php
<?php
try{
    // Do something
}catch(Exception $e) {
    // Error message
    $e->getMessage(); 
}
```
### Forcing charset
```php
<?php header ('Content-type: text/html; charset=UTF-8'); ?>
<?php header ('Content-type: text/html; charset=ISO-8859-1'); ?>
```

# Hosting
## Hostgator
### Configuring PHPMailer
```php
<?php
include("PHPMailer/PHPMailerAutoload.php");

$mail = new PHPMailer;
$mail->isSMTP(); 
$mail->Host = 'mail.domain.com.br';
$mail->SMTPAuth = true;
$mail->Username = 'some-email@domain.com.br';
$mail->Password = 'password here';
$mail->SMTPSecure = 'tls';
$mail->Port = 587;

$mail->setFrom('some-email@domain.com.br', 'Domain Name');
$mail->addAddress('receiver-email@domain.com.br');
$mail->isHTML(true);

$mail->Subject = 'Here is the subject';
$mail->Body    = 'This is the HTML message body <b>in bold!</b>';
$mail->AltBody = 'This is the body in plain text for non-HTML mail clients';

if(!$mail->send()) {
    echo 'Message could not be sent.';
    echo 'Mailer Error: ' . $mail->ErrorInfo;
} else {
    echo 'Message has been sent';
}
```
