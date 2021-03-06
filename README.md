# Client-side PSR-7 Oauth1 request signer for PHP `^7.0`

[![Build Status](https://travis-ci.org/php-api-clients/psr7-oauth1.svg?branch=master)](https://travis-ci.org/php-api-clients/psr7-oauth1)
[![Latest Stable Version](https://poser.pugx.org/api-clients/psr7-oauth1/v/stable.png)](https://packagist.org/packages/api-clients/psr7-oauth1)
[![Total Downloads](https://poser.pugx.org/api-clients/psr7-oauth1/downloads.png)](https://packagist.org/packages/api-clients/psr7-oauth1/stats)
[![Code Coverage](https://scrutinizer-ci.com/g/php-api-clients/psr7-oauth1/badges/coverage.png?b=master)](https://scrutinizer-ci.com/g/php-api-clients/psr7-oauth1/?branch=master)
[![License](https://poser.pugx.org/api-clients/psr7-oauth1/license.png)](https://packagist.org/packages/api-clients/psr7-oauth1)
[![PHP 7 ready](http://php7ready.timesplinter.ch/php-api-clients/psr7-oauth1/badge.svg)](https://appveyor-ci.org/php-api-clients/psr7-oauth1)

# Installation

To install via [Composer](http://getcomposer.org/), use the command below, it will automatically detect the latest version and bind it with `^`.

```bash
composer require api-clients/psr7-oauth1 
```

In case you need to support `5.5+` as well in your package, we suggest you use the following command:

```bash
composer require api-clients/psr7-oauth1:^1.0
```

However since `1.0` and `2.0` of this package are 100% compatible, we recommend you use the following command to support both:

```bash
composer require "api-clients/psr7-oauth1:^2.0 || ^1.0" 
```

# Example

```php
<?php

use ApiClients\Tools\Psr7\Oauth1\Definition;
use ApiClients\Tools\Psr7\Oauth1\RequestSigning\RequestSigner;
use ApiClients\Tools\Psr7\Oauth1\Signature\HmacSha1Signature;

// Pass it a PSR-7 request and it returns a signed PSR7 request you can use in any PSR7 capable HTTP client.
// By default a HMAC-SHA1 signature will be used, this can be changed, see examples below how to do that.
$request = (new RequestSigner(
    new Definition\ConsumerKey('consumer_key'),
    new Definition\ConsumerSecret('consumer_secret')
))->withAccessToken(
    new Definition\AccessToken('token_key'),
    new Definition\TokenSecret('token_secret')
)->sign($request);
```

# Suppported signatures

All supported signatures are HMAC signatures.

## MD5

Signs request with `HMAC-MD5`. Usage:

```php
<?php

use ApiClients\Tools\Psr7\Oauth1\Definition;
use ApiClients\Tools\Psr7\Oauth1\RequestSigning\RequestSigner;
use ApiClients\Tools\Psr7\Oauth1\Signature\HmacMd5Signature;

$consumerSecret = new Definition\ConsumerSecret('consumer_secret');
$requestSigner = new RequestSigner(
    new Definition\ConsumerKey('consumer_key'),
    $consumerSecret,
    new HmacMd5Signature($consumerSecret)
);
```

## SHA1

Signs request using `HMAC-SHA1`. Usage:

```php
<?php

use ApiClients\Tools\Psr7\Oauth1\Definition;
use ApiClients\Tools\Psr7\Oauth1\RequestSigning\RequestSigner;
use ApiClients\Tools\Psr7\Oauth1\Signature\HmacSha1Signature;

$consumerSecret = new Definition\ConsumerSecret('consumer_secret');
$requestSigner = new RequestSigner(
    new Definition\ConsumerKey('consumer_key'),
    $consumerSecret,
    new HmacSha1Signature($consumerSecret)
);
```

## SHA256

Signs request using `HMAC-SHA256`. Usage:

```php
<?php

use ApiClients\Tools\Psr7\Oauth1\Definition;
use ApiClients\Tools\Psr7\Oauth1\RequestSigning\RequestSigner;
use ApiClients\Tools\Psr7\Oauth1\Signature\HmacSha256Signature;

$consumerSecret = new Definition\ConsumerSecret('consumer_secret');
$requestSigner = new RequestSigner(
    new Definition\ConsumerKey('consumer_key'),
    $consumerSecret,
    new HmacSha256Signature($consumerSecret)
);
```

## SHA384

Signs request using `HMAC-SHA384`. Usage:

```php
<?php

use ApiClients\Tools\Psr7\Oauth1\Definition;
use ApiClients\Tools\Psr7\Oauth1\RequestSigning\RequestSigner;
use ApiClients\Tools\Psr7\Oauth1\Signature\HmacSha384Signature;

$consumerSecret = new Definition\ConsumerSecret('consumer_secret');
$requestSigner = new RequestSigner(
    new Definition\ConsumerKey('consumer_key'),
    $consumerSecret,
    new HmacSha384Signature($consumerSecret)
);
```

## SHA512

Signs request using `HMAC-SHA512`. Usage:

```php
<?php

use ApiClients\Tools\Psr7\Oauth1\Definition;
use ApiClients\Tools\Psr7\Oauth1\RequestSigning\RequestSigner;
use ApiClients\Tools\Psr7\Oauth1\Signature\HmacSha512Signature;

$consumerSecret = new Definition\ConsumerSecret('consumer_secret');
$requestSigner = new RequestSigner(
    new Definition\ConsumerKey('consumer_key'),
    $consumerSecret,
    new HmacSha512Signature($consumerSecret)
);
```

# Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

# License

The MIT License (MIT)

Copyright (c) 2016 Cees-Jan Kiewiet & Beau Simensen

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
