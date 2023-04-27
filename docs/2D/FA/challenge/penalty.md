# چالش پنالتی

![](/docs/2D/FA/challenge/img/penalty.png)

## معرفی
چالش پنالتی در ایران‌اوپن ۲۰۲۳ به عنوان چالش فنی برای تیم‌های دانش‌آموزی استفاده می‌شود.

در این چالش دو تیم در رقابت پنالتی‌ها (بدون هیچگونه تغییری در قوانین پنالتی) در مقابل هم قرار میگیرند.

در هر نوبت توپ دست بازیکن تیمی قرار گرفته و دروازه‌بان تیم مقابل وظیفه‌ی دفاع از دروازه را دارد.


## نحوه‌ی اجرای سرور
برای اجرای سرور از دستور زیر استفاده کنید:

```bash
rcssserver server::nr_normal_halfs=0 server::nr_extra_halfs=0 server::pen_max_goalie_dist_x=10 server::penalty_shoot_outs=true
```

یا این که این کانفیگ ها را در فایل `server.conf` پیدا کنید و مقادیر را تغییر دهید.
این فایل را میتوانید در فولدر `~/.rcssserver` پیدا کنید.

```bash
server::nr_normal_halfs=0 
server::nr_extra_halfs=0 
server::pen_max_goalie_dist_x=10 
server::penalty_shoot_outs=true
```

