# DEVHELPER
General snippets and tips for development

## Sumary
- jQuery Validator
- PHP

## PHP
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
### Force charset
```php
<?php header ('Content-type: text/html; charset=UTF-8'); ?>
<?php header ('Content-type: text/html; charset=ISO-8859-1'); ?>
```

## jQuery Validator
### Translate error messages
```javascript
jQuery.extend(jQuery.validator.messages, {
    required: "Campo Obrigatório.",
    email: "Email inválido.",
});
```
