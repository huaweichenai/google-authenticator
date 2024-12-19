基于Google Authenticator双因素身份验证实现动态码验证
==============================

## Installation<br>
```
composer require huaweichenai/google-authenticator
```

Usage:
------

* 1：创建密钥

```php
$authenticator = new Authenticator();
$secret = $authenticator->createSecret();
```

* 2：获取手机端扫描二维码链接(用于手机端获取动态口令)

```php
$authenticator = new Authenticator();
$qrCodeUrl  = $authenticator->getQRCodeGoogleUrl('username', $secret, 'title');
```

不支持使用此方法，此方法向第三方分享了你的安全性，建议使用下面的方法获取二维码信息自行生成二维码

* 3：获取手机端扫描二维码的信息（使用此信息生成二维码用于手机端获取动态口令）

```php
$authenticator = new Authenticator();
$authCode  = $authenticator->getAuthCode('username', $secret, 'title');
```

* 4：动态口令认证

```php
$authenticator = new Authenticator();
$verifyCode  = $authenticator->verifyCode($secret, 'code验证码');
if (verifyCode) {
  echo '认证成功';
} else {
  echo '认证失败';
}
```