# ابزار‌های هندسی در کتابخانه librcsc

## Vector2D

در این قسمت میخواهیم کلاس برداری دو بعدی Vector2D رو معرفی کنیم.

این کلاس شامل دو عضو x و y هست و توابع بسیاری که ریاضیات را برای ما آسون میکند. مانند:

- dist and dist2
- r and r2
- polar2vector
- th
- etc...

توابع dist فاصله از یک نقطه دیگر و توابع r اندازه خود بردار را میدهند. تابع th زاویه‌ی بردار نسبت به افق را میدهد.

به مثال زیر توجه کنید.

```c
Vector2D a(2,3);
Vector2D b(4,5);

double d = a.dist(b); // distance
double d2 = a.dist2(b); // distance * distance

double r = a.r(); // radius
AngleDeg t = a.th(); // angle
```



## polar2vector

این تابع استاتیک هست و تبدیلات مختصات قطبی را برای ما انجام میدهد. دو ورودی زاویه و شعاع میگیرد و بردار را به ما برمیگرداند. مثال:

```c
double r = 10;
double teta = 60;

Vector2D pos = Vector2D::polar2Vector(r, teta);
```

