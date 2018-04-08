# Kavenegar notifications channel for Laravel 5.3 | 5.4

This package makes it easy to send [Kavenegar SMS notifications](http://kavenegar.com/) with Laravel 5.3 or 5.4.

## Contents

- [Installation](#installation)
    - [Setting up your Kavenegar account](#setting-up-your-kavenegar-account)
- [Usage](#usage)
- [Contributing](#contributing)

## Installation

You can install the package via composer:

``` bash
composer require kavenegar/laravel-notification
```

You must install the service provider:

```php
// config/app.php
'providers' => [
    ...
    Kavenegar\LaravelNotification\KavenegarServiceProvider::class,
],
```

### Setting up your Kavenegar account

Add your Kavenegar Account Key and Sender Number (optional) to your `config/services.php`:

```php
// config/services.php
...
'kavenegar' => [
    'key' => env('KAVENEGAR_API_KEY'),
    'sender' => env('KAVENEGAR_SENDER')
],
...
```

## Usage

Now you can use the channel in your `via()` method inside the notification:

``` php
use Kavenegar\LaravelNotification\KavenegarChannel;
use Illuminate\Notifications\Notification;

class HappyNewYear extends Notification
{
    public function via($notifiable)
    {
        return [KavenegarChannel::class];
    }

    public function toSMS($notifiable)
    {
        return 'Happy new year :D';
    }
}
```

In order to let your Notification know which phone number you are sending to, add the `routeNotificationForJusibe` method to your Notifiable model e.g your User Model

```php
public function routeNotificationForSms()
{
    return $this->phone; // where `phone` is a field in your users table;
}
```

## Contributing

Bug fixes, docs, and enhancements welcome! Please let us know <a href="mailto:support@kavenegar.com?Subject=SDK" target="_top">support@kavenegar.com</a>

<hr> 
<div dir='rtl'>
	
## راهنما

### معرفی سرویس کاوه نگار

کاوه نگار یک وب سرویس ارسال و دریافت پیامک و تماس صوتی است که به راحتی میتوانید از آن استفاده نمایید.

### ساخت حساب کاربری

اگر در وب سرویس کاوه نگار عضو نیستید میتوانید از [لینک عضویت](http://panel.kavenegar.com/client/membership/register) ثبت نام  و اکانت آزمایشی برای تست API دریافت نمایید.

### مستندات

برای مشاهده اطلاعات کامل مستندات [وب سرویس پیامک](http://kavenegar.com/وب-سرویس-پیامک.html)  به صفحه [مستندات وب سرویس](http://kavenegar.com/rest.html) مراجعه نمایید.

### راهنمای فارسی

در صورتی که مایل هستید راهنمای فارسی کیت توسعه کاوه نگار را مطالعه کنید به صفحه [کد ارسال پیامک](http://kavenegar.com/sdk.html) مراجعه نمایید.

### اطالاعات بیشتر
برای مطالعه بیشتر به صفحه معرفی
[وب سرویس اس ام اس ](http://kavenegar.com)
کاوه نگار
مراجعه نمایید .

 اگر در استفاده از کیت های سرویس کاوه نگار مشکلی یا پیشنهادی  داشتید ما را با یک Pull Request  یا  ارسال ایمیل به support@kavenegar.com  خوشحال کنید.
 
##
![http://kavenegar.com](http://kavenegar.com/public/images/logo.png)		

[http://kavenegar.com](http://kavenegar.com)	

</div>


