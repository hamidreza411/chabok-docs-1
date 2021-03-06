---
id: tracker
title: ترکر
layout: panel
permalink: panel/tracker.html
prev: dashboard.html
next: users.html
---

**ترکرها** (یا شمارنده‌ها) ابزاری برای اندازه‌گیری نتایج کمپین‌های تبلیغاتی هستند؛ با این مکانیزم که داده‌های آماری کمپین (مانند تعداد کلیک، نصب، منابع هر کدام و ...) را در اختیار شما می‌گذارند تا با تحلیل آن‌ها بتوانید کمپین‌های جذب کاربر خود را بهینه‌سازی کنید.


در این قسمت شما می‌توانید برای کمپین‌های نصب خود، **ترکر** [تعریف کنید](/panel/tracker.html#ایجاد-ترکر). برای این کار باید **نام** و **لینک مقصدی** کمپینتان را ثبت کنید. پس از فعال کردن ترکر می‌توانید آمار لحظه‌ای آن را [مشاهده کنید](/panel/tracker.html#آمار-ترکر ).

برای آشنایی با **راه‌اندازی ترکر** مستندات آن را در [اندروید](/android/tracker.html) و [آی‌اواس](/ios/tracker.html) مطالعه کنید.

<Br>

### سطح‌بندی

 قابلیت سطح‌بندی به شما کمک می‌کند تا بفهمید کاربران جدید با **چه شبکه‌ای، کمپینی، گروه تبلیغاتی و محتوایی** جذب شما شدند. این پارامترها مانند پارامترهای UTM به شما اطلاع می‌دهد **کاربر از کجا آمده است**.

لینک ترکر چابک **۴ سطح** را به ترتیب زیر پشتیبانی می‌کند:

- **۱- network (شبکه)**
- **۲- campaign (کمپین)**
- **۳- adgroup (گروه تبلیغاتی)**
- **۴- creative (خلاقانه)**


### سطح‌بندی پویا 

سطح‌بندی پویا به شما امکان می‌دهد تا با ساخت یک ترکر، بی نهایت **زیر ترکر (subtracker)** داشته باشید. هدف زیر ترکرها در واقع دسته‌بندی مخاطبان، برای ارزیابی و در نتیجه بهینه‌سازی هرچه بیشتر است. به عنوان مثال شما می‌خواهید کمپین‌های تابستانه خود را برای گرفتن نصب بروید. طبیعی است که شما این کار را با یک کمپین و یا یک محتوا منتشر نکنید. در این حالت می‌توانید به سادگی به تعداد کمپین‌های خود زیر ترکر بسازید و عملکرد جمعی و فردی هر کدام را بررسی کنید. در ادامه باز هم می‌توانید برای هر زیر ترکر کمپین، زیر ترکر‌های ریزتر (برای محتوا) بسازید و به همین ترتیب ادامه دهید.

<div style="text-align: center;"><img src="http://uupload.ir/files/kipk_subtracker-chart.png" class="img-fluid" style="
    width: 800px;
"></div>

 ساخت زیر ترکر‌ها از طریق **افزودن پارامتر** انجام می‌شود. پارامترها، در واقع برچسب‌هایی هستند که می‌توان روی لینک ترکر گذاشت. برای فهم بهتر می‌توانید آن‌ها را مانند پارامتر‌های UTM که در وب استفاده می‌شوند، در نظر بگیرید. جدول زیر پارامتر‌های چابک را متناظر با پارامترهای UTM نشان می‌دهد:

<p>
<table>
<thead>
<tr>
<th style="text-align: center">پارامترهای چابک</th>
<th style="text-align: center">پارمترهای UTM گوگل</th>
<th style="text-align: center">توضیح</th>
</tr>
</thead>
<tbody><tr>
<td align="center">Ad Network name</td>
<td align="center">utm_source</td>
<td align="center">شبکه تبلیغاتی</td>
</tr>
<tr>
<td align="center">Campaign name</td>
<td align="center">utm_campaign</td>
<td align="center">نام کمپین</td>
</tr>
<tr>
<td align="center">Ad group name</td>
<td align="center">utm_content</td>
<td align="center">محتوای کمپین</td>
</tr>
<tr>
<td align="center">Creative name</td>
<td align="center">utm_term</td>
<td align="center">کلیدواژه کمپین</td>
</tr>
</tbody></table>
</p>

به یاد داشته باشید که استفاده از پارامترها کاملا بستگی دارد به ساختاری که برای کمپینتان تدارک دیده‌اید. 

##### افزودن پارامتر به لینک ترکر

پارامترهایی که می‌توانید در لینک ترکر بگذارید عبارتند از:

##### دسته‌بندی کاربران (Segmenting Users)

در **لینک ترکر** می‌توانید از پارامترهای ‍‍‍‍‍‍‍‍`campaign`، `adgroup` ،`creative` استفاده کنید.

به عنوان مثال می‌خواهید مخاطبانتان را براساس نام کمپین دسته‌بندی کنید. نام این کمپین،‌ کمپین شماره ۱ است. در این صورت لینک ترکر شما به صورت زیر خواهد بود:

```markup
https://sand.chabok.io/637z3i?campaign=CAMPAIGN_1&adgroup=AD_GROUP&creative=CREATIVE
```

##### هدایت کاربران (Redirect Users)

شما می‌توانید برای هدایت کاربران به جای دلخواه از پارامترهای `fallback` ،`redirect_ios` ،`redirect_android` در لینک ترکر خود استفاده کنید. لینک زیر مثالی از تمام پارامترهایی است که می‌توانید در لینک خود قرار دهید. 

```markup
https://sand.chabok.io/637z3i?redirect_ios=https://itunes.apple.com/us/genre/ios/id36?mt=8&redirect_android=https://play.google.com/store&fallback=https://mylandingpage.com/&click_id=11111&android_id=ANDROID_ID&
```

##### کال‌بک داینامیک (Dynamic Callback)

علاوه بر کال‌بک جداگانه می‌توانید در لینک خود از پارامترهای `callback` و `install_callback` استفاده کنید. برای این کار می‌توانید [جدول پارامتر‌های کال‌بک](/panel/tracker.html#کالبک) در پایین صفحه را مشاهده کنید. لینک زیر مثالی برای این مورد نشان می‌دهد:


```markup
https://sand.chabok.io/637z3i?callback=https://campaign.90tv.ir/?event={{activity_kind}}&tracker={{tracker_name}}&install_callback=https://campaign.90tv.ir/?event={{activity_kind}}&tracker={{tracker_name}}&os={{os_name}}&ip={{ip_address}}
```

<br>

##### نکات ضروری پارامترها

- همیشه پارامترها را با **&** جدا کنید.
- حتما از **حروف کوچک** استفاده کنید زیرا پارامتر به حروف بزرگ و کوچک حساس هستند.
- از درست نوشتن پارامترها اطمینان یابید.
- از ترتیب سطح‌بندی پیروی کنید. به عنوان مثال زمانی که گروه تبلیغاتی هنوز خالی است خلاقانه را پر نکنید.

<Br>

### ایجاد ترکر 

شما می‌توانید علاوه بر **نام** و **لینک مقصد** به ترکر خود پارامترهای دیگری هم مانند **نام کمپین، شبکه، گروه تبلیغاتی و خلاقانه**، **پارامتر لینک مقصد و دیپ لینک (Deeplink)**، **کال‌بک** و **محدوده اتریبیوشن** اضافه کنید: 

<Br>

![عکس مربوطه](http://uupload.ir/files/046x_new-tracker-1.png)
![عکس مربوطه](http://uupload.ir/files/xmzo_new-tracker-2.png)


<Br>

#### اطلاعات

شما می‌توانید نام کمپین، شبکه تبلیغاتی، گروه تبلیغاتی و خلاقانه مخصوص خود را به ترکر اضافه کنید. با این کار شما ترکرهای خود را **سطح‌بندی** می‌کنید تا آن‌ها را به صورت جداگانه بررسی کنید. سطح‌بندی‌های داخل پنل پیش‌فرض هستند و شما می‌توانید از طریق [افزودن پارامتر](/panel/tracker.html#افزودن-پارامتر-به-لینک-ترکر) آن را پویا کنید.

پارامتر **خلاقانه (Creative)** در واقع آخرین و ریزترین سطح دسته‌بندی ترکر است که شما یا آژانس تبلیغاتی خود می‌توانید آن را به دلخواه استفاده کنید.

>`نکته مهم:` دقت داشته باشید در هنگام ایجاد ترکر، سطح‌های انتخابی شما پرش نداشته باشد. برای مثال اگر **نام کمپین** داده‌اید، **شبکه تبلیغاتی** هم پر شده باشد زیرا در صورت خالی بودن، آمار را نخواهید داشت. 

#### لینک مقصد

در این قسمت تعیین می‌کنید کلیک روی کمپین، شما را به چه مقصدی هدایت کند. لینک مقصد را می‌توانید براساس پلتفرم هم تعیین کنید. به عنوان مثال کاربران اندرویدی به لینک نصب اپلیکیشن در کافه بازار یا پلی‌ استور هدایت شوند و کاربران آی‌او‌اس به اپ استور.  

##### لینک اندروید

در **اختصاص لینک مقصد اندروید**، شما با انتخاب استور (کافه بازار، پلی استور یا مارکت دلخواه کاربر) **دیگر نیازی به وارد کردن لینک مخصوص آن استور را ندارید** و چابک خودش به طور هوشمند این کار را انجام می‌دهد.

- در صورت انتخاب کافه بازار یا پلی استور، کاربر **مستقیما** به هر کدام از آن‌ها هدایت می‌شود.

- در صورت **انتخاب مارکت، از کاربر با توجه به استورهایی که روی دستگاه خود دارد پرسیده می‌شود که کدام باز شود**.

##### لینک آی‌اواس

در اختصاص لینک برای نصب مستقیم (مدل Enterprise) باید از فرم زیر پیروی کنید:

```bash
itms-services://?action=download-manifest&url=https://mobileapp.adpdigital.com/navad/navad.plist
```

<Br>

در لینک مقصد می‌توانید پارامترهایی را مانند منبع، فرم یا مدل کمپین، نام کمپین و ... قرار دهید و بازخوردش را در پنل گوگل آنالییکس خود نگاه کنید:

![عکس مربوطه](http://uupload.ir/files/kihu_parameters.png)

##### دیپ لینک (Deeplink)

دیپ لینک یا لینک عمقی به شما اجازه می‌دهد تا لینک مقصد خود را به **صفحات داخلی اپلیکیشن** دهید.

<Br>

#### کال‌بک

شما می‌توانید به ترکر خود **لینک کال‌بک** اضافه کنید. در اختصاص لینک کال‌بک، شما ‌می‌توانید پارامترهایی را درخواست دهید. این پارامترها در **جدول‌های زیر** قابل مشاهده هستند. هر کدام از این پارامترها را به دلخواه خودتان می‌توانید انتخاب کنید.  

##### جدول پارامترهای کال‌بک کلیک

 <p>
<table>
<thead>
<tr>
<th style="text-align: center">پارامترها</th>
<th style="text-align: right">توضیح</th>
</tr>
</thead>
<tbody><tr>
<td align="center">activity_kind</td>
<td align="right">نوع فعالیت (کلیک، نصب و...)</td>
</tr>
<tr>
<td align="center">tracker</td>
<td align="right">شناسه ترکر</td>
</tr>
<tr>
<td align="center">tracker_name</td>
<td align="right">نام ترکر</td>
</tr>
<tr>
<td align="center">network_name</td>
<td align="right">نام شبکه تبلیغاتی</td>
</tr>
<tr>
<td align="center">campaign_name</td>
<td align="right">نام کمپین</td>
</tr>
<tr>
<td align="center">adgroup_name</td>
<td align="right">نام گروه تبلیغاتی</td>
</tr>
<tr>
<td align="center">creative_name</td>
<td align="right">نام کریتیو</td>
</tr>
<tr>
<td align="center">ip_address</td>
<td align="right">آی‌پی کاربر</td>
</tr>
<tr>
<td align="center">os_name</td>
<td align="right">سیستم‌عامل</td>
</tr>
<tr>
<td align="center">os_version</td>
<td align="right">نسخه سیستم‌عامل</td>
</tr>
<tr>
<td align="center">device_manufacturer</td>
<td align="right">برند دستگاه</td>
</tr>
<tr>
<td align="center">device_name</td>
<td align="right">مدل دستگاه</td>
</tr>
<tr>
<td align="center">click_time</td>
<td align="right">زمان کلیک</td>
</tr>
</tbody></table>
</p>

<Br>

##### جدول پارامترهای کال‌بک نصب

<p>
<table>
<thead>
<tr>
<th style="text-align: center">پارامترها</th>
<th style="text-align: right">توضیح</th>
</tr>
</thead>
<tbody><tr>
<td align="center">activity_kind</td>
<td align="right">نوع فعالیت (کلیک، نصب و...)</td>
</tr>
<tr>
<td align="center">tracker</td>
<td align="right">شناسه ترکر</td>
</tr>
<tr>
<td align="center">tracker_name</td>
<td align="right">نام ترکر</td>
</tr>
<tr>
<td align="center">network_name</td>
<td align="right">نام شبکه تبلیغاتی</td>
</tr>
<tr>
<td align="center">campaign_name</td>
<td align="right">نام کمپین</td>
</tr>
<tr>
<td align="center">adgroup_name</td>
<td align="right">نام گروه تبلیغاتی</td>
</tr>
<tr>
<td align="center">creative_name</td>
<td align="right">نام کریتیو</td>
</tr>
<tr>
<td align="center">ip_address</td>
<td align="right">آی‌پی کاربر</td>
</tr>
<tr>
<td align="center">os_name</td>
<td align="right">سیستم‌عامل</td>
</tr>
<tr>
<td align="center">os_version</td>
<td align="right">نسخه سیستم‌عامل</td>
</tr>
<tr>
<td align="center">device_manufacturer</td>
<td align="right">برند دستگاه</td>
</tr>
<tr>
<td align="center">device_name</td>
<td align="right">مدل دستگاه</td>
</tr>
<tr>
<td align="center">click_time</td>
<td align="right">زمان کلیک</td>
</tr>
<tr>
<td align="center">app_id</td>
<td align="right">شناسه اپلیکیشن</td>
</tr>
<tr>
<td align="center">app_version</td>
<td align="right">نسخه اپلیکیشن</td>
</tr>
<tr>
<td align="center">connection_type</td>
<td align="right">نوع اتصال</td>
</tr>
<tr>
<td align="center">android_id</td>
<td align="right">شناسه اندروید (فقط در اندروید)</td>
</tr>
<tr>
<td align="center">installed_at</td>
<td align="right">زمان نصب</td>
</tr>
<tr>
<td align="center">adid</td>
<td align="right">شناسه تبلیغاتی</td>
</tr>
</tbody></table>
</p>

<Br>

> `نکته:` شما می‌توانید از `click_id` هم به عنوان پارامتر کال‌بک استفاده کنید. این شناسه را خودتان (یا آژانس تبلیغاتی‌تان) تعیین می‌کنید و به لینک ترکر چابک اضافه می‌کنید و در کال‌بک آن را می‌توانید دریافت کنید.

برای مثال به کال‌بک زیر توجه کنید:

![عکس مربوطه](http://uupload.ir/files/ut47_callback-example.png)

<Br>

#### محدوده اتریبیوشن

آخرین قسمت ایجاد ترکر، تعیین **محدوده اتریبیوشن** است. این اقدام برای **جلوگیری از [تقلب](https://blog.chabok.io/fraud_detection/) در شمارش** انجام می‌شود. شما می‌توانید تعداد ساعاتی که بین کلیک و نصب برای شما قابل قبول است را مشخص کنید.

#### افزودن رویداد (مدل CPA)

شما می‌توانید کمپین‌های نصب خود را با مدل CPA یا همان هزینه براساس اکشن (رفتار) اجرا کنید. دکمه افزودن CPA **بلافاصله بعد از کلیک روی ایجاد** در صفحه ترکر جدید ظاهر می‌شود. همینطور می‌توانید پس از ایجاد، وارد صفحه جزئیات ترکر شوید و **افزودن رویداد** را بزنید.

![عکس مربوطه](http://uupload.ir/files/gdsu_add-event-in-tracker.png)

<br>



در این صفحه علاوه بر تعیین رویداد (یا اکشن) می‌توانید **هدف** نیز مشخص کنید.
سربرگ هدف علاوه بر مشخص کردن نام هدف، به شما این امکان را می‌دهد تا برای رسیدن به یک یا چند رویداد، سگمنت‌های متفاوتی همراه با چندین ویژگی (attribute) را تعریف کنید.

![عکس مربوطه](http://uupload.ir/files/uxwy_goal_in_panel.png)

<Br>

##### تفاوت رویداد و هدف

در این قسمت با ذکر مثال تفاوت بین رویداد و هدف را توضیح می‌دهیم.


فرض کنید صاحب کسب و کار آنلاینی هستید و قصد دارید بسنجید چه تعداد از کاربران بعد از کلیک بر روی لینک ترکر و نصب اپلیکیشن، روی دکمه ثبت‌نام در اپلیکیشن کلیک می‌کنند در این حالت که فقط انجام یک رویداد (Event) بعد از نصب کاربر برایتان اهمیت دارد از رویداد استفاده می‌کنید. 
 
اما اگر بخواهید انجام دادن چند رویداد بعد از کلیک روی لینک ترکر و نصب اپ را رصد کنید و یا اینکه بخواهید تعداد انجام شدن یک رویداد توسط گروه خاصی از کاربران را اندازه بگیرید، باید برای ترکر، هدف (Goal)‌ تعیین کنید. مثلا اگر می‌خواهید اثربخشی کمپین نصب از یک منبع خاص را روی ثبت‌نام در اپلیکیشن، جست‌و‌جو در اپلیکیشن و اضافه کردن یک آیتم به لیست علاقه‌مندی‌ها را برای گروهی از کاربران که در موقعیت مکانی خاصی مثلا در شهر کرج هستند، بسنجید. می‌توانید با تعریف یک هدف و تخصیص چند رویداد و سگمنت به سادگی تعداد آن‌ها را روی ترکرهای مختلف مقایسه کنید. 

<Br>


### آمار ترکر 

در صفحه ترکر، نمودار آماری کاربران جذب شده برای مجموع ترکرها نمایش داده شده است. در این نمودار می‌توانید کاربرانی که به صورت **ارگانیک**، از طریق **شبکه تبلیغاتی** و یا از **تبلیغات گوگل** جذب شده‌اند را مشاهده و مقایسه کنید.

**ارگانیک**: کاربرانی که خودشان، جدا از کمپین‌های تبلیغاتی به اپلیکیشن شما پیوسته‌اند.  

![عکس مربوطه](http://uupload.ir/files/fy72_all-trackers.png)

<Br>

با کلیک روی هر ترکر، **وارد سطح‌ کوچکتر آن ترکر می‌شوید**. به عنوان مثال کلیک روی ترکر وارد شبکه‌های آن می‌شود سپس کلیک روی شبکه وارد کمپین‌های آن شبکه می‌شود و به همین ترتیب ادامه پیدا می‌کند. 

#### جزئیات ترکر

برای مشاهده آمار دقیق هر ترکر کافی است در لیست ترکرهای فعال خود از بخش دستورات، وارد **جزئیات** شوید.

![عکس مربوطه](http://uupload.ir/files/3ad_lqtz_53ep_tracker-detail-1.png)
![عکس مربوطه](http://uupload.ir/files/xymw_tracker-detail-2.png)

<br>

##### ویرایش

در این قسمت می‌توانید تمام اطلاعات ترکر (به جز نام آن) خود را تغییر دهید.

##### افزودن دسترسی

شما می‌توانید آمار ترکر خود را با آژانس‌های مورد نظر **به اشتراک بگذارید**. فقط کافی است نام ایمیل آن‌ها را در **افزودن دسترسی** وارد کنید. درصورتی که آژانس از قبل حساب داشته باشد به لیست ترکرهایش اضافه خواهد شد، در غیر این صورت به صفحه **ثبت نام** هدایت خواهد شد.

##### جدول آمار

در جدول **آمار ترکر** می‌توانید آمار سطح‌های ترکر (شبکه تبلیغاتی، نام کمپین، گروه تبلیغاتی و خلاقانه) خود را مشاهده کنید. با کلیک روی شبکه وارد کمپین‌های آن می‌شوید و به همین ترتیب وارد سطح‌های کوچکتر شوید. این آمار شامل **کلیک، نصب، نرخ تبدیل، رد شده، رویدادهای تعیین شده (در اینجا purchase)، درآمد، حذف و نرخ حذف** است.

##### نمودارهای آماری

- **ترافیک**: روند نصب و کلیک‌هایی که ترکر شمارش می‌کند. موارد **رد شده** تعداد کل نصب‌هایی که چابک **غیر واقعی** تشخیص داده است. در این نمودار می‌توانید سه مورد از عواملی که منجر به رد شده‌اند را در ماه جاری مشاهده کنید. **خارج از محدوده** همان محدوده اتریبیوشن یا زمان قابل قبولی که بین کلیک و نصب تعیین کرده‌اید. عامل بعدی **کوتاه بودن فاصله بین نصب و کلیک** است. عامل آخر **نصب نامعتبر** است که به معنی عدم تطابق امضاهای کاربر در کلیک و نصب می‌باشد.

- **رویداد**: رویداد‌هایی که شما تعیین کرده‌اید تا توسط ترکر رصد شوند.

- **بازدید**: درصد کاربرانی که از کمپین نصب مورد نظر آمده‌اند و **بازدید** داشته‌اند. 

- **حذف**: تعداد حذف‌های یک کمپین در ماه جاری.

- **سگمنت**: در این قسمت تمام سگمنت‌هایی که کاربران با کمپین نصب مورد نظر جذب شده‌اند، به صورت هوشمند قابل مشاهده می‌باشند. با این قابلیت می‌توانید برای کاربران جدید خود هدف‌ تعیین کنید و از نتایج آن با خبر شوید.

### ترکرهای پیش‌فرض چابک

چابک به طور پیش‌فرض **۴ ترکر** را برای هر حساب قرار می‌دهد. این ترکرها **ارگانیک** (نصب‌هایی که  به طور طبیعی و بدون کمپین رخ داده‌اند)، **تبلیغات گوگل** (Google Ads)[، **جستجوی گوگل پلی استور**](/android/tracker.html#۴-ترک-جستجوی-ارگانیک-گوگل) و [**تبلیغات کافه بازار**](/panel/settings.html#تبلیغات-کافه-بازار) هستند. 
