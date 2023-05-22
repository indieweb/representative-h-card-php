Representative H-Card Parsing
=============================

[![Build Status](https://travis-ci.org/indieweb/representative-h-card-php.png?branch=master)](http://travis-ci.org/indieweb/representative-h-card-php)
[![Packagist](https://img.shields.io/packagist/v/indieweb/representative-h-card.svg)](https://packagist.org/packages/indieweb/representative-h-card)

Given a parsed mf2 document, return the [representative h-card](http://microformats.org/wiki/representative-h-card-parsing) for the page.


Installation
------------

Install via composer:

```json
{
  "indieweb/representative-h-card": "0.1.*"
}
```

Or just require the one file:

```php
require_once('src/mf2/representative-h-card.php');
```

Usage
-----

This function accepts a PHP array in the format returned by the [microformats2 parser](https://github.com/indieweb/php-mf2).

```php
$url = 'http://aaronparecki.com/';
$html = file_get_contents($url);
$parsed = Mf2\parse($html, $url);
$representative = Mf2\HCard\representative($parsed, $url);
print_r($representative);
```

The function will find the representative h-card (according to the [representative h-card parsing](http://microformats.org/wiki/representative-h-card-parsing) rules) and will
return the h-card that is found.

```
Array
(
    [type] => Array
        (
            [0] => h-card
        )
    [properties] => Array
        (
            [name] => Array
                (
                    [0] => Aaron Parecki
                )
            [photo] => Array
                (
                    [0] => http://aaronparecki.com/images/aaronpk.png
                )
            [url] => Array
                (
                    [0] => http://aaronparecki.com/
                )
            [uid] => Array
                (
                    [0] => http://aaronparecki.com/
                )
        )
)
```
