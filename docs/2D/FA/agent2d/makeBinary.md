# ساخت باینری در بیس Agent2D

<iframe width="560" height="315" src="https://www.youtube.com/embed/eQwX2p5CNFI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>


> تیم سایرس (Cyrus) - آموزش ساخت باینری استاتیک [YT](https://youtu.be/eQwX2p5CNFI) 



<iframe width="560" height="315" src="https://www.youtube.com/embed/nLqYelU4sok" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>


> تیم امپراطور (EMPEROR) - آموزش اضافه کردن پرچم به تیم [YT](https://youtu.be/nLqYelU4sok)




## باینری چیست؟
باینری به فایل اجرایی بازیکن‌های تیم شما گفته می‌شود که با اجرای آن کد مربوط به تیم شما اجرا می‌شود.

در مسابقات اصطلاح `باینری استاتیک` به مجموعه فایل‌های اجرایی بازیکن‌های تیم شما گفته می‌شود معمولا این فایل ها در یک پوشه و به صورت فایل آرشیو شده (معمولا `.tar.gz`) می‌باشد.


<note type="warning" label="">

توجه کنید که تمام فایل‌هایی که برای اجرای تیم شما لازم است باید در یک پوشه قرار داشته باشند.
این پوشه در هر مسابقه باید از استاندارد‌های مربوط به آن مسابقه پیروی کند.

</note>



در این آموزش شما با شیوه‌ی ساختن فایل باینری آشنا می‌شوید.


ابتدا فرض می کنیم پوشه تیم شما در آدرس زیر می باشد:

```bash
/home/user/workspace/yourteam/
```

جهت از بین نرفتن اطلاعات ابتدا پوشه src را در مکان دیگری کپی می نماییم.

```bash
cp -r /home/user/workspace/yourteam/ ~/team_binary 
```

با استفاده از دستور زیر یک پوشه با نام lib در پوشه binary می سازیم.

```bash
cd ~/team_binary
mkdir lib
```

به صورت معمول کتابخانه بیس Agent در مسیر زیر نصب می شود:

```bash
/usr/local/lib/
```

و کتابخانه بیس Starter Agent در مسیر زیر نصب می شود:

```bash
/usr/local/StarterLibRCSC
```

سپس اطلاعات موجود در پوشه بالا را به پوشه lib در باینری تیم منتقل می نماییم:

برای بیس StarterAgent2D یا دانش آموزی:

```bash
cp /usr/local/StarterLibRCSC/librcsc* ~/team_binary/lib
```

برای بیس Agent2D:

```bash
cp /usr/local/lib/librcsc* ~/team_binary/lib
```

سپس فایل start.sh خود را باز نموده و متغیر LIBPATH در خط 12 را به صورت زیر تغییر دهید:

```bash
LIBPATH = './lib/'
```

پروژه را دوباره بیلد کرده تا فایل‌های باینری ساخته شوند.
    
```bash
cd ~/team_binary
make
```


در نهایت در پوشه باینری تمامی فایل‌های cpp. و h. و فایل‌های .o را پاک نمایید.
```bash
rm **/*.cpp **/*.h **/*.o **/*.rcg **/*.rcl
```


در نهایت فایل آرشیو شده با فرمت `.tar.gz` را از پوشه binary تهیه می کنیم.
توجه کنید که نام TEAMNAME.tar.gz را با نام تیم خود جایگزین کنید.
```bash
tar -czvf TEAMNAME.tar.gz ~/team_binary
```


بر اساس نوع مسابقه ممکن است استاندارد‌های دیگری هم برای باینری تعریف شده باشد که باید در نظر گرفته شود.
استاندارد کلی برای مسابقات به این صورت است که فایل باینری شما باید در کنار فایلی برای `start` یا `kill` قرار بگیرد.


در ادامه استاندارد برخی مسابقات آورده شده است.


## استاندارد مسابقات ایران اوپن ۲۰۲۳

اطلاعات زیر از [این لینک](https://docs.google.com/document/d/1Q2ek8j1lOcXRRSh50fwXBpddYuAil761vfH8k441YQw/edit?usp=sharing) گردآوری شده است. 

1. برای مسابقات ایران اوپن ۲۰۲۳ باینری تیم شما باید در یک فایل آرشیو شده با فرمت `.tar.gz` باشد.
2. فایل باینری تیم شما باید با نام تیم شما باشد.
3. فایل `start` مطابق زیر باید در پوشه اصلی فایل آرشیو شده باشد.


برای تیم‌های دانش‌آموزی:

```bash
#!/bin/sh

HOST=$1
BASEDIR=$2
NUM=$3

LIBPATH=./lib
if [ x"$LIBPATH" != x ]; then
if [ x"$LD_LIBRARY_PATH" = x ]; then
    LD_LIBRARY_PATH=$LIBPATH
else
    LD_LIBRARY_PATH=$LIBPATH:$LD_LIBRARY_PATH
fi
export LD_LIBRARY_PATH
fi


teamname="TEAMNAME"

player="./sample_player"
coach="./sample_coach"

config="./player.conf"
coach_config="./coach.conf"

opt="--player-config ${config}"
opt="${opt} -h ${HOST} -t ${teamname}"

coachopt="--coach-config ${coach_config} --use_team_graphic on"
coachopt="${coachopt} -h ${HOST} -t ${teamname}"

cd $BASEDIR

case $NUM in
    1)
        $player $opt -g
        ;;
    12)
        $coach $coachopt
        ;;
    *)
        $player $opt
        ;;
esac
```


برای تیم‌های دانشجویی‌ای که بر اساس بیس Agent ساخته‌شده‌اند:

```bash
#!/bin/sh

HOST=$1
BASEDIR=$2
NUM=$3

LIBPATH=./lib
if [ x"$LIBPATH" != x ]; then
if [ x"$LD_LIBRARY_PATH" = x ]; then
    LD_LIBRARY_PATH=$LIBPATH
else
    LD_LIBRARY_PATH=$LIBPATH:$LD_LIBRARY_PATH
fi
export LD_LIBRARY_PATH
fi


teamname="Teamname"

player="./sample_player"
coach="./sample_coach"

config="./player.conf"
coach_config="./coach.conf"
config_dir="./formations-dt"
opt="--player-config ${config}  --config_dir ${config_dir}"
opt="${opt} -h ${HOST} -t ${teamname}"

coachopt="--coach-config ${coach_config} --use_team_graphic on"
coachopt="${coachopt} -h ${HOST} -t ${teamname}"

cd $BASEDIR

case $NUM in
    1)
        $player $opt -g
        ;;
    12)
        $coach $coachopt
        ;;
    *)
        $player $opt
        ;;
esac

```
    
    
4. در فایل `start` متغیر `teamname` را با نام تیم خود جایگزین کنید.
5. میتوانید فایلی با نام `localStartAll` به تیم خود اضافه کرده و با آن تیم خود را تست کنید


```bash
#!/bin/sh
./start 127.0.0.1 . 1 &
sleep 2
./start 127.0.0.1 . 2  &
sleep 0.3
./start 127.0.0.1 . 3  &
sleep 0.3
./start 127.0.0.1 . 4  &
sleep 0.3
./start 127.0.0.1 . 5  &
sleep 0.3
./start 127.0.0.1 . 6  &
sleep 0.3
./start 127.0.0.1 . 7  &
sleep 0.3
./start 127.0.0.1 . 8  &
sleep 0.3
./start 127.0.0.1 . 9  &
sleep 0.3
./start 127.0.0.1 . 10 &
sleep 0.3
./start 127.0.0.1 . 11 &
sleep 0.3
./start 127.0.0.1 . 12 &
```
    
    
6. باینری تیم شما باید زیر ۲۰۰ مگ باشد و نباید هیچ فایلی جز فایل‌های ضروری برای اجرا داخل آن قرار گیرد. (فایل لاگ به طور مثال نباید در فولدر باینری باشد)


