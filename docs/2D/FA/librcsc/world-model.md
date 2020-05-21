# World Model
بازیکن با استفاده از سنسورهای خود اطلاعات محیط بازی را از سرور دریافت می‌کند، بعد از تحلیل‌ و بررسی این اطلاعات و انجام محاسبات ریاضی بر روی آنها،‌ در نهایت اطلاعات مهم را داخل این کلاس ذخیره میکند. بعضی از سنسورها در زیر نوشته شده‌اند.

 - Eye
 - Ear
 - BodySense
 - و غیره ...

## Layers and Ball
در world model میتونیم به مکان ها و سرعت های هر بازیکن و حتی توپ هم دسترسی پیدا کنیم. در قطعه کد زیر مثالی برای دسترسی به اطلاعات بازیکن‌ها را میبینید.

```c
const WorldModel &wm = agent->world(); // define a variable as refrence for shortcut

// teammates
const AbstractPlayerObject* player = wm.ourPlayer(n) // n is in range of 1 to 11 (uniform number)
//opponents
const AbstractPlayerObject* player = wm.theirPlayer(n);

// find player's position and speed as a Vector (x and y)
Vector2D player_pos = player->pos();
Vector2D player_vel = player->vel();

//finding ball speed and pos as Vector
Vector2D ball_pos = wm.ball().pos();
Vector2D ball_vel = wm.ball().vel();
```

باید توجه داشت که اگه بازی full state نباشید ممکن هست بازیکنان NULL باشند و این  باگ دادن و KILL شدن بازیکن میشود.
برای جلوگیری از این قضیه به کد زیر توجه کنید.
```c
const WorldModel &wm = agent->world();

for(int i = 1; i <= 11; i++){
	const AbstractPlayerObject *tm = wm.ourPlayer(i);
	if (tm == NULL || tm->unum < 0)
		continue;
	
	//else do process;
}
```

## InterceptTable
در این کلاس یکی از مهم‌ترین اعضای آن InterceptTable هست که داخل آن محاسباتی در اول هر سایکل انجام میگیرد برای پیدا کردن نزدیک‌ترین بازیکنان به توپ. منظور از نزدیک‌ترین بازیکنان فاصله مکانی نیست بلکه زمانی است. که برای نوشتن الگوریتم‌های دفاعی بسیار کمک کننده هستند.
در زیر مثالی از کاربرد آن نوشته شده است.

```c
const WorldModel &wm = agent->world();

// find minimum cycles for self to reach the ball
const int self_min = wm.interceptTable()->selfReachCycle();
// find minimum cycles for teammates to reach the ball
const int mate_min = wm.interceptTable()->teammateReachCycle();
// find minimum cycles for opponents to reach the ball
const int opp_min = wm.interceptTable()->opponentReachCycle();
```

## GameTime
در این کلاس می‌توانیم زمان بازی را نیز بدست بیاوریم. به مثال زیر دقت کنید.
```c
int cycle = wm.time().cycle();
```