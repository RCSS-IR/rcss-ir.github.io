# Namira Log-Analyzer

<div id="46388315721"><script type="text/JavaScript" src="https://www.aparat.com/embed/yVOkK?data[rnddiv]=46388315721&data[responsive]=yes"></script></div>

> تیم نامیرا - آموزش ابزار Log-Analyzer

[Namira Log-Analyzer](https://github.com/Farzin-Negahbani/Namira_LogAnalyzer) ابزاری پایتونی‌ برای تجزیه و تحلیل بازی‌های شبیه‌سازی دوبعدی فوتبال است که توسط تیم نامیرا ساخته شده است.

استفاده از این ابزار و بسته به نیاز شما این اسکریپت میتواند برای کارهای مختلفی استفاده شود. از جمله‌:

- تولید اطلاعات جامع در مورد عملکرد تیم شما در مسابقات مختلف.

- ارزیابی قابلیت‌های مختلف تیم شما از جمله شمردن تعداد پاس و درصد مالکیت و ...

- استخراج داده برای آموزش الگوریتم‌های مختلف یادگیری ماشین

- و ..

  

## شروع به استفاده 

برای استفاده از این ابزار شما باید اول پیش‌نیاز‌های آن به وسیله دستور زیر نصب کنید.

```bash
sudo apt update && sudo apt install python3 python3-pip python3-setuptools python3-numpy python3-matplotlib
```

حال با استفاده از دستور زیر پروژه را در سیستم خود ذخیره کنید و وارد فولدر پروژه شوید.

``` bash
git clone https://github.com/Farzin-Negahbani/Namira_LogAnalyzer.git && cd Namira_LogAnalyzer
```

شما به دو روش میتواند این ابزار را در سیستم خود نصب کنید.

- روش اول


```bash 
sudo python3 ./setup.py install
```

- روش دوم

```bash
pip install .
```


برای **حذف** این برنامه از سیستمتان میتوانید از دستور زیر استفاده کنید.

```bash 
pip uninstall loganalyzer
```

## شیوه‌ی استفاده

<note type="tip" label="">برای بررسی نحوه بازیابی اطلاعات، به فایل `Testcase.py` رجوع کنید.</note>

شما میتوانید از این ابزار به دو شیوه استفاده کنید:

- **استفاده به عنوان یک دستور**

   با دادن فایل rcl یا rcg به عنوان ورودی به دستور `**loganalyzer**`، میتوانید از قابلیت‌های این ابزار استفاده کنید. به طور مثال:


``` bash
loganalyzer --path <log file without .rcl or .rcg >
```

-  **استفاده به عنوان یک ماژول‌ در پایتون**

``` python
import loganalyzer
from loganalyzer import Parser
from loganalyzer import Game
from loganalyzer import Analyzer
parser = Parser('path to log file without .rcl or .rcg')
game = Game(parser)
analyzer = Analyzer(game)
analyzer.analyze()
left_team_pass = analyzer.pass_l
left_team_in_target_shoot = analyzer.in_target_shoot_l
left_team_agent_1 = game.left_team.agents[0].data
```

## قابلیت‌ها

این ابزار با تحلیل فایل ورودی، به شما اطلاعات مفیدی را از متغیر‌های زیر میدهد. 

- پاس
  - شمارش پاس
    - پاس های طولی
    - پاس های عرضی
    - در ۹ منطقه زمین (A,B,...I)
    - پاس های صحیح
  - دقت پاس
  - پاس های قطع شده

- شوت
  - دقت شوت
  - شمارش شوت
    - شوت های طولی
    - شوت های عرضی
    - در ۹ منطقه زمین (A,B,...I)
    - شوت های در چارچوب
    - شوت های خارج از چارچوب

- مالکیت
  - مالکیت هر تیم در ۹ منطقه زمین (A,B,...I)
  - مالکیت هر بازیکن در ۹ منطقه زمین (A,B,...I)
  - مالکیت هر تیم یا هر بازیکن در هر منطقه دلخواه

- موقعیت 
  - سیکل هایی که هر بازیکن در ۹ منطقه زمین (A,B,...I) قرار داشته
    - سیکل هایی که هر بازیکن در هر منطقه دلخواه قرار داشته

- مسافت طی شده برای هر بازیکن
- نیروی استفاده شده برای هر بازیکن
- نیروی استفاده شده، نسبت به مسافت طی شده برای هر بازیکن
- Heatmap بازی برای هر تیم
- شمارش ضربه‌ها
- شمارش تکل‌ها
- شمارش say‌ها

<note type="success" label="شیوه‌ی ناحیه‌بندی زمین در ابزار">

<ImageZoom 
  src="/docs/2D/FA/img/doc/tools/default_regions.jpeg" 
  :border="false" 
  width="full"
/>

</note>

## ارجاع‌دهی

در صورتی که این ابزار را مفید ارزیابی می‌کنید، لطفا در صورت استفاده از این ابزار در پروژه خود، در قسمت ارجاعات (References) مقاله‌ی خود به مقالات زیر ارجاع دهید.

```
Namira Soccer 2D Simulation Team Description Paper 2018. [PDF](https://archive.robocup.info/Soccer/Simulation/2D/TDPs/RoboCup/2018/Namira_SS2D_RC2018_TDP.pdf)

Persian Gulf Soccer 2D Simulation Team Description Paper 2017. In The 21th annual RoboCup International Symposium, Japan, Nagoya. [PDF](https://www.robocup2017.org/file/symposium/soccer_sim_2D/TDP_PersianGulf.pdf)
```

## ارتباط با سازنده

برای سوال و پیشنهاد میتوانید با آدرس‌های زیر با سازندگان این ابزار ارتباط برقرار کنید. همچنین در صورت مشاهده‌ی اشکال در ابزار، آن را در قسمت Issueهای گیتهاب پروژه مطرح کنید تا در اولین فرصت برطرف شود. 

<AvatarMini 
            img="/docs/2D/FA/img/people/unknown-avatar.png" 
            firstName="فرزین"
            lastName="نگهبانی"
            email="farzin.negahbani@gmail.com">
</AvatarMini>
<AvatarMini 
            img="/docs/2D/FA/img/people/unknown-avatar.png" 
            firstName="شهریار"
            lastName="بهمنی"
            email="shahryarbahmeie@gmail.com">
</AvatarMini>
<AvatarMini 
            img="/docs/2D/FA/img/people/unknown-avatar.png" 
            firstName="احسان"
            lastName="عسلی"
            email="ehsanasali@uga.edu">
</AvatarMini>
