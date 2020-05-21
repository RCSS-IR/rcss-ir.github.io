### ساخت باینری در بیس Agent2D

ابتدا فرض می کنیم پوشه تیم شما در آدرس زیر می باشد:

```bash
/home/user/workspace/yourteam/
```

جهت از بین نرفتن اطلاعات ابتدا پوشه src را در مکان دیگری کپی می نماییم.

```bash
cp /home/user/workspace/yourteam/src /home/user/workspace/binary -r
```

با استفاده از دستور زیر یک پوشه با نام lib در پوشه binary می سازیم.

```bash
cd /home/user/workspace/binary
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
cp /usr/local/StarterLibRCSC/librcsc* /home/user/workspace/binary/lib
```

برای بیس Agent2D:

```bash
cp /usr/local/lib/librcsc* /home/user/workspace/binary/lib
```

سپس فایل start.sh خود را باز نموده و متغیر LIBPATH در خط 12 را به صورت زیر تغییر دهید:

```bash
LIBPATH = './lib/'
```

در نهایت در پوشه باینری تمامی فایل های cpp. و h. را پاک نمایید.

تقریبا باینری شما آماده می باشد.