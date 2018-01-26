# php-enum

> This class gives the ability to emulate and get enumeration data natively in PHP.

- You can convert enum values easily.
- requires php>=5.6.0, because array constant are used.

## Getting started

### Install
```shell
composer require ginnerpeace/php-enum
```

### Example
Create a class for an enum data, like this:
```php
<?php

namespace PHPEnum\Demo;

use PHPEnum\Enum;

/**
 * custom global request code
 */
class RequestCode extends Enum
{
    CONST SUCCESS = 0;
    CONST ERROR = 1;

    CONST __DICT = [
        self::SUCCESS => 'request success',
        self::ERROR   => 'request failure',
    ];
}
```

### Use
```php
<?php

// Use value.
////////////////////////////////////////////////////////////////////////////
RequestCode::SUCCESS;                   // 0
RequestCode::ERROR;                     // 1
////////////////////////////////////////////////////////////////////////////

// Determine if the name has been in Enum.
////////////////////////////////////////////////////////////////////////////
RequestCode::hasName('SUCCESS');        // true
RequestCode::hasName('TEST');           // false
////////////////////////////////////////////////////////////////////////////

// Determine if the name has been in Enum.
// Using strict comparison usually, unless strict is set to false.
////////////////////////////////////////////////////////////////////////////
RequestCode::hasValue(1);               // true
RequestCode::hasValue('1');             // false

RequestCode::hasValue('1', false);      // true
RequestCode::hasValue(9);               // false
////////////////////////////////////////////////////////////////////////////

// Value & Name, convert each other.
////////////////////////////////////////////////////////////////////////////
RequestCode::nameToValue('SUCCESS');    // 0
RequestCode::nameToValue('TEST');       // throw UnexpectedValueException

RequestCode::valueToName(1);            // 'ERROR'
RequestCode::valueToName(9);            // throw UnexpectedValueException
////////////////////////////////////////////////////////////////////////////

// Translate the given constant name/value to the display value.
////////////////////////////////////////////////////////////////////////////
RequestCode::transName('ERROR');        // 'request failure'
RequestCode::transName('TEST');         // 'TEST'

RequestCode::transValue(0);             // 'request success'
RequestCode::transValue(9);             // 9
////////////////////////////////////////////////////////////////////////////

// Some Getter methods.
////////////////////////////////////////////////////////////////////////////
RequestCode::getMap();
return:
[
    'SUCCESS' => 0,
    'ERROR' => 1,
]

RequestCode::getNameMap();
return:
[
    0 => 'SUCCESS',
    1 => 'ERROR',
]

RequestCode::getDict();
return:
[
    0 => 'request success',
    1 => 'request failure',
]

RequestCode::getNameDict();
return:
[
    'SUCCESS' => 'request success',
    'ERROR' => 'request failure',
]
////////////////////////////////////////////////////////////////////////////
```
