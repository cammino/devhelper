# DEVHELPER
General snippets and tips for quick development

# Sumary
- HTML
- CSS
    - SASS
- Javascript
    - General
        - Functions to manage cookies easily
    - jQuery
    - jQuery Validate
        - Translating error messages
- PHP
    - General
        - Using Try/Catch
        - Forcing Charset
- RUBY

# Javascript
## General
### Functions to manage cookies easily
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
