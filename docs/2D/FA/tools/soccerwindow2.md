# ابزار نمایش و خطایابی SoccerWindow2

<ImageZoom 
  src="/docs/2D/FA/img/doc/tools/soccerwindow2.jpg" 
  :border="true" 
  width="auto"
/>

SoccerWindow2 (ساکرویندو۲) ابزار غیر رسمی‌ای برای برای نمایش بازی‌هاست. به کمک این ابزار شما میتوانید از دیباگر خود بیس استفاده کنید و فرایند خطایابی را در بیس ایجنت تسهیل ببخشید. این ابزار امکانات اضافه‌ای را نیز برای شخصی‌سازی نمایش بازی در اختیار شما میگذارد در پایین تر شیوه نصب و اجرا و میانبر‌های مفید این ابزار آورده شده است.

##   دانلود و نصب

برای دانلود اخرین نسخه‌ی این برنامه به [این آدرس](https://osdn.net/projects/rctools/releases/p4886) مراجعه کنید و آخرین نسخه SoccerWindow2 را دانلود کنید. 

پس از دانلود شدن آن با استفاده از دستور زیر در ترمینال فایل‌ها را از حالت فشرده خارج کنید:‌

```bash
tar -zxpf soccerwindow2-x.x.x.tar.gz
```

*توجه کنید که به جای x.x.x باید نسخه‌ی ساکر ویندو دانلود شده را بزنید.*

حال با استفاده از دستورات زیر وارد محل اطلاعات شوید و آن را Build و سپس نصب کنید: 

```bash
cd soccerwindow2-x.x.x
./configure && make
sudo make install
```

### مشکلات احتمالی

ممکن است در هنگام نصب با ارور زیر روبه‌رو شوید.

```bash
	unrecognized command line option ‘-pthread-lQtGui’ 
```

برای برطرف ساختن این مشکل فایل `configue` را باز کنید و به دنبال این خط باشید.

```bash
QT4_LDADD="$($PKG_CONFIG --static --libs-only-other $QT4_REQUIRED_MODULES)$($PKG_CONFIG --static --libs-only-l $QT4_REQUIRED_MODULES)"
```

بین متغیرهای ‍`$PKG_CONFIG`، مانند زیر، فاصله (اسپیس) بگذارید.

```bash
QT4_LDADD="$($PKG_CONFIG --static --libs-only-other $QT4_REQUIRED_MODULES) $($PKG_CONFIG --static --libs-only-l $QT4_REQUIRED_MODULES)"
```

سپس دوباره دستورات را اجرا کنید.

```bash
./configure && make
sudo make install
```

حال سرور شبیه ساز را اجرا کرده و در ترمینالی جداگانه با دستور زیر SoccerWindow2 را اجرا کنید.

 ```bash
soccerwindow2
 ```

در صورتی که تمامی مراحل با موفقیت طی شود SoccerWindow به صورت کامل نصب و اجرا می‌شود.



## میانبرهای کیبورد در داخل ساکر ویندو

```bash
SCROLL MOUSE +/-		 کم و زیاد کردن شفافیت پنچره باز شده
CRTL + Q				 بستن ساکر ویندو
E						 نمایش یا پنهان کردن محیط تحت کنترل بازیکن
CTRL + R				 تغییر جهت تیم ها
T						 نمایش یا پنهان کردن محیط و اطلاعات تکل
CTRL + T 				 نمایش یا پنهان کردن نوار امتیازات و زمان
SHIFT + T 				 نمایش یا پنهان کردن لوگو و پرچم تیم ها
I						 تنظیم مرکزیت و اندازه دوربین بازی روی مرکز
CTRL + I				 باز کردن جزپیات و اطلاعات بازی مختص به هر بازیکن
O						 نمایش یا پنهان خط افساید
CTRL + O 				 باز کردن فایل بازی ها
P						 تنظیم مرکزیت دوربین بازی روی بازیکن دلخواه
CTRL + P				 نمایش یا پنهان کردن تمام بازیکنان
CTRL + A			  	 نمایش یا پنهان کردن توجهات بازیکنان به صدا ها
S						 نمایش یا پنهان کردن انرژی و ماکس انرژی
D						 نمایش جهت بدن بازیکان
CTRL + D				 نمایش دیلاگ های بازی
F 						 نمایش یا پنهان کردن اشارات بازیکنان
CTRL + F				 نمایش پرچم های زمین
G						 نمایش گل بعدی
CTRL + G 				 نمایش گل قبلی
H						 نمایش یا پنهان کردن تایپ بازیکنان
CTRL + H				 نمایش یا پنهان کردن لیست تایپ بازیکنان
CTRL + K			     شروع بازی
CTRL + L				 لایو کردن بازی
L (V needed)			 نمایش یا پنهان کردن دید و و اندازه دید بازیکن
Z						 بزرگنمایی بازی
CTRL + Z / X			 کوچک کردن بازی
CTRL + X				 باز کردن لانچر بازی
CTRL + C				 کانکت شدن به سرور
V						 نمایش یا پنهان کردن جهت دید بازیکن	
CTRL + V				 نمایش یا پنهان کردن منوی ویو
B						 تنظیم مرکزیت دوربین بازی روی توپ
N						 نمایش یا پنهان کردن شماره بازیکنان
CTRL + M 				 نمایش یا پنهان کردن نوار منو
1 , .... , 9 , 0		 انتخاب بازیکنان		
```





## کامندلاین‌های مفید

> مقدار داخل پرانتز مقدار یا عملیات پیش‌فرض آن کامندلاین است! (= defult)

دستورات زیر را بعد از soccerwindow در ترمینال وارد کنید.

مثال :`127.0.0.1 soccerwindow2 --host`

```bash
 --host <Value> (="127.0.0.1")         	تغییر هاست برای اتصال به سرور
 --port <Value> (=6000)                 تعییر پورت برای اتصال به سرور 

  --auto-quit-mode (=off)               خروج اتوماتیک پس از پایان بازی
  --kill-server (=off)                	بستن سرور بعد از بسته شدن برنامه   
 					
             			دستورات برای لاگ های بازی
                    
  --game-log [ -l ] <Value> (="") 		ادرس فایل لاگ سیو شده برای اجرا
  --game-log-dir <Value> (="")    		تغییر ادرس دیفالت مکان لاگ ها
 					
             			دستورات برای اندازه 
                    
  --maximize (=off)                		استارت در حالت ماکسیمم صفحه
  --full-screen (=off)             		استارت در حالت فول اسکرین
  --canvas-size <Value> (="")      		استارت با اندازه دلخواه (WxH)
                                   		--canvas-size=1024x768 برای مثال
  --hide-menu-bar (=off)          		استارت بدون نمایش نوار منو
  --hide-tool-bar (=off)        	 	استارت بدون نمایش نوار ابزار 
  --hide-status-bar (=off)         		استارت بدون نمایش نوار وضعیت
 					
             			دستورات برای نمایش
                    
  --anonymous-mode (=off)          نمایش ندادن نام تیم ها 
  --keepaway-mode (=off)           keepaway استارت در حالت 
  --show-score-board (=on)         نمایش امتیازات 
  --hide-score-board (=off)        پنهان کردن امتیازات
  --show-team-graphic (=on)        نمایش لوگو تیم ها
  --hide-team-grahip (=off)        پنهان کردن لوگو تیم ها
  --reverse-side (=off)            جا به جا کردن تیم های چپ و راست
  --show-player-number (=on)       نمایش شماره بازیکنان
  --hide-player-number (=off)      پنهان کردن شماره بازیکنان
  --show-view-area (=on)           نمایش دید بازیکنان 
  --hide-view-area (=off)          پنهان کردن دید بازیکنان
  --show-pointto (=on)             نمایش اشاره کردن بازیکنان 
  --hide-pointto (=off)            پنهان کردن اشاره کردن بازیکنان 
  --show-attentionto (=off)        نمایش جهت گوش دادن بازیکنان 
  --hide-attentionto (=on)         پنهان کردن جهت گوش دادن بازیکنان 
  --show-stamina (=on)             نمایش انرژی بازیکنان
  --hide-stamina (=off)            پنهان کردن انرژی بازیکنان 
  --show-stamina-capacity (=off)   نمایش ماکسمیم انرژی بازیکنان
  --hide-stamina-capacity (=on)    پنهان کردن ماکسمیم انرژی بازیکنان 
  --show-card (=on)                نمایش کارت های بازیکنان 
  --hide-card (=off)               پنهان کردن کارت های بازیکنان 

							دستورات حالت دیباگ

  --debug-server-mode [ -d ] (=on)    استارت در حالت دیباگ 
  --debug-server-port <Value> (=6032) تغییر پورت برای سرور دیباگ

  --show-debug-view (=on)            	نمایش اطلاعات دیباگ 
  --hide-debug-view (=off)           	پنهان کردن اطلاعات دیباگ 
  --show-debug-view-ball (=on)       	نمایش اطلاعات دیباگ توپ 
  --hide-debug-view-ball (=off)      	پنهان کردن اطلاعات دیباگ توپ 
  --show-debug-view-self (=on)       	نمایش اطلاعات دیباگ خود بازیکن  
  --hide-debug-view-self (=off)      	پنهان کردن اطلاعات دیباگ خود بازیکن 
  --show-debug-view-teammates (=on)  	نمایش اطلاعات دیباگ هم تیمی ها 
  --hide-debug-view-teammates (=off) 	پنهان کردن اطلاعات دیباگ هم تیمی ها 
  --show-debug-view-opponents (=on)  	نمایش اطلاعات دیباگ دید حریف 
  --hide-debug-view-opponents (=off) 	پنهان کردن اطلاعات دیباگ دید حریف 
  --show-debug-view-shape (=on)     	نمایش اطلاعات دیباگ شکل ها 
  --hide-debug-view-shape (=off)   	 	پنهان کردن اطلاعات دیباگ شکل ها 
  --show-debug-view-target (=on)    	نمایش اطلاعات دیباگ تارگت 
  --hide-debug-view-target (=off)   	پنهان کردن اطلاعات دیباگ تارگت 
  --show-debug-view-message (=on)    	نمایش اطلاعات دیباگ پیام ها 
  --hide-debug-view-message (=off)   	پنهان کردن اطلاعات دیباگ پیام ها 
  --show-debug-log-objects (=on)     	نمایش اطلاعات دیباگ توپ 
  --hide-debug-log-objects (=off)		پنهان کردن اطلاعات دیباگ توپ    
  
 
```



