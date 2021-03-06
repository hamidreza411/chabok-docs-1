---
id: tracker
title: ترکر نصب
layout: react-native-bridge
permalink: react-native-bridge/tracker.html
prev: sdk-setup.html
next: chabok-messaging.html
---

ترکر چابک کلیک و نصب  کمپین‌ها را شمارش می‌کند. همینطور با توجه به قابلیت [رصد رویدادها](/react-native-bridge/tracker.html#۲۱-رصد-رویدادها-tracking-events) می‌توانید مدل‌های بازاریابی CPI و CPA را برای تبلیغات خود اجرا کنید. مزیت دیگر ترکر چابک [حذف و جلوگیری تقلب](/react-native-bridge/tracker.html#۴-مکانیزم-ضد-تقلب-fraud-prevention) در کمپین‌های تبلیغاتی است.

 نگران راه‌اندازی هم نباشید این صفحه به طور کامل مراحل **پیاده‌سازی و استفاده از ترکر** را قدم به قدم مرور می‌کند.  

<br>

>‍‍`نکته:` در صورتی که از قبل **SDK** چابک را نصب کرده‌‌اید، از [**رصد رویدادها**](/react-native-bridge/tracker.html#۲۱-رصد-رویدادها-tracking-events) شروع کنید.
 
### ۱. پیاده‌سازی (SDK Integration)
---

برای ایجاد حساب کاربری کافیست در وبسایت چابک وارد صفحه [شروع کنید](https://chabok.io/register.html) شوید و حساب شخصی خود را بسازید. پس از ایجاد حساب و ثبت اپلیکیشن خود، با مراجعه به بخش [تنظیمات پنل](https://sandbox.push.adpdigital.com/front/setting/access) پارامترهای اتصال به چابک که در مرحله [مقداردهی](/react-native-bridge/tracker.html#ج--مقداردهی-initialize) مورد نیاز است، در دسترس خواهد بود.


#### ۱.۱. مراحل پیاده‌سازی 

برای راه‌اندازی SDK چابک ۳ مرحله زیر را به ترتیب انجام ‌دهید:

[ الف- نصب کتابخانه](/react-native-bridge/tracker.html#الف--نصب-کتابخانه)

[ب- مقداردهی اولیه (Initialize)](/react-native-bridge/tracker.html#ب--مقداردهی-اولیه-initialize)

[ج- ثبت کاربر](/react-native-bridge/tracker.html#ج--ثبت-کاربر)

<Br>

### الف- نصب کتابخانه 

#### نصب کتابخانه جاوااسکریپ

برای نصب از طریق `npm`:

```bash
npm install react-native-chabok --save
```
 یا `yarn`:

```bash
yarn add react-native-chabok
```
بعد از اتمام نصب، دستور زیر را اجرا کنید تا ماژول به پروژه شما **لینک** شود:

```bash
react-native link react-native-chabok
```

>`نکته:` دقت داشته باشید که [اندروید](/react-native-bridge/sdk-setup.html#۱--نصب-کتابخانه-اندروید) و [آی‌اواس](/react-native-bridge/sdk-setup.html#۱--نصب-کتابخانه-آی‌او‌اس) نیاز به نصب جداگانه دارند که در ادامه به هر دو پرداخته می‌شود:


#### نصب کتابخانه اندروید

برای دریافت کتابخانه چابک دستورات زیر را به فایل `build.gradle` اصلی پروژه اضافه کنید:

```javascript  
buildscript {
    repositories {
        google()
        jcenter()
        maven {
            url "https://plugins.gradle.org/m2/" 
        }
    }
    
    dependencies {    
        classpath 'io.chabok.plugin:chabok-services:1.0.0'
        classpath 'com.google.gms:google-services:4.3.2'
    }
}
```

دستور زیر را در انتهای فایل `build.gradle` ماژول اپلیکیشن خود اضافه کنید:

```javascript  
apply plugin: 'io.chabok.plugin.chabok-services'
apply plugin: 'com.google.gms.google-services'
```

>`نکته:`
 این فایل عموما در مسیر زیر وجود دارد:
**app/build.gradle**

#### نصب کتابخانه آی‌او‌اس

کتابخانه چابک پس از لینک کردن ماژول چابک در دسترس است، با روش زیر آن را نصب کنید:

```bash
$ pod install --repo-update
```
پس از اجرای دستورات بالا اگر با خطایی رو به رو شدید، دستور زیر را وارد کنید، سپس `pod install` را دوباره اجرا کنید.

```bash
$ pod update
```
حالا برای اطمینان از نصب، پروژه را در `xcode` باز کنید ، اگر header فایل چابک را مشاهده کردید، نصب کتابخانه آی‌او‌اس موفقیت آمیز بوده است.

<Br>

### ب- مقدار‌دهی اولیه (Initialize)

#### مقدار‌دهی اولیه اندروید

چابک برای راه اندازی نیاز به **مقداردهی اولیه** دارد.
<br>
۱. برای مقداردهی ابتدا از پنل خود وارد بخش **تنظیمات**> **دسترسی و توکن‌ها**> **کتابخانه موبایل**> **فعال‌سازی راه‌اندازی هوشمند**> شوید و فایل **Chabok.sandbox.json** یا **Chabok.production.json** را بسته به محیطتان دانلود کنید.
<p class="text-center">
<img src="http://uupload.ir/files/9tlr_sandbox-android-chabok-doc.gif">
</p>

>`نکته:`
برای غیرفعال کردن قابلیت **پوش نوتیفیکیشن**(pushNotification)، کافیست مقدار پیش ‌فرض آن را در فایل دانلود شده تغییر بدید.

۲. فایل دانلود شده را در پوشه ماژول اصلی پروژه قرار دهید.
<p class="text-center">
<img width="90%" src="http://uupload.ir/files/pby6_download-file-in-main-module-of-project.gif">
</p>

<br>

۳. در مرحله آخر نیاز است کد‌های زیر را در کلاس اپلیکیشن خود فراخوانی کنید.

```java
import android.app.Application;
import android.content.Context;

//React-Native
import com.facebook.react.PackageList;
import com.facebook.react.ReactApplication;
import com.facebook.react.ReactNativeHost;
import com.facebook.react.ReactPackage;

//Chabok
import com.adpdigital.push.AdpPushClient;
import com.adpdigital.push.config.Environment;

//Java
import java.lang.reflect.InvocationTargetException;
import java.util.List;

public class MainApplication extends Application implements ReactApplication {

    private final ReactNativeHost mReactNativeHost = new ReactNativeHost(this) {
        @Override
        public boolean getUseDeveloperSupport() {
            return BuildConfig.DEBUG;
        }
        
        @Override
        protected List<ReactPackage> getPackages() {
            @SuppressWarnings("UnnecessaryLocalVariable")
            List<ReactPackage> packages = new PackageList(this).getPackages();
            return packages;
        }
        
        @Override
        protected String getJSMainModuleName() {
            return "index";
        }
    };

    @Override
    public ReactNativeHost getReactNativeHost() {
        return mReactNativeHost;
    }

    @Override
    public void onCreate() {
        super.onCreate();

        AdpPushClient.configureEnvironment(Environment.SANDBOX); // or PEODUCTION
    }
}
```

<br>

-**configureEnvironment**: متد `configureEnvironment` تعیین می‌کند که اپلیکیشن شما به محیط [آزمایشی (Sandbox)](https://sandbox.push.adpdigital.com) و یا [عملیاتی (Production) ](https://panel.push.adpdigital.com) چابک متصل شده. این موضوع بستگی به این دارد که حساب کاربری شما روی کدام محیط تعریف شده باشد.  

>`نکته:`متدی که در بالا قرار دادیم برای راه‌اندازی محیط سندباکس است. در صورتی که **حساب عملیاتی** دارید کافیست `Environment.SANDBOX` را با `Environment.PRODUCTION` عوض کنید.
<br>

> `نکته`: برای درخواست حساب محیط **عملیاتی**، در بخش تنظیمات پنل، وارد بخش [**درخواست حساب عملیاتی**](https://sandbox.push.adpdigital.com/front/setting/accountRequest) شوید و درخواست خود را ثبت نمایید و پس از تایید و ساخت حساب عملیاتی فایل **Chabok.production.json** را دانلود کنید و به جای فایل **Chabok.sandbox.json** در پوشه ماژول اصلی پروژه خود قراردهید. 


> `نکته:` دقت داشته باشید که **قابلیت آنی (realtime)**  چابک به طور پیش فرض **غیر فعال** است. برای فعال کردن مقدار قابلیت آنی (realtime)، کافی است مقدار پیش‌فرض آن را در فایل دانلود شده تغییر بدید. این قابلیت در[ پیام چابک](/android/chabok-messaging.html) و [پیام‌رسانی آنی](/android/event-handling.html) استفاده می‌شود.
 

#### مقدار‌دهی اولیه آی‌او‌اس

چابک برای راه‌اندازی نیاز به **مقداردهی اولیه** دارد.


۱- برای مقداردهی ابتدا از پنل خود بخش **تنظیمات> دسترسی و توکن‌ها> کتابخانه موبایل> راه‌اندازی هوشمند** فایل **Chabok.sandbox.plist**  یا  **Chabok.production.plist**  (بسته به محیطتان) را دانلود کنید.

![enter image description here](http://uupload.ir/files/hgt4_ios-configuration-file.png)

> `نکته:` برای غیر فعال کردن دریافت توکن پوش‌نوتیفیکیشن، کافیست مقدار پیش‌فرض آن را در فایل دانلود شده تغییر دهید.

<br>

۲- فایل دانلود شده را در `Bundle Resources` پروژه خود مطابق تصویر اضافه کنید:

![](https://github.com/chabok-io/chabok-assets/raw/master/chabok-docs/ios/chabok-plist.png)

<br>

۳- در آخر متد چابک را در کلاس `AppDelegate` و متد `didFinishLaunchingWithOptions` فراخوانی کنید.

{% tabs %}
{% tab OBJECTIVE-C %}
```objectivec
#import "AppDelegate.h"
#import <AdpPushClient/AdpPushClient.h>

@implementation AppDelegate

- (BOOL)application:(UIApplication *)application
            didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
            
    [PushClientManager.defaultManager configureEnvironment:Sandbox]; // or PEODUCTION
    return YES;
}
```
{% endtab %}
{% tab SWIFT %}
```swift
import UIKit
import AdpPushClient

@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate, PushClientManagerDelegate {

    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?) -> Bool {
    
    PushClientManager.default()?.configureEnvironment(.Sandbox) // or PEODUCTION
    
    return true
}
```
{% endtab %}
{% endtabs %}

> `نکته`: متد بالا برای محیط سندباکس است. در صورتی که حساب عملیاتی دارید کافیست فقط `Sandbox` را با ‍‍`Production` عوض کنید.


> `نکته`: برای درخواست حساب محیط **عملیاتی**، در بخش تنظیمات پنل، وارد بخش [**درخواست حساب عملیاتی**](https://sandbox.push.adpdigital.com/front/setting/accountRequest) شوید و درخواست خود را ثبت نمایید و پس از تایید و ساخت حساب عملیاتی فایل **Chabok.production.plist** را دنلود کنید و به جای فایل **Chabok.sandbox.plist** در روت پروژه خود قراردهید. 

>`نکته` : توجه داشته باشید هنگامی که **گواهی sandbox اپل** را در پنل تستی قرار می‌دهید، فقط امکان دریافت `Push Notification` در حالت `debug` وجود خواهد داشت. اما اگر **گواهی production اپل** را در محیط عملیاتی قرار دهید، زمانی `Push Notification` را دریافت خواهید کرد که اقدام به ساخت **ipa** از پروژه خود کرده و از طریق TestFlight یا Enterprise اپلیکیشن خود را نصب کنید.

> `نکته:` دقت داشته باشید که **قابلیت آنی (realtime)**  چابک به طور پیش فرض **غیر فعال** است. این قابلیت در[ پیام چابک](/ios/chabok-messaging.html) و [پیام‌رسانی آنی](/ios/event-handling.html) استفاده می‌شود.

<br>
 

### ج- ثبت کاربر

یکی از مزیت‌های چابک نسبت به درگاه‌های ارسال پوش‌نوتیفیکیشن، امکان **معرفی** هر کاربر با یک شناسه منحصر به فرد است. این قابلیت به شما امکان می‌دهد دستگاه‌های کاربر را **مدیریت کنید** و سوابق جمع‌آوری شده را همانند یک سیستم مدیریت مشتریان (CRM) در اختیار داشته باشید.       
این شناسه می‌تواند برای **دستگاه‌های متعدد یک کاربر** استفاده شود. شناسه کاربر می‌تواند هر فیلد با ارزش و معنا‌دار برای کسب و کار شما باشد که کاربر خود را با آن شناسایی می‌کنید. **شماره موبایل**، **کدملی**، **شماره‌حساب**، **ایمیل** و یا حتی **شناسه دیتابیس‌تان** مثال‌هایی از شناسه‌های کاربری مناسب در موارد واقعی هستند. ارسال پیام‌ به کاربران توسط همین شناسه‌ها و بدون استفاده از توکن یا شناسه گوشی، به سادگی امکان پذیر خواهد بود.      
 
#### ورود به حساب کاربری (login)
متد لاگین تنها زمانی فراخوانی شود که کاربر در اپلیکیشن لاگین یا ثبت‌نام می‌کند. نیازی به فراخوانی این متد در هر بار اجرای اپلیکیشن نیست.

<p>
فقط شناسه کاربر را گرفته و کاربر را با آن شناسه بر روی سرور چابک ثبت‌ نام می‌کند.
</p>

```java
chabok.login("user_id");
```

>`نکته:` مقدار `USER_ID` می‌تواند **بین ۳ تا ۶۴** کاراکتر باشد. زبان فاسی، کاراکترهای `#,+,*,\,/` و فاصله هم در آن **مجاز نیستند**.


#### خروج از حساب کاربری (logout)

در صورتی که کاربر از حساب کاربری خود خارج شد، با فراخوانی متد زیر می‌توانید کاربر را همچنان با یک تگ مهمان در سیستم خود داشته باشید و تعاملتان را با او ادامه دهید.

```java
chabok.logout();
```

#### رویداد تایید ثبت کاربر

رویداد `onRegister` به شما این امکان را می‌دهد که بررسی کنید آیا عملیات ثبت‌ کاربر انجام شده است یا خیر.

```javascript
const chabokEmitter = new NativeEventEmitter(NativeModules.AdpPushClient);

chabokEmitter.addListener('onRegister', (status)=>{  
    if (status.isRegister) {  
        console.log('User registered ', status);  
	} else {  
        console.log('Not registered error:', error);  
	}  
})
```


#### ۲.۱. رصد رویدادها (Tracking Events)

رویدادها در واقع همان تعامل کاربر با اپلیکیشنتان است. از این رو آن‌ها را **رفتار** کاربر می‌نامیم. شما می‌توانید رفتار کاربر را در اپلیکیشن خود به طور **لحظه‌ای** رصد کنید. این امر به شما امکان می‌دهد تا **CPA های پیشرفته** برای کمپین‌هایتان [تعریف کنید](/panel/tracker.html#افزودن-cpa) و نصب‌هایتان با تحقق اهدافی که برای کاربران تعیین کرده‌اید شمرده شوند. 


به عنوان مثال می‌خواهید رفتار **افزودن به سبد خرید** از فروشگاه اینترنتی خودتان را رصد کنید. برای ثبت این رفتار کد زیر را با الگوی بالا وارد می‌نماییم.

نمونه:

```javascript
const data = {
  "value": 35000
}

this.chabok.track('add-to-card', data)
```

>‍‍‍`نکته:` در متد `track` در صورتی که به `value` مقدار عددی بدهید، آن رفتار در سگمنت با پیشوند **آخرین و مجموع** اضافه می‌شود. اما در صورتی که مقدار غیر عددی (string) بدهید، آن رفتار فقط با پیشوند **آخرین** به سگمنت اضافه می‌شود.

<Br>

##### رصد درآمد (Tracking Revenue)

شما می‌توانید در‌آمدی که کاربران با نشان دادن رفتاری از خود (مانند خرید) تولید می‌کنند را رصد و ذخیره کنید. این کار را باید با متد `trackPurchase` انجام دهید. به عنوان مثال کاربر خریدی را با ارزش ۵۰ هزار تومان انجام داده است.

نمونه:

```java
this.chabok.trackPurchase('Purchase', {revenue: 50000, currency: "RIAL"});
```
برای اطلاعات بیشتر مربوط به رصد رویدادها [اینجا](/react-native-bridge/behavior-tracking.html) را مطالعه کنید.

<br>

#### ۳.۱. تست راه‌اندازی 

اگر عملیات ثبت‌ کاربر به درستی انجام شده باشد، اطلاعات کاربر در [پنل](https://sandbox.push.adpdigital.com/front/users/subscribers/list)  چابک قسمت **کاربران** قابل مشاهده خواهد بود.  

البته محیط آزمایشی فقط برای تست و آشنایی با امکانات است و دارای محدودیت سقف کاربر می‌باشد. بنابراین برای اپلیکیشن‌های تجاری و اپ‌استور توصیه می‌کنیم از حساب عملیاتی که این سقف را ندارد، استفاده کنید.

> `نکته` : در صورتی که مقداردهی اولیه و ثبت کاربر به درستی اعمال شده باشد، می‌توانید اطلاعات دستگاه متصل خود را در [بخش مشترکین پنل چابک](https://sandbox.push.adpdigital.com/front/users/subscribers/list) مشاهده کنید.

در صورتی که مقداردهی اولیه و ثبت کاربر به درستی اعمال شده باشد، می‌توانید اطلاعات دستگاه متصل خود را در [بخش مشترکین پنل چابک](https://sandbox.push.adpdigital.com/front/users/subscribers/list) مشاهده کنید.


#### ۴.۱. انتشار اپلیکیشن در استورها

به طور کلی چابک دارای دو نوع حساب رایگان (محیط آزمایشی) و عملیاتی  است. در صورتی که روی حساب رایگان هستید می‌توانید روی همان حساب نسخه جدید را منتشر کنید.

 داده‌های شما از حساب رایگان به عملیاتی به هیج وجه منتقل نمی‌شوند و برای انتقال باید آپدیت فوری از اپلیکیشن خود بدهید و تمام کاربران را به نسخه جدید بیاورید. برای همین در صورتی هم که حساب عملیاتی دارید  باید حتما **روی محیط عملیاتی** نسخه جدید اپلیکیشن خود را در استورها منتشر کنید.

<br><br>

### ۲. ترک نصب‌ها (Tracking Installs)
---
 
پس از اینکه راه‌اندازی SDK چابک را در اپلیکیشنتان انجام دادید می‌توانید برای کمپین‌های نصب خود ترکر فعال کنید. 

#### ۱.۲. ایجاد لینک ترکر 

برای ایجاد لینک ترکر فقط کافیست وارد صفحه **ترکر** پنل شوید و **ترکر جدید** بسازید. همینطور شما می‌توانید به لینک ترکر خود پارامتر [اضافه کنید](/panel/tracker.html#پارامتر-در-لینک-ترکر).


 برای اطلاعات بیشتر درباره ایجاد ترکر جدید در پنل و مشاهده نمونه‌ای از آن می‌توانید به مستندات [پنل](/panel/tracker.html#ایجاد-ترکر-جدید) مراجعه کنید.


**نمونه لینک ترکر چابک**:

{% tabs %}
{% tab sandbox %}
حساب‌ رایگان:

```javascipt
https://sand.chabok.io/JY@4sc
```  
{% endtab %}
{% tab production %} 
حساب عملیاتی:

```javascipt
https://a.chabok.io/JY@4sc
```  
{% endtab %}
{% endtabs %}

#### ۲.۲. انتشار لینک ترکر 

پس از ایجاد یک ترکر جدید و گرفتن لینک آن کافی است آن را در کمپین‌های نصب خود قرار دهید.
با این کار ترکر شما فعالیت خود را آغاز می‌کند و از این پس هر کلیک و نصب به صورت لحظه‌ای در پنل به نمایش گذاشته خواهد شد.


<br><br>

### ۳. ترک کمپین‌های نصب از استور‌ها
---

شما می‌توانید  نصب‌های خود که از استور‌های مختلف **اندروید و آی‌اواس** گرفته‌اید را ترک کنید. 

>‍`نکته:‍‍‍‍` دقت داشته باشید که برای ترک کمپین‌های نصب باید حتما نسخه SDK چابک شما **۱.۳.۰ به بالا** باشد.

<br>

##### گوگل پلی استور

برای انجام این کار باید از `INSTALL_REFERRER` intent اندروید استفاده کنید. این Referrer وظیفه اطلاع رسانی نصب از گوگل پلی را  به SDK چابک دارد. فقط کافیست اپلیکیشن شما آن را دریافت کند. بنابراین اطمینان یابید که کد زیر در `build.gradle` شما اضافه شده باشد:

```java
implementation 'com.android.installreferrer:installreferrer:1.0'
```

<br>

#### استورهای غیر از گوگل پلی (Third-Party App Stores)

این کار را چابک با دو روش **استفاده از روش Referrer** و **آی‌دی ترکر** انجام می‌دهد. 

> `نکته:` این روش را می‌توانید برای ترک نصب از **گوگل پلی استور** هم استفاده کنید. فقط **زمان کلیک** و **زمان شروع دانلود** را در اختیار شما قرار نمی‌دهد.

##### روش Referrer 

در صورتی که می‌خواهید از استورهای غیر از گوگل پلی که Referrer را **پشتیبانی می‌کنند** ترک کنید، تگ `receiver` را در کلاس `application`  فایل `AndroidManifest.xml` خود قرار دهید: 

```xml
<receiver
    android:name="com.adpdigital.push.ChabokReferrerReceiver"
    android:permission="android.permission.INSTALL_PACKAGES"
    android:exported="true">
       <intent-filter>
            <action android:name="com.android.vending.INSTALL_REFERRER" />
        </intent-filter>
</receiver>
```

زمانی که شما دریافت Referrer را در اپلیکیشن خود پیاده‌سازی کردید، اطلاعات کمپین را دریافت می‌کند و به شما انتقال خواهد داد.

از طریق Referrer شما اطلاعات کلیدی ترکر خود مانند منبع نصب، آی‌دی ترکر و سطح ترکر را ارسال می‌کنید.

#### روش آی‌دی ترکر (Pre-Install Campaigns)

اگر هم استورها Referrer را کلا **پشتیبانی نکنند** شما همچنان می‌توانید منبع (Source) نصب را در کمپین خود برای اندروید و آی‌اواس بفهمید. برای انجام این کار باید در ابتدا ترکر خود را در پنل ایجاد کنید و **آی‌دی ترکر** را در کد apk یا ipa خود قرار دهید.


```javascript
this.chabok.setDefaultTracker("YOUR_TRACKER_ID");
```

>`نکته:` دقت داشته باشید که `TRACKER_ID` شناسه ۶ کاراکتری است که در لینک ترکر شما وجود دارد. به عنوان مثال در لینک `https://sand.chabok.io/JY@4sc` آی‌دی ترکر `JY@4sc` می‌باشد. این آی‌دی را می‌توانید از پنل>ترکر>جزئیات ترکر مانند تصویر زیر کپی کنید:

![عکس مربوط](http://uupload.ir/files/bjbc_tracker-analytics-s.png)

<br><br>

### ۴. ترک جستجوی ارگانیک گوگل
---

گوگل به کاربران امکان می‌دهد تا با جستجوی اپلیکیشن در موتور جستجوی خود و کلیک روی آیکون آن به **گوگل پلی** بروند و آنجا به طور مستقیم نصب کنند.

شما می‌توانید **کلید واژه‌‌ای** که کاربر در **گوگل** جستجو کرده است را داشته باشید. چابک این کلید واژه را در سطح `campaign` ترکر ایجاد می‌کند. 

علاوه بر آن، چابک پارامتر `utm_medium` را در سطح `adgroup` ایجاد می‌کند. این پارامتر همان معیار شمارش است.

>`نکته:` دقت داشته باشید که برای استفاده از این قابلیت باید حتما ‍‍`referrer` را پیاده‌سازی کرده باشید.

<br><br>

### ۵. کال‌بک‌های ترکر (Callbacks)
---

در صورتی هم که می‌خواهید داده‌های ترکر را در سیستم‌های دیگر از جمله سرورهای خود دریافت کنید می‌توانید از کال‌بک استفاده کنید. این کار را می‌توانید از پنل هنگام ایجاد ترکر جدید انجام دهید. به این ترتیب لینکی که می‌خواهید زمان رخ دادن رویداد (کلیک یا نصب) فرخوانی شود را وارد می‌کنید. 

همچنین شما می‌توانید در کال‌بک خود از پارامترهایی برای اطلاعات بیشتر از مبدا رویداد کسب کنید. برای مشاهده این پارامترها و نمونه لینک کال‌بک می‌توانید به مستندات [پنل](/panel/tracker.html#کالبک) مراجعه کنید.

<br><br>

### ۶. مکانیزم ضد تقلب (Fraud Prevention)
---

SDK چابک به گونه‌ای پیاده‌سازی شده است که امکان تقلب و نصب غیر واقعی در روش‌های مبتنی بر نصب و رفتار (CPA و CPI) را به طور کامل از بین می‌برد. علاوه بر آن، به هیج وجه فراخوانی و رصد رویداد‌های چابک قابل دستکاری نیستند. 

مواردی که چابک برای حذف تقلب انجام می‌دهد عبارتند از:

- **IP Filtering**:

آی‌پی کاربر را در زمان کلیک و نصب تطبیق می‌دهد، جلوی نصب‌های متعدد با یک آی‌پی را می‌گیرد و همچنین آی‌پی‌های ناشناخته را رد می‌کند.

- **User Verification**:

با توجه به ساختار کاربر محور بودن سیستم چابک، تمام اطلاعات کاربر در کلیک و نصب را مقایسه می‌کند تا واقعی بودن کاربر جذب شده مشخص شود.

- **SDK Signature**:

روی SDK امضای خاصی را می‌گذارد تا هنگام کلیک دریافت شود و پس از نصب با اپلیکیشن شما تطبیق داده شود. همچنین یکی از راه‌های مقابله با **SDK Spoofing** است. SDK Spoofing یکی از راه‌های تقلب است که نصب‌ها را روی دستگاه‌های واقعی شبیه‌سازی می‌کند و آن را جزو نصب‌های کمپین محاسبه می‌نماید. این کار معمولا از اپلیکیشن‌های دیگر روی دستگاه صورت می‌گیرد و نصب‌های بی‌شمار غیر واقعی را وارد کمپین‌ شما می‌کند.


- **Server to Server Verification**:

اطلاعات کاربر را هنگام کلیک جمع‌آوری می‌کند و با اطلاعاتی که سرور شما در هنگام نصب دریافت می‌کند اعتبارسنجی می‌نماید؛ در صورت عدم تطابق، نصب را رد می‌کند.

- **TTI**:

زمان قابل قبول بین کلیک و نصب است. چابک به طور خودکار فاصله زمانی بسیار کوتاه را رد می‌کند و همینطور در صورتی که از محدوده‌ای که شما تعیین کرده‌اید بیشتر شود ([محدوده اتریبیوشن](/panel/tracker.html#محدوده-اتریبیوشن))، نصب شمرده نخواهد شد.

- **Two-Phase Authentication**:

احراز هویت برای تشخیص واقعی بودن کاربر در هنگام نصب است. در چابک این کار از طریق ارسال پیام کوتاه انجام می‌شود.

<br><br>

### ۷. آشنایی با برخی مفاهیم ترکر
---

- **اتریبیوشن**: نصب‌هایی که از طریق کمپین‌های تبلیغاتی شمرده می‌شوند.

- **بازدید**: هر بار که اپلیکیشن باز شود یک بازدید محاسبه می‌شود.

- **ترکر**: ابزار شمارش و رصد کمپین‌های تبلیغاتی را ترکر می‌نامند.

- **رد شده**: نصب‌ها و کلیک‌هایی که غیر واقعی تشخیص داده می‌شوند و در شمارش محاسبه نمی‌شوند.

- **رویداد**: هرگونه تعامل کاربر با اپلیکیشن، یک رویداد در نظر گرفته می‌شود. 

- **نصب**: اولین بازدید هر کاربر نصب به حساب می‌آید.
