---
id: verification
title: اعتبارسنجی شناسه کاربری
layout: react-native-bridge
permalink: react-native-bridge/verification.html
prev: event-handling.html
next: features.html
---

> `نکته`: به زودی کتابخانه **ReactNative Bridge** این امکان را به طور کامل پیاده‌سازی می‌کند.

### اعتبارسنجی

در بعضی از برنامه‌ها بر اساس منطق برنامه گاهی نیاز است که هویت کاربر تایید شود، در این صورت می‌توان برای او یک کد فعال‌سازی پیامک و یا ایمیل نمود و با استفاده از آن هویت وی را تایید کرد. چابک این امکان را به شما می‌دهد، درصورتیکه از شرکت [آتیه‌داده‌پرداز](http://www.adpdigital.com) سرشماره پیامک خریداری کرده باشید، این شماره برای حساب شما فعال خواهد بود و می‌توانید از سرویس درخواست ارسال پیامک استفاده نمایید. توجه داشته باشید نیازی نیست که کاربر شما در چابک ثبت‌نام (register) شده باشد، بلکه بهتر است قبل از ثبت‌نام عملیات اعتبارسنجی انجام شود و در صورت معتبر بودن کاربر، شناسه او برای ثبت‌نام مورد استفاده قرار گیرد.

### فراخوانی وب سرویس به طور مستقیم

ابتدا لازم است تا حساب چابک خود را ایجاد کرده باشید و اطلاعات مربوط به `api-key` را از حساب خود بخوانید. توضیحات مربوط به نحوه فراخوانی وب‌سرویس در [اینجا](https://apidoc.chabok.io/#/Verification) آمده است.


#### مراحل اعتبارسنجی

برای راه‌اندازی اعتبارسنجی باید دو مرحله زیر را به ترتیب انجام دهید تا بتوانید احراز هویت کاربر را به درستی انجام دهید:

1. ارسال کد تایید
2. اعتبارسنجی کد ارسالی

##### ارسال کد تایید

برای ارسال کد تایید کافیست تا `USER_ID` را به  [Verification Code Request](https://apidoc.chabok.io/#/Verification/Verification_requestVerificationCode)  ارسال کنید. پس از آن چابک کد فعال سازی را برای کاربر ارسال می‌کند.
 
##### اعتبارسنجی کد ارسالی 

 پس از ارسال کد تایید لازم است این کد برای چابک ارسال شود تا صحت آن بررسی گردد. جهت اعتبار سنجی می‌بایست کد تایید را به همراه `USER_ID` به [Verification VerifyCode Request](https://apidoc.chabok.io/#/Verification/Verification_verifyCode) ارسال کنید. 

>  `نکته`: مقدار `USER_ID`  دقیقا باید همان مقداری باشد که در مرحله قبل برای درخواست کد استفاده شده است.
