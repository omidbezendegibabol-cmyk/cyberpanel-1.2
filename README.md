# cyberpanel-1.2
CyberPanel v2.4.8 fixed for Ubuntu 22.04 &amp; MariaDB. Fixed login_page, max_length migration issue &amp; git clone problems. Ready to install with one command. Developer: Omid Bezendegi

---------------------------------------

# CyberPanel v2.4.8 - (cyberpanelmaster-1.2) نسخه اصلاح‌شده

این مخزن حاوی سورس **CyberPanel نسخه 2.4.8** است که برای نصب روی **Ubuntu 22.04** و **MariaDB** بهینه‌سازی و رفع اشکال شده است.

## تغییرات انجام‌شده (Changelog)
- رفع مشکل `login_page` و جایگزینی با `loadLoginPage` در `loginSystem/views.py`
- اصلاح `max_length=255` به `250` در Migrationها برای سازگاری با MariaDB
- رفع مشکلات متداول `git clone` در محیط‌های با اینترنت محدود
- آماده‌سازی برای نصب بدون نیاز به دانلود مجدد سورس

## پیش‌نیازها (Requirements)
- Ubuntu 22.04
- MariaDB 10.11
- Python 3.10
- LiteSpeed Web Server (OpenLiteSpeed)

## راهنمای نصب (How to Install)
1. فایل فشرده را دانلود کنید.
2. با دستور زیر استخراج کنید:
   ```bash
   tar -xzf cyberpanel_fixed_v2.4.8.tar.gz
------------------------------------------------------------------------------------------------------------------------------------------

بخاطر حجم بالای فایل حدود 800 مگ به 18 پارت تقسیم گردید*
طریقه یکپارچه کردن پارت ها 📥
روش بازسازی و نصب (برای خودت یا دیگران)
روی لینوکس (اوبونتو):
bash
# ۱. دانلود همهٔ پارت‌ها (اگر از گیت‌هاب clone کردی)
git clone https://github.com/omidbezendegibabol-cmyk/cyberpanel-1.2.git
cd cyberpanel-1.2

# ۲. چسبوندن پارت‌ها به هم و ساخت فایل اصلی
cat part_* > cyberpanel_fixed_v2.4.8.tar.gz

# ۳. استخراج و نصب
tar -xzf cyberpanel_fixed_v2.4.8.tar.gz
cd cyberpanel_source
sudo bash cyberpanel.sh
روی ویندوز (Command Prompt):
cmd
copy /b part_* cyberpanel_fixed_v2.4.8.tar.gz
سپس فایل را به لینوکس منتقل کن و ادامه بده.
