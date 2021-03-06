---
id: release-note
title: لیست تغییرات کتابخانه
layout: flutter
permalink: flutter/release-note.html
prev: features.html
---

شما در این صفحه می‌توانید از تغییرات هر نسخه کتابخانه چابک مطلع شوید. چابک برای نسخه‌گذاری از مدل **Semantic Versioning** استفاده می‌کند. برای آشنایی با این مدل [این قسمت](#مدل-نسخهگذاری-در-چابک-semantic-versioning) را مطالعه نمایید.

<br>

## [نسخه ۱.۰.۲ - ۱۳۹۸/۱۲/۶](https://github.com/chabok-io/chabok-client-flutter/releases/tag/v1.0.2)

### تغییرات

- حذف پیام‌های هشدار در فایل bridge کتابخانه

## [نسخه ۱.۰.۱ - ۱۳۹۸/۱۲/۶](https://github.com/chabok-io/chabok-client-flutter/releases/tag/v1.0.1)

### تغییرات

- حذف پیام‌های هشدار در کتابخانه

## [نسخه ۱.۰.۰ - ۱۳۹۸/۱۲/۶](https://github.com/chabok-io/chabok-client-flutter/releases/tag/v1.0.0)

### تغییرات

- به روز رسانی کتابخانه اندروید به [نسخه ۳.۱.۳](/android/release-note.html#نسخه-۳۱۳---۱۳۹۸۱۰۱۸)
- افزودن کتابخانه آی‌او‌اس [نسخه ۲.۲.۰](/ios/release-note.html#نسخه-۲۲۰---۱۳۹۸۰۷۱۷)
- پشتیبانی از دریافت **Referral** با استفاده از فراخوانی متد `setOnReferralHandler`.
- پشتیبانی از دریافت **DeepLink** با استفاده از فراخوانی متد `setOnDeepLinkHandler`.
- پشتیبانی از افزودن به مقادیر آرایه‌ای که برای داده‌های سفارشی کاربر استفاده کرده‌اید با فراخوانی متد `addToUserAttributeArray(attributeKey, attributeValue)`.
- پشتیبانی از حذف مقادیر آرایه‌ای که برای داده‌های سفارشی کاربر استفاده کرده‌اید با فراخوانی متد `removeFromUserAttributeArray(attributeKey, attributeValue)`.
- پشتیبانی از حذف داده‌های سفارشی کاربر با فراخوانی متد `unsetUserAttribute(attributeKey)`.
- پشتیبانی از تاریخ و ساعت برای مقادیری که در رویدادها و داده‌های سفارشی کاربر ارسال می‌کنید با استفاده از شی `DateTime` که در دارت موجود هست.
- افزودن متد `incrementUserAttribute(attributeKey)` برای افزایش مقدار داده‌های کمیتی کاربر
- افزودن متد `decrementUserAttribute(attributeKey)` برای کاهش مقدار داده‌های کمیتی کاربر
- منسوخ شدن متد `init` و جایگزینی آن با متد `configureEnvironment` برای راه‌اندازی اولیه کتابخانه چابک.
- منسوخ شدن متد‌ `register`  و جایگزینی آن با متد `login` برای ثبت ورود کاربر.
- منسوخ شدن متدهای `unregister` و `registerAsGuest` و جایگزینی آن‌ها با متد `logout` برای ثبت خروج کاربر.
- دریافت خودکار پوش‌نوتیفیکیشن و پیام چابک

## نسخه ۰.۰.۲ 

### تغییرات

- دریافت پیام چابک از طریق فراخوانی متد `setOnMessageCallback`.
- دریافت کنش‌های کاربر با اعلان‌ها از طریق فراخوانی متد `setOnNotificationOpenedHandler`.
- اطلاع از وضعیت نمایش اعلان از طریق فراخوانی متد `setOnShowNotificationHandler`.
- دریافت وضعیت اتصال به سرور چابک از طریق فراخوانی متد `setOnConnectionHandler`.

## نسخه ۰.۰.۱ 

### تغییرات

- افزودن تگ به کاربر از طریق فراخوانی متد `addTag`.
- حذف تگ از کاربر از طریق فراخوانی متد `removeTag`.
- افزودن داده‌های سفارشی کاربر از طریق فراخوانی متد `setUserAttributes`.
- رصد رفتار کاربران با فراخوانی متد `track`.
- رصد خرید کاربران با فراخوانی متد `trackPurchase`.
- ثبت کاربر با فراخوانی متد `register`.
- حذف کاربر با فراخوانی متد `unregister`.

<br><br>

#### مدل نسخه‌گذاری در چابک (Semantic Versioning)  

چابک از مدل نسخه‌گذاری `MAJOR`.`MINOR`.`PATCH` استفاده می‌کند. همه تغییرات نسخه‌ها بلافاصله پس از انتشارشان به صورت موردی در صفحه **لیست  تغییرات** برای اطلاع شما اضافه می‌شوند. برای همین توصیه می‌کنیم این صفحه را حتما مطالعه نمایید. این موارد برای هر نسخه در دو بخش **ارتقا** و **تغییرات** برای شما نمایش داده شده‌ است.

- `Patch:` تغییرات در این سطح شامل **Bug Fix** و **قابلیت‌های بسیار کوچک** می‌باشد. به روز رسانی به این نسخه‌ها نیاز به تغییری در کد ندارد. برای آگاهی از آن‌ها، باید بخش **تغییرات** را مطالعه کنید. به عنوان مثال به‌ روز رسانی کتابخانه چابک از نسخه `2.14.0` به نسخه `2.14.1` مربوط به این سطح می‌شود.  
- `Minor:` تغییرات در این سطح شامل **قابلیت‌های بزرگتر** و **تغییر در کارکرد (Functionality) کتابخانه** می‌شود. در به روز رسانی به این نسخه‌ها حتما باید بخش **ارتقا**  و تغییرات صفحه لیست تغییرات را با دقت مطالعه کنید. در صورت بروز هر گونه مشکل در نتیجه رعایت نکردن نکات بخش **ارتقا** و **تغییرات** در به روز رسانی به نسخه‌های **Minor**، تیم چابک مسئولیتی را نمی‌پذیرد. توصیه می‌کنیم که هر سه تا شش ماه اقدام به بررسی نسخه‌های **Minor** نمایید. به عنوان مثال به‌ روز رسانی کتابخانه چابک از نسخه `2.12.1` به نسخه `2.14.1` مربوط به این سطح می‌شود.  
- `Major:` این سطح از تغییرات مخصوص **بازنویسی** و یا **تغییرات اساسی** در کتابخانه چابک است. در به روز رسانی به این نسخه‌ها حتما باید بخش **ارتقا** تغییرات صفحه لیست تغییرات را با دقت مطالعه کنید. در صورت بروز هر گونه مشکل در نتیجه رعایت نکردن نکات بخش **ارتقا** و **تغییرات** در به روز رسانی به نسخه‌های **Major**، تیم چابک مسئولیتی را نمی‌پذیرد. بنابراین توصیه می‌کنیم که هر یک سال اقدام به بررسی نسخه‌های **Major** نمایید. به عنوان مثال به‌روزرسانی کتابخانه چابک از نسخه `1.0.1` به نسخه `2.14.1` مربوط به این سطح می‌شود.  
