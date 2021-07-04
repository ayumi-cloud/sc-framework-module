## Summer CMS Developer Validating and Sanitizing Data API

### Validating and Sanitizing

Sanitizing and validating user input is one of the most common tasks in a web application. To make this task easier Summer CMS provides a native filter module that you can use to sanitize or validate data.

Common use cases for the module include cleaning the user input data for the frontend and backend forms, cleaning the data being read and written to the config files, cleaning the data being sent and recieved from the database, cookies, local and session storage, trust tokens etc.

The module also converts formats such as encoding and enconding. For example, an associative array into a JSON object.

For larger more complex sanitization and validation methods third-party libraries have been used as they pffer the highest level of complete protection, below mentions a few third-party libraries being used:

 - [HTML Purifier](http://htmlpurifier.org/) - a `HTML` filter that guards against XSS and ensures standards-compliant output.
 - [DOMPurify](https://github.com/cure53/DOMPurify) - a DOM-only, super-fast, uber-tolerant XSS sanitizer for `HTML`, `MathML` and `SVG`.
 - [JSON5](https://github.com/json5/json5) - a superset of `JSON` which allows comments, trailing commas, single-quoted strings and more. Including a parser to allow encoding and decoding JSON-Object strings into JSON objects and vice versa.
- [Laravel (Validation)](https://laravel.com/docs/master/validation) - laravel includes a wide variety of convenient validation rules that you may apply to data, even providing the ability to validate if values are unique in a given database table.
- [OpenType Sanitizer](https://github.com/khaledhosny/ots) - parses and serializes OpenType files (OTF, TTF) and WOFF and WOFF2 font files, validating them and sanitizing them as it goes.
- [ImageMagick](https://github.com/ImageMagick/ImageMagick) - it can read and write images in a variety of formats (over 200) including PNG, JPEG, GIF, HEIC, TIFF, DPX, EXR, WebP, Postscript, PDF, and SVG.
- [libavif](https://github.com/AOMediaCodec/libavif) - is a portable C implementation of the AV1 Image File Format. It is a work-in-progress, but can already encode and decode all AOM supported YUV formats and bit depths (with alpha).

https://symfony.com/doc/current/validation.html

=== TO DO ===

- `YAML`
- `XML`
- `Twig`
- `CSS`

- Image codecs
- GD PHP

Below shows which libraries are being used to clean each coding language:

Programming language | Third party library | Description
---|---|---
HTML | HTML Purifier | Sanitization
Javascript | DOMPurify | Sanitization
JSON | JSON5 | Parser
PHP | Laravel | Validation
MathML | DOMPurify | Sanitization
SVG | DOMPurify | Sanitization



=== TO DO ===

Invalid sanitization and validation methods are sent to the error module for the developer to view the stack trace. Also the data is sent to the analytics section for full chart analysis.

### API's

- [HTML Sanitizer API](https://wicg.github.io/sanitizer-api/)
- [Trusted Types API](https://w3c.github.io/webappsec-trusted-types/dist/spec/)

Some libraries already generate Trusted Types that you can pass to the sink functions. For example, DOMPurify supports Trusted Types and will return sanitized HTML wrapped in a `TrustedHTML` object such that the browser does not generate a violation.

### Validating and Sanitizing API

To run a validation command use Laravel's `Validator` and to run a sanitization command use Summer CMS's `Sanitize`, for example `Sanitize::cleanNumber();`

Value | Description
---|---
removeNullCharacters | Remove null characters.
validateStandardCharacterEntities | Validate Standard Character Entities.








cleanNumber | Sanitizing int and float numbers.
cleanUrl | Sanitizing full url's (can include: scheme, host, port, user, pass, path, query, fragment).
cleanPath | Sanitizing uri path only (excluding query and fragment).
cleanUrlConvertUri | Sanitizing full uri's (can include: paths, fragment, query).
cleanUrlConvertHost | Sanitizing url host only (can include: subdomains).
cleanUrlConvertScheme | Sanitizing url scheme only.
cleanDomain | Sanitizing url domain (can include: scheme, host, port, user, pass).
cleanBoolean | Sanitizing boolean.
cleanJson | Sanitizing, parser decoding and encoding.
cleanIp | Sanitizing ipv4 and/or ipv6 addresses.
cleanIpApache | Sanitizing ipv4 and/or ipv6 addresses for Apache.
cleanIpv4 | Sanitizing ipv4 addresses only.
cleanIpv6 | Sanitizing ipv6 addresses only.
cleanString | Sanitizing strings.
cleanUserAgent | Sanitizing user agents.
cleanNormalize | Normalize a string.
cleanDateTime | Sanitizing Date or Date and Time.



cleanEmail | x

cleanMinMaxRange | x

cleanDateRange | x

cleanDateTimeRange | x

cleanArray | x

cleanObject | x


..

=== TO DO ===

### Extended Validating and Sanitizing API

..

=== TO DO ===

### Sanitizing HTML API

Because this is using the HTMLPurifier library to run a html sanitization command use Summer CMS's `Purifier`, for example:

default
```php
clean(Input::get('inputname'));
```
or

```php
Purifier::clean(Input::get('inputname'));
```

dynamic config
```php
clean('This is my H1 title', 'titles');
clean('This is my H1 title', array('Attr.EnableID' => true));
```
or

```php
Purifier::clean('This is my H1 title', 'titles');
Purifier::clean('This is my H1 title', array('Attr.EnableID' => true));
```

use [URI filter](http://htmlpurifier.org/docs/enduser-uri-filter.html)

```php
Purifier::clean('This is my H1 title', 'titles', function (HTMLPurifier_Config $config) {
    $uri = $config->getDefinition('URI');
    $uri->addFilter(new HTMLPurifier_URIFilter_NameOfFilter(), $config);
});
```

### Javascript .. etc.

=== TO DO ===

(*) Subject to adding more features as time goes on.
