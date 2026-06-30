# 🚀 CyberPanel v2.4.8 — نسخهٔ اصلاح‌شده (cyberpanelmaster-1.2)

> **یک پنل میزبانی وب قدرتمند، رایگان و متن‌باز با LiteSpeed، بهینه‌سازی شده برای Ubuntu 22.04 و MariaDB.**

![GitHub repo size](https://img.shields.io/github/repo-size/omidbezendegibabol-cmyk/cyberpanel-1.2?style=flat-square)
![GitHub last commit](https://img.shields.io/github/last-commit/omidbezendegibabol-cmyk/cyberpanel-1.2?style=flat-square)
![License](https://img.shields.io/badge/license-GPLv3-blue?style=flat-square)

---

## 📖 دربارهٔ این نسخه

این مخزن حاوی **سورس کامل و اصلاح‌شدهٔ CyberPanel نسخه 2.4.8** است که طی یک فرآیند طولانی نصب، عیب‌یابی و بهینه‌سازی روی **Ubuntu 22.04** و **MariaDB 10.11** تست و تثبیت شده است.

بسیاری از مشکلات رایج هنگام نصب (مانند خطاهای git clone، ناسازگاری Migrationها با MariaDB، و خطاهای مربوط به InnoDB) در این نسخه برطرف شده‌اند.

---

## ✨ تغییرات و بهبودها (Changelog)

### 🐛 باگ‌های رفع‌شده
- 🔧 رفع مشکل `login_page` → `loadLoginPage` در `loginSystem/views.py`
- 🗄️ اصلاح `max_length=255` به `250` در Migrationها برای سازگاری با MariaDB
- 🌐 رفع مشکلات متداول `git clone` در محیط‌های با اینترنت محدود یا ناپایدار (ایران)
- 💾 رفع خطاهای InnoDB و `aria_log_control` با راه‌اندازی موقت MyISAM
- 🔑 تنظیم رمز عبور صحیح دیتابیس در `settings.py`

### 🛠️ بهینه‌سازی‌ها
- ⚡ بهینه‌سازی DNS, MTU و TCP برای اینترنت پایدارتر روی VirtualBox
- 🗜️ کاهش حجم Migrationها با اصلاح `max_length`
- 📦 آماده‌سازی سورس برای نصب بدون نیاز به دانلود مجدد از گیت‌هاب رسمی
- 🧹 پاک‌سازی فایل‌های موقت و کش‌های غیرضروری

---

## 📋 پیش‌نیازها (Requirements)

| نرم‌افزار | نسخه |
|-----------|------|
| 🐧 Ubuntu | 22.04 LTS |
| 🗄️ MariaDB | 10.11.x |
| 🐍 Python | 3.10.x |
| 🌐 LiteSpeed | OpenLiteSpeed / Enterprise |
| 🔧 Git | 2.34+ |

---

## 📥 راهنمای نصب (How to Install)

### ⚠️ توجه: فایل اصلی به دلیل حجم بالا (~800MB) به ۱۸ پارت تقسیم شده است.

### 🐧 روی لینوکس (Ubuntu)

```bash
# ۱. کلون کردن مخزن
git clone https://github.com/omidbezendegibabol-cmyk/cyberpanel-1.2.git
cd cyberpanel-1.2

# ۲. یکپارچه‌سازی پارت‌ها و ساخت فایل اصلی
cat part_* > cyberpanel_fixed_v2.4.8.tar.gz

# ۳. استخراج و نصب
tar -xzf cyberpanel_fixed_v2.4.8.tar.gz
cd cyberpanel_source
sudo bash cyberpanel.sh
🪟 روی ویندوز (Command Prompt)
cmd
copy /b part_* cyberpanel_fixed_v2.4.8.tar.gz
سپس فایل را به محیط لینوکس منتقل کرده و مراحل بالا را ادامه دهید.

🔧 نکات فنی مهم
🗄️ اگر MariaDB خطای InnoDB داد
bash
sudo sed -i 's/^innodb/#innodb/' /etc/mysql/mariadb.conf.d/50-server.cnf
echo -e "[mysqld]\ndefault-storage-engine=MyISAM" | sudo tee /etc/mysql/conf.d/temp-myisam.cnf
sudo systemctl restart mariadb
🔑 اگر کاربر admin را گم کردی
bash
cd /usr/local/lscp
sudo /usr/local/CyberCP/bin/python manage.py shell -c "
from loginSystem.models import Administrator
admin, created = Administrator.objects.get_or_create(adminName='admin', defaults={'adminPassword':'123456','adminEmail':'admin@localhost','adminType':1})
if not created: admin.adminPassword='123456'; admin.save()
print('Admin password reset to 123456')
"
🚪 پورت پیش‌فرض
پنل روی پورت 8090 (یا 8091 در صورت اشغال بودن) قابل دسترسی است:

text
http://localhost:8090
📂 ساختار فایل‌ها در این مخزن
text
cyberpanel-1.2/
├── part_aa          # پارت ۱ از ۱۸
├── part_ab          # پارت ۲ از ۱۸
├── ...
├── part_ar          # پارت ۱۸ از ۱۸
└── README.md        # همین فایل
🤝 مشارکت (Contributing)
پیشنهادات، گزارش باگ و Pull Requestهای شما باعث افتخار است.
لطفاً پیش از ارسال تغییرات عمده، یک Issue باز کنید تا در مورد آن گفتگو کنیم.

👨‍💻 توسعه‌دهنده
Omid Bezendegi
📧 omidbezendegibabol@gmail.com
🔗 GitHub Profile

📜 مجوز (License)
این پروژه تحت مجوز GPL v3 مطابق با CyberPanel اصلی منتشر می‌شود.

با افتخار در ایران توسط شرکت هوش دیجیتال ساخته توسط پارسا فانی اصفهانی ساخته و بهینه‌سازی شده است. 🇮🇷
