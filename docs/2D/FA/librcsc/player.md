# کلاس Player

## PlayerType

موقع اجرای هر بازی، سرور به صورت رندم ۱۸ تا بازیکن با مشخصات مختلف به وجود میاورد ولی به صورت یکسان برای هر دو تیم. یکی از دلایلی که دو بازی از دو کد یکسان هیچ وقت مثل هم نیست تفاوت مشخصات بازیکنان هست.



هر بازیکن در سرعت دویدن، سرعت شوت زدن، نحوه مصرف انرژی، اندازه بازیکن، حداکثر فاصله برای ضربه زدن به توپ و .... متفاوت است. این تفاوت‌ها به صورت اطلاعاتی پایه‌ای از سمت سرور به بیس فرستاده میشود و بیس با انجام محاسبات اطلاعات مهم مانند مثال‌های بالا را برای ما بدست می‌آورد.

نحوه دسترسی:

```c
const WorldModel &wm = agent->world();

const AbstractPlayerObject *tm = wm.ourPlayer(2);

if(tm->pos().dist(wm.ball().pos()) < tm->playerTypePtr()->kickable_area)
    // DO SOMETHING

```

این کد چک میکند که آیا توپ در دسترس بازیکن شماره‌ی دو هست یا نه.

یکی از توابع مهم playerTypePtr تابع cycleToReachDistance هست که با مشخصات آن بازیکن حساب میکند چقدر طول میکشد تا یک فاصله را طی کند. مثال:

```c
const WorldModel &wm = agent->world();

const AbstractPlayerObject *tm = wm.ourPlayer(2);
double dist = 10;

int cycles = tm->playerTypePtr().cycleToReachDistance(dist);
```



