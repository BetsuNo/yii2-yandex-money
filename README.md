Yii2 component for Yandex Money integration in your web applications
===================================================================

This repo is fork of [grigorieff/yii2-yandex-money](https://github.com/grigorieff/yii2-yandex-money) 
was made because there was no stable release.

Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
php composer.phar require --prefer-dist betsuno/yii2-yandex-money "*"
```

or add

```
"betsuno/yii2-yandex-money": "*"
```

to the require section of your composer.json.

Configuration
------------

Add to your app config:

```php
    'components' => [

        .........

        'ym' => [
            'class'         => 'betsuno\yii2yandexMoney\YMComponent',
            'client_id'     => '......',
            'code'          => '......',
            'redirect_uri'  => '......',
            'client_secret' => '......'
        ],

        .........

    ];
```

Usage
-----

```php
$ym = Yii::$app->ym->api;

// get account info

$accountInfo = $ym->accountInfo();

.......

// get operation history with last 3 records
$operationHistory = $ym->operationHistory(['records' => 3]);

......

// make request payment
$requestPayment = $ym->requestPayment([
    'pattern_id' => 'p2p',
    'to'         => $money_wallet,
    'amount_due' => $amount_due,
    'comment'    => $comment,
    'message'    => $message,
    'label'      => $label,
]);

......

// call process payment to finish payment
$processPayment = $ym->processPayment([
    'request_id' => $request_payment->request_id,
]);

......

```

License
-------

MIT

Requirements
------------
This Yii2 component requires:
* [Yii 2 framework][1]
* [Yandex Money SDK][2]

[1]:https://github.com/yiisoft/yii2
[2]:https://github.com/yandex-money/yandex-money-sdk-php
