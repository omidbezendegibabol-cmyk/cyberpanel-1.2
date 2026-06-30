# cyberpanel-1.2
CyberPanel v2.4.8 fixed for Ubuntu 22.04 &amp; MariaDB. Fixed login_page, max_length migration issue &amp; git clone problems. Ready to install with one command. Developer: Omid Bezendegi

---------------------------------------

# CyberPanel v2.4.8 - نسخه اصلاح‌شده

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
