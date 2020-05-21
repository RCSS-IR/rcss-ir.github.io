# کلاس BallObject

اطلاعات توپ مانند مکان و سرعت و ... در کلاس BallObject ذخیره میشوند.

این کلاس دارای توابعی کاربردیست که در زیر مثال‌هایی از آنها را میبینید.



## inertiaPoint

این تابع مکان توپ در چند سایکل بعدی را به عنوان خروجی از نوع Vector2D برمیگرداند.

```c
const WorldModel &wm = agent->world();
int n_cycles = 10;

Vector2D predict_ballpos = wm.ball().inetiaPoint(n);
```



## inertiaFinalPoint

این تابع مکان نهایی توپ با استفاده سرعتی که دارد را محاسبه میکند. یعنی مکانی که توپ در آنجا می‌ایستد.

```c
const WorldModel &wm = agent->world();

Vector2D predict_ballpos = wm.ball().inertiaFinalPoint();
```

