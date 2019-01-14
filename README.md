# php-aliyun-open-api-live

[![Build Status](https://travis-ci.org/aliyunapi/php-aliyun-open-api-live.svg?branch=master)](https://travis-ci.org/aliyunapi/php-aliyun-open-api-live)
[![Latest Stable Version](https://poser.pugx.org/aliyunapi/php-aliyun-open-api-live/v/stable.png)](https://packagist.org/packages/aliyunapi/php-aliyun-open-api-live)
[![Total Downloads](https://poser.pugx.org/aliyunapi/php-aliyun-open-api-live/downloads.png)](https://packagist.org/packages/aliyunapi/php-aliyun-open-api-live)

Installation
------------


```
"vitta/php-aliyun-open-api-live": "~1.1.3"
```

to the require section of your composer.json.

使用方式
------------
```
$live = new \aliyun\live\Client([
    'accessKeyId' => '123456',
    'accessSecret' => '123456'
    'appName' => 'live',
    'domain' => 'live.cctv.com',
    'pushAuth' => '1234567',
    'sidePushDomain' => 'your push url',
    'sidePlayDomain' => 'you play url'
]);

//发送接口请求
$package = [
    'Action' => 'DescribeLiveStreamsPublishList',
    'DomainName' => 'live.cctv.com',
    'StartTime' => gmdate('Y-m-d\TH:i:s\Z', strtotime('2017-03-15')),
    'EndTime' => gmdate('Y-m-d\TH:i:s\Z', strtotime('2017-04-01')),
];
$response = $live->createRequest($package);
print_r($response);
//非请求接口
生成推流地址
$live->getPushPath();
$live->getPushArg($uuid);
生成边缘推流地址
$live->getSidePushUrl($streamName)
//获取播放地址
$live->getPlayUrls($uuid);
获取边缘播放地址
$live->getPlayUrls($stream, true);

exit;
```